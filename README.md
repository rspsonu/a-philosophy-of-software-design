# Summary - A Philosophy of Software Design

## Why do we need a philosophy?

The start of a software project is the point where the software is at it's simplest form. The speed of development is also the fastest at this stage. We could say that the software is least complex at this point. But since software is an ever changing entity with modifications, new feature requirements, bug fixes, etc., its complexity will inevitably increase. 

A developer needs to keep in mind all the relevant factors when changing software, so as to implement the new requirement without introducing bugs. As complexity increases, the relevant factors that a developer needs to consider also increases, slowing down the rate of development and also introducing bugs, which slows down development even further.

To tackle this problem, we need to design software that is simple. The complexity would still accumulate inspite of our best efforts, but we can keep it from becoming overwhelming. This book aims to provide us with a philosophy that can guide us in designing simple software.

> **Complexity is anything related to the structure of a software system that makes it hard to understand and modify the system.**

## Symptoms of Complexity

1. **Change amplification**: The first symptom of complexity is that a seemingly simple change requires code modifications in many different places. One of the goals of good design is to reduce the
amount of code that is affected by each design decision, so design changes don’t require very many code modifications.
2. **Cognitive load**: The second symptom of complexity is cognitive load, which refers to how much a developer needs to know in order to complete a task. A higher cognitive load means that developers have to spend more time learning the required  information, and there is a greater risk of bugs because they have missed something important.
3. **Unknown unknowns**: The third symptom of complexity is that it is not obvious which pieces of code must be modified to complete a task, or what information a developer must have to carry out the task successfully. An unknown unknown means that there is something you need to know, but there is no way for you to find out what it is, or even whether there is an issue.