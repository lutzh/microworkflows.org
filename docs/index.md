---
layout: default
title: Microworkflows
---

When you need to implement a complex workflow across multiple microservices, don't immediately turn to workflow engines, or implementing e.g. the saga pattern. Instead, consider breaking up the workflow into chunks, or microworkflows.


# What is a Microworkflow?

A microworkflow is a set of process steps that is triggered by an event, emits one or more events, and is implemented within a single microservice.

(Image of Microworkflow)


# The Microworkflow Pattern

Microworkflows is an [architectural pattern](https://en.wikipedia.org/wiki/Architectural_pattern) is (i.e. a general, reusable solution to a commonly occurring problem in software architecture within a given context), and can be described in a [design pattern](https://en.wikipedia.org/wiki/Software_design_pattern) style:


Pattern Name and Classification: Microworkflows (Distributed Systems Pattern)

Intent: A description of the goal behind the pattern and the reason for using it.

Also Known As: Other names for the pattern.

Motivation (Forces): A scenario consisting of a problem and a context in which this pattern can be used.

Applicability: Situations in which this pattern is usable; the context for the pattern.

Structure: A graphical representation of the pattern. Class diagrams and Interaction diagrams may be used for this purpose.

Participants: A listing of the classes and objects used in the pattern and their roles in the design.

Collaboration: A description of how classes and objects used in the pattern interact with each other.

Consequences: A description of the results, side effects, and trade offs caused by using the pattern.

Implementation: A description of an implementation of the pattern; the solution part of the pattern.

Sample Code: An illustration of how the pattern can be used in a programming language.
Known Uses: Examples of real usages of the pattern.

Related Patterns: Other patterns that have some relationship with the pattern; discussion of the differences between the pattern and similar patterns.



# Why Microworkflows?


## Issues of Workflow Engines and Self-Built Coordinators


