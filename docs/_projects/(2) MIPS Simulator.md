---
name: MIPS Assembly Instructions Simulator.
tools: [Python, Tkinter, MIPS, Multi-threading]
image: ../static/MIPS-Simulator-Thumbnail.png
description: Simulating the assembly instructions compiler and generating output - also involved optimising via instruction pipelining in MIPS arch.
---

This project was a part of course Computer Organisation, it was done in three phases:

- Parsing assembly code, executing instructions one by one to generate correct ouput.
- Optimising this simulator to distribute instructions in 5 phases as per MIPS arch. and execute in pipelined fashion while using latches to transfer data between pipeline.
- Implementing a two level cache with configurable cache size, associativity and block size.

To generate how the pipeline looked like and where did the stalls occur we generate excel file with visualisation something like this.
![404 sorry image couldn't load](https://user-images.githubusercontent.com/54976309/81482981-6d7e6a00-9258-11ea-86a5-8df9772d4ec5.png "Pipeline Visuals")

We(me and my team mate) also implemented an interface which is similar to QtSpim(simulator in market to run MIPS code). This was done with the help of Tkinter in python.
This is how our cache finally looks like in GUI once the programs finishes execution.

![404 sorry image couldn't load](https://user-images.githubusercontent.com/54976309/81482959-39a34480-9258-11ea-800e-01e188a44df9.png "Cache Structure")


As an optional adventure we went out to write **multi-threaded** program for simulating the pipeline model to execute instructions parallelly.

This was interesting as it produced correct output less frequently or sometimes halting with error. After studying about threads in Operating Systems course the folowing year it finally became clear as to why our program wasn't thread safe as we hadn't used mutex to protect data and also didn't sync the instructions well. I believe *it's an art to write concurrent multi-threaded programs with validity and determinism*.

Checkout the github repo to play around and try out fun simulator!

<p class="text-center"> {% include elements/button.html link="https://github.com/deep-maheshwari/MIPS-Simulator" text="Checkout Github Project" style="outline-dark" %} </p>
