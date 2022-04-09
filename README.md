# Summary - A Philosophy of Software Design

## Why do we need a philosophy?

The speed of software development is one of the most important factors to consider when building software. It could even be said that it _is_ the most important factor, as the speed of development determines how fast you could ship features and be ahead of the competition. In the worst case, the speed of development could become so slow that the project isn't even viable anymore.

It's the nature of software to increase in complexity through time. A complex software requires a developer to be aware of multiple factors when changing the software, so as to not introduce bugs or break older functions while adding or modifying features. Changing a complex software takes time, and as the complexity increases, the time taken to further develop the software reliably, increases with it. Therefore it is important to make sure the rate of increase in complexity of a software is as low as possible.

To tackle this problem, we need to design software that is simple. The complexity would still accumulate inspite of our best efforts, but we can keep it from becoming overwhelming. This book aims to provide us with a philosophy, a guiding principle, that can help us in designing simple software.

> **Complexity is anything related to the structure of a software system that makes it hard to understand and modify the system.**

## Symptoms of Complexity

1. **Change amplification**: The first symptom of complexity is that a seemingly simple change requires code modifications in many different places. One of the goals of good design is to reduce the
amount of code that is affected by each design decision, so design changes don’t require very many code modifications.
2. **Cognitive load**: The second symptom of complexity is cognitive load, which refers to how much a developer needs to know in order to complete a task. A higher cognitive load means that developers have to spend more time learning the required  information, and there is a greater risk of bugs because they have missed something important.
3. **Unknown unknowns**: The third symptom of complexity is that it is not obvious which pieces of code must be modified to complete a task, or what information a developer must have to carry out the task successfully. An unknown unknown means that there is something you need to know, but there is no way for you to find out what it is, or even whether there is an issue.

## Causes Of Complexity
1. **Dependencies**:  a dependency exists when a given piece of code cannot be understood and modified in isolation; the code relates in some way to other code, and the other code must be considered and/or modified if the given code is changed. 

    Dependencies are a fundamental part of software and can’t be completely eliminated. In fact, we intentionally introduce dependencies as part of the software design process. Every time you write a new class you create dependencies around the API for that class. However, one of the goals of software design is to reduce the number of dependencies and to make the dependencies that remain as simple and obvious as possible.

2. **Obscurity**: Obscurity occurs when important information is not obvious. A simple example is a variable name that is so generic that it doesn’t carry much useful information (e.g., time).

    Obscurity is often associated with dependencies, where it is not obvious that a dependency exists. For example, if a new error status is added to a system, it may be necessary to add an entry to a table holding string messages for each status, but the existence of the message table might not be obvious to a programmer looking at the status declaration. Inconsistency is also a major contributor to obscurity: if the same variable name is used for two different purposes, it won’t be obvious to developer which of these purposes a particular variable serves.

    In many cases, obscurity comes about because of inadequate documentation. However, obscurity is also a design issue. If a system has a clean and obvious design, then it will need less documentation. The need for extensive documentation is often a red flag that the design isn’t quite right. The best way to reduce obscurity is by simplifying the system design.

## Working Code Isn't Enough

### Tactical Programming

Tactical Programming refers to the approach of programming where you're just writing code to get something working. The goal is to just make a feature or a bug fix work. It is very fast, but in the pursuit of speed it sacrifices producing a good system design.

It seems reasonable to add a bit of complexity if it allows the current task to be completed more quickly. But as is the nature of software, the accumulation of complexity is incremental. It’s not one particular thing that makes a system complicated, but the accumulation of dozens or hundreds of small things. And the complexity is going to increase rapidly if everyone is programming tactically.

### Strategic programming

The first step towards becoming a good software designer is to realize that working code isn’t enough. It’s not acceptable to introduce unnecessary complexities in order to finish your current task faster. The most important thing is the long-term structure of the system. Most of the code in any system is written by extending the existing code base, so your most important job as a developer is to facilitate those future extensions. Thus, you should not think of “working code” as your primary goal, though of course your code must work. Your primary goal must be to produce a great design, which also happens to work. This is strategic programming.

Strategic programming requires an investment mindset. Rather than taking the fastest path to finish your current project, you must  invest time to improve the design of the system. These investments will slow you down a bit in the short term, but they will speed you up in the long term.