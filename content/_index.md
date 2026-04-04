---
title: The Microworkflow Pattern
---

When you need to implement a complex workflow across multiple microservices, don't immediately turn to workflow engines, or implementing e.g. the saga pattern. Instead, consider breaking up the workflow into chunks, or microworkflows.

## What is a Microworkflow?

A microworkflow is a set of process steps that is triggered by an event, emits one or more events, and is implemented within a single microservice.

## The Pattern

Microworkflows is an [architectural pattern](https://en.wikipedia.org/wiki/Architectural_pattern), i.e. a general, reusable solution to a commonly occurring problem in software architecture within a given context.

**Context:** You are building or evolving a system based on microservices and asynchronous, event-driven communication. Business processes span multiple services and involve several steps.

**Problem:** As the business process grows in complexity, there is a temptation to introduce a central coordinator, a workflow engine, or to implement patterns like saga with a dedicated orchestrator. This creates coupling, concentrates logic in a single place, and undermines the autonomy of individual services.

**Solution:** Break down the complex end-to-end workflow into small, self-contained workflows. Each microworkflow is triggered by an event, performs its processing within a single microservice, and emits one or more events when done. No service needs to know the overall process. Each service only reacts to the events it cares about and publishes the results of its own work. The complex workflow emerges from the composition of these simple, independent microworkflows.

**Consequences:** Services remain autonomous and loosely coupled. Each microworkflow is simple enough to understand, test, and maintain in isolation. There is no single point of failure controlling the overall process. On the other hand, the end-to-end flow is not visible in any single place, and observability requires a separate approach (see [Implications](docs/implications)).

**Example:** Consider an order process. Instead of one orchestrator that calls payment, inventory, and shipping in sequence, each service implements its own microworkflow. The payment service listens for `OrderAccepted` events and emits `PaymentReceived`. The inventory service listens for `PaymentReceived` and emits `ItemsReserved`. The shipping service listens for `ItemsReserved` and emits `ShipmentScheduled`. No service knows about the others. The order process simply happens.

**Related:** [Unix Philosophy](docs/related#-unix-philosophy), [Stream Processing](docs/related#-stream-processing), [Choreography](docs/orchestration-vs-choreography)
