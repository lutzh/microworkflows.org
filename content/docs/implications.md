---
title: Implications
weight: 1
---

# Implications

Not using a workflow engine also means that the features they typically provide won't be available. Let's look at some of them, and what doing without them means for your system.


## Separate Observation From Control

A commonly stated advantage of workflow engines is the "end-to-end" view over the process.

There isn't really a reason though for mixing controlling the process (that is, knowing the whole process, the current state an invocation of the process is in, and driving the process by initiating the next step) with observation. We generally try to keep things simple in software architecture, and want to avoid coupling unrelated concerns.

Observability of the whole process is an understandable requirement, but is complete unrelated to managing the workflow itself. It usually also needs a different technical approach. When work is scaled out in a distributed system, there'll most likely be multiple executions of the workflow be running in parallel, on different nodes. For observability though, you want an aggregated view, across all nodes. This is why a system such as Temporal, for example, relies on Elastic Search for "advanced visibility".

You can achieve observability by introducing a "view" service, that only consumes events, but otherwise doesn't take part in the flow. This service can track the current state of the execution and make it queryable. It can also be used to send notifications on certain transitions, or track time spans between selected states.

So executing workflows, and observability of what's going on in your system, should be treated separately. Don't mix observability and control!


## Error Handling

Error handling is undoubtedly an important topic when dealing with a long running workflow. But not all errors are the same, so when we consider error handling, it makes sense to group the possible failures into categories. Let's see how much value a workflow engine adds for the following ones.

Temporary technical failures, e.g. timeouts
There is no need for a workflow engine to handle these. These can easily, and should, be handled within the individual microservices.

Errors in the real world
These should result in their own events.


## Timeouts

Again, let's go just a little bit deeper and look of the types of timeouts that can occur, and how to best handle them.
