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

### Strategic Programming

The first step towards becoming a good software designer is to realize that working code isn’t enough. It’s not acceptable to introduce unnecessary complexities in order to finish your current task faster. The most important thing is the long-term structure of the system. Most of the code in any system is written by extending the existing code base, so your most important job as a developer is to facilitate those future extensions. Thus, you should not think of “working code” as your primary goal, though of course your code must work. Your primary goal must be to produce a great design, which also happens to work. This is strategic programming.

Strategic programming requires an investment mindset. Rather than taking the fastest path to finish your current project, you must  invest time to improve the design of the system. These investments will slow you down a bit in the short term, but they will speed you up in the long term.

## Modules Should Be Deep

### Modular Design
In modular design, a software system is decomposed into a collection of modules that are relatively independent. Modules can take many forms, such as classes, subsystems, or services. In an ideal world, modules would be ccompletely independent of each other. In this world, the complexity of a system would be the complexity of its worst module.

Unfortunately, this ideal is not achievable. Modules must work together by calling each others’s functions or methods. As a result, modules must know something about each other. For example, the arguments for a method create a dependency between the method and any code that invokes the method. If the required arguments change, all  invocations of the method must be modified to conform to the new signature. Dependencies can take many other forms,
and they can be quite subtle. The goal of modular design is to minimize the dependencies between modules.

In order to manage dependencies, we think of each module in two parts: an _interface_ and an _implementation_. The interface consists of everything that a developer working in a different module must know in order to use the given module. Typically, the interface describes what the module does but not how it does it. The implementation consists of the code that carries out the promises made by the interface. A developer working in a particular module must understand the interface and implementation of that module, plus the interfaces of any other modules invoked by the given module. A developer should not need to understand the implementations of modules other than the one he or she is working in.

> **For the purposes of this book, a module is any unit of code that has an interface and an implementation.**

The best modules are those whose interfaces are much simpler than their implementations. Such modules have two advantages. First, a simple interface minimizes the complexity that a module imposes on the rest of the system. Second, if a module is modified in a way that does not change its interface, then no other module will be affected by the modification. If a module’s interface is much simpler than its implementation, there will be many aspects of the module that can be changed without affecting other modules.

### What’s in an interface?

The interface to a module contains two kinds of information: _formal_ and _informal_. The formal parts of an interface are specified  explicitly in the code. For example, the formal interface for a method is its signature, which includes the names and types of its parameters, the type of its return value, and information about exceptions thrown by the method.

Each interface also includes informal elements. These are not specified in a way that can be understood or enforced by the programming language. The informal parts of an interface include its high-level behavior, such as the fact that a function deletes the file named by one of its arguments. If there are constraints on the usage of a class (perhaps one method must be called before another), these are also part of the class’s interface. In general,
if a developer needs to know a particular piece of information in order to use a module, then that information is part of the module’s interface. The informal aspects of an interface can only be described using comments, and the programming language cannot ensure that the description is complete or accurate. For most interfaces the informal aspects are larger and more complex than the formal aspects.

### Abstractions

> **An abstraction is a simplified view of an entity, which omits unimportant details.**

In modular programming, each module provides an abstraction in form of its interface. The interface presents a simplified view of the  module’s functionality; the details of the implementation are  unimportant from the standpoint of the module’s abstraction, so they are omitted from the interface.

In the definition of abstraction, the word “unimportant” is crucial. The more unimportant details that are omitted from an abstraction, the better. However, a detail can only be omitted from an abstraction if it is unimportant. An abstraction can go wrong in two ways. First, it can include details that are not really  important; when this happens, it makes the abstraction more  complicated than necessary, which increases the cognitive load on developers using the abstraction. The second error is when an abstraction omits details that really are important. This results in obscurity: developers looking only at the abstraction will not have all the information they need to use the abstraction  correctly. An abstraction that omits important details is a false abstraction: it might appear simple, but in reality it isn’t. The key to designing abstractions is to understand what is important, and to look for designs that minimize the amount of information that is important.

## Deep Modules

> **Deep modules are those that provide powerful functionality yet have simple interfaces.**

To visualize the notion of depth, imagine that each module is represented by a rectangle, as shown in the figure below. The area of each rectangle is proportional to the functionality implemented by the module. The top edge of a rectangle represents the module’s interface; the length of that edge indicates the complexity of the interface. The best modules are deep: they have a lot of functionality hidden behind a simple interface. A deep module is a good abstraction because only a small fraction of its internal complexity is visible to its users.

![Deep and Shallow Modules](/images/deep-and-shallow-modules.PNG "Deep and Shallow Modules")

Module depth is a way of thinking about cost versus benefit. The benefit provided by a module is its functionality. The cost of a module (in terms of system complexity) is its interface. A module’s interface represents the complexity that the module imposes on the rest of the system: the smaller and simpler the interface, the less complexity that it introduces. The best modules are those with the greatest benefit and the least cost. Interfaces are good, but more, or larger, interfaces are not necessarily better!

## Shallow modules

> A shallow module is one whose interface is complicated relative to the functionality it provides. Shallow modules don’t help much in the battle against complexity, because the benefit they provide (not having to learn about how they work internally) is negated by the cost of learning and using their interfaces. Small modules tend to be shallow.

## Conclusion

A shallow module is one whose interface is complicated relative to the functionality it provides. Shallow modules don’t help much in the battle against complexity, because the benefit they provide (not having to learn about how they work internally) is negated by the cost of learning and using their interfaces. Small modules tend to be shallow.