---
name: Modern Cache Replacement via RL/DL Techniques.
tools: [Reinforcement Learning, Deep Learning]
image: https://www.iitg.ac.in/cseweb/marslab/images/slider/EmbeddedSystem_shutterstock.jpg
description: This project involves work to explore modern techniques using Reinforcement Learning or Deep Learning or 
            combination of both to appoach optimal possible strategy of cache replacement.
---

<h3 style="text-align: center;">My Research - Modern Cache Replacement Techniques</h3>

<br/>
- The traditional cache replacement techniques include some of well know standard techniques such as LRU(Least Recently Used), LFU(Least Frequently Used) etc.
- With the appearance of modern machine learning algorithms which can help us read patterns in more semantic way than these traditional heuristic algorithms, the
architecture world is set out on expedition to use these techniques to find an optimal implementation.
- As any of the implementation comes with it's limitations, till date we don't have any on-chip facility to load these compute expensive algorithms we can just use the simulators to simulate such ML based policy and obtains results.
- We(I and my team mate) went on and took this exploration path to understand cache replacement, some of tradidinal algoriths and their heuristics.
- I tried to understand the [Simulator](https://github.com/ChampSim/ChampSim) written in *C++* and implement a few traditional heuristic based policy to see metrics.
- Next I stepped in the world of modern cache replacement techniques by reading various papers. The most inspiring for my case was *Designing a cost-effective cache replace- 
ment policy using machine learning* which was from *2021 IEEE International Symposium on High-Performance Computer Architecture (HPCA)*. 
- Tried to implement this in [Open-Gym](https://github.com/google-research/google-research/tree/master/cache_replacement) simulator which is easy to be used with python and allows us to implement ML/RL algorithms.
- Finally concluded research with a heuristic based policy implemented via analysis features from above work done in python.

<p class="text-center"> {% include elements/button.html link="../static/BTP04_Report_8thSem_End.pdf" text="Full Report" style="primary" %} </p>