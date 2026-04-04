---
title: "Microworkflows And .."
weight: 3
---

You may find the thought of basing your system on events and microworkflows, and not relying on any coordinator or workflow engine, a bit mind-bending. In fact, I believe the challenge lies not in technology or tools, but in the mindset. I'd like to provide some thought experiments that may make it easier to understand the philosophy behing microworkflows.

## .. Unix Philosophy

Think about the command line tools in your shell. They follow the [Unix Philosophy](https://en.wikipedia.org/wiki/Unix_philosophy), which has been summarized as:

- Write programs that do one thing and do it well.
- Write programs to work together.
- Write programs to handle text streams, because that is a universal interface.

Following this philosophy allows the assembly of complex processes by chaining various command line tools, and piping the output of one to the next via a standard channel (standard out/in).

Each command will accept the output of the previous as given facts. There's no reverse channel to communicate back to the previous command in case of an error! Instead, each program is responsible to deal with the input completely on its own. It'll usually transform the input in some way and write the result to standard out, or, in case of an error, will write some information to the standard error channel. There's no central coordinator that calls the programs and controls the overall process - it's not needed. So when trying to make sense of microworkflows, think of Unix command line tools. Just replace "text streams" with "event streams" in the above summary, and you have a basic description of the microworkflows approach.

## .. Stream Processing

Stream processing looks at data not as an amount of records (or bytes) that is stored somewhere and manipulated in place, but as a - possibly endless - continuous stream of events. In different stages, this stream is transformed. It's a common approach for use cases where new data is continously produced, e.g.

- IoT data, such as sensor data
- stock tickers
- clicks on a website

When processing these events, there's no back channel to the source. In stream processing, the incoming stream is accepted as a stream of facts. If an error occurs, it will be left to the current processing stage to deal with it, there's no calling back to a sensor or a stock ticker saying "processing of this information failed, so do something about it".

Try to think about your business system in this way. Instead of focussing on, for example, "the order workflow", where the design revolves around a single order and its state changes while being processed, think of it as a stream of incoming orders that will be transformed. E.g. a payment service transforms a stream of "OrderAccepted" events into "PaymentReceived" events. To get into the microworkflows mindset, think of your services as stream processing stages, where each stage implements a microworkflow.


## .. Agile

At first sight, this may seem a bit off, as microworkflows have clearly nothing to do with what kind of process you follow in your software development. Yet there's an interesting parallel when it comes to "scaling the process" vs "breaking down the problem".

Of the large enterprises with many development teams (and possibly many dependencies between their products), some follow an approach of "scaling agile", where they put some layer of higher-level coordination "on top" of the agile organization, to coordinate the outcome of many teams to achieve a common goal. "[SAFe](https://en.wikipedia.org/wiki/Scaled_agile_framework)" is a notorious example for this.

The problem is, there's a very high probability these enterprises will lose all the benefits of the agile approach. In such a setup, the teams will usually lose their autonomy and the ability to manage their tasks and timelines, as they're now governed by some overarching "release train" or such.

Many advocates of agile working (and I) are strongly against these so-called "scaled agile" approaches, and in fact demand a different mindset, as expressed well in this tweet:


I guess at this point you see the similarity: Don't "scale up" your system to handle complex workflows, instead "break down" the work into microworkflows.
