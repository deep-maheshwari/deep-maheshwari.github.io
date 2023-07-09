---
title: How and When to Use Bloom Filters? A Real Production Scenario!
tags: [Algorithms, Data Structure]
style: fill
color: info
description: Bloom filters use case from my experience in real production scenario.
external_url: 
---

This blog is about how we could exploit bloom filters as an efficient data structure where we have huge amounts of data in production scenarios and we don't want to run into time complexity issues iterating over huge data to find something.

Bloom Filters are primarily hash based data structure which helps us with storing huge amounts of data efficiently in bitmap. Now the compression of storage costs us with some accuracy when we try to lookup some element inserted in this bloom filter. More information about this can be found in [Bloom Filter Wiki](https://en.wikipedia.org/wiki/Bloom_filter). 

I would be abstracting out the specifics of what my data was in explanation.

In my case the case was to de-duplicate elements from two huge sets of integers. Also the catch was that we didn't want to exceed memory so we used batching to fetch data from the filesystem and stream it in batch of 1000's. Now with this setup let's say set A has to be dedeuplicated if we find any element that it has is also present in set B. In simple terms if we find any element in both set A and set B, we need to remove that element from set A. 

The naive way to this would be following:

```python
def deduplicate():
    with open('dedup_A', 'w+') as dedup_A: # writing to file since we have memory constraints and can't store in RAM
        for batch_elements_A in A.read_batch():
            for element_A in batch_elements_A:
                found = False
                for batch_elements_B in B.read_batch():
                    found = element_A in batch_elements_B
                if found:
                    break
                dedup_A.write(element_A)
```

The above functions costs us significant time as if we see the complexity is O(n\*m) where n is size of set A and m is size of set B. In production secnario this was costing us about 2 hours for data even of order just 1 million elements in set A against 10 elements in set B. Now what's the solution to reduce this? ***Bloom Filter to the rescue!!!***

What we can do is just store the set with higher number of elements in bloom filter which satisfies our memory constraint with few 1000 bits for even millions of 64 bit elements. Now we perform lookup in this bloom filter. Now when answer is no we know that it's definitely not there, but if it's yes then for that element we would have to iterate over all the elements of opposite set. Assuming the positives to be less and data to be uniformly spread along with optimal error rate we can control the full iterations leading to amortized linear complexity.

Using the [pybloomfilter](https://github.com/prashnts/pybloomfiltermmap3) python library the code would look something like:

```python
def deduplicate():
    bloomfilterB = pybloomfilter.BloomFilter(len(set_B), 0.01) # 1st param is # elements to be put in filter, second is acceptable error rate 
    for batch_elements_B in B.read_batch():
        bloomfilterA.update(batch_elements_A)
    with open('dedup_A', 'w+') as dedup_A:
        for batch_elements_A in A.read_batch():
            for element_A in batch_elements_A:
                found = False
                probably_found = element_A in bloomfilterB
                if probably_found:   # This condition is met rarely some few constant times hence amortizing complexity to linear
                    for batch_elements_B in B.read_batch():
                        found = element_A in batch_elements_B
                if found:
                    break
                dedup_A.write(element_A)
```

This was just one example of Bloom Filters, there are lots of practical applications and lots of software frameworks use these. Hope you found this article useful!
