---
title: 'Threads, Dispatch Queues, and Operation Queues – Oh my!'
description: I can never remember how all this stuff works, so here's my attempt to summarize it for my future self.
slug: concurrency
date: 2017-07-29T18:45:18-07:00
tags: ["iOS"]
image: /images/uploads/GrandCentral.jpg
comments: true
---
There are so many concepts when it comes to handling concurrency, events, threads (whatever you want to call it) for iOS. Maybe it’s because I come from the world of browsers where we don’t really have to worry too much about this sort of thing. Maybe it’s because I don’t have to worry about it on a day-to-day basis. Whatever the reason, I always forget how this works. I’ll spend hours reading articles, searching Stack Overflow, watching videos, but then a month down the road I don’t remember anything. Here’s my attempt to remember it all and have a place of reference. If it benefits you, too, well then great!

*(Disclaimer: since I’m still learning this, I can’t guarantee everything here is 100% accurate, but I’ll add references to as much of it as I can. Feel free to leave comments, too!)*

## Threads

As far as I can tell, iOS handles a lot of this for you with Grand Central Dispatch. According to [Apple’s docs](https://developer.apple.com/documentation/dispatch) “work submitted to dispatch queues are executed on a pool of threads fully managed by the system.” So I guess there’s not too much to remember here, other than there are a pool of threads, one being a main thread (sometimes referred to as the UI thread), the system manages to make things as performant as possible (via things like concurrency and parallelism explained in detail under “GCD Concepts” [here](https://www.raywenderlich.com/148513/grand-central-dispatch-tutorial-swift-3-part-1)).

## Dispatch Queues

The `Dispatch` class contains the interface for Grand Central Dispatch. It is used to run tasks on other threads through the use of queues. There are a few different types of queues:

* *Main*: This is what everything runs on unless you specify otherwise. All UI updates need to be done on this queue. It corresponds directly to the main thread.

* *Global Queues*: I like to think of this as preset queues. You specific a type of queue and the system is responsible for prioritizing it appropriately. The queues are (in order of priority): `userInteractive`, `userInitiated`, `utility`, `background`.

* *Custom Queues*: You give your queue a name and a `qos` value (one of the values listed above). I’m not all too sure why you would use a custom queue, but some advantages I read are: easier to debug due to having a name associated with what it’s doing and more configurable. (Add a comment if I’m wrong or if there are better reasons for custom queues.)

### Sync and Async

Just a quick note since `.sync` and `.async` are in all calls to `Dispatch`. Sync (rarely used on the main queue) means that control will not return back to the caller until the entire call stack is complete. Async will return control back to the caller immediately.

## Operation Queues

Still have a lot of research to do on operation queues, but from my limited understanding, `NSOperationQueue` is more about scheduling tasks and managing them at a lower level. Grand Central Dispatch takes care of the lower level tasks for you, but could be a bad thing for certain implementations. An example in one of [these](https://stackoverflow.com/questions/40764140/operationqueue-main-vs-dispatchqueue-main) Stack Overflow answers is a login sequence of an application.

* [Stack Overflow – Operation Queue vs Dispatch Queue for iOS Application](https://stackoverflow.com/questions/7078658/operation-queue-vs-dispatch-queue-for-ios-application)

## Other Stuff

### Run loops

From [Apple’s documentation](https://developer.apple.com/library/content/documentation/Cocoa/Conceptual/Multithreading/RunLoopManagement/RunLoopManagement.html), a run loop is: “the fundamental infrastructure associated with threads. A run loop is an event processing loop that you use to schedule work and coordinate the receipt of incoming events. The purpose of a run loop is to keep your thread busy when there is work to do and put your thread to sleep when there is none.”

There doesn’t seem to be a lot of recent documentation for run loops, I’m guessing it is because as a developer you don’t really need to worry about them too often. Each thread has a run loop, which is responsible for responding to events, and can be anything from user events (touches, shakes, etc.) to networking events.

Looking through Apple’s [NSRunLoop](https://developer.apple.com/documentation/foundation/nsrunloop) documentation helps gain a little clarity on what you can do with run loops. I also found the answer to [this Stack Overflow question](https://stackoverflow.com/questions/12091212/understanding-nsrunloop) to be a good explanation.

## Resources

* [Video series from Ray Wenderlich](https://videos.raywenderlich.com/courses/55-ios-concurrency-with-gcd-and-operations/lessons/1) – I haven’t watched this yet, but plan to in the near future!

* [Tutorial from Ray Wenderlich](https://www.raywenderlich.com/148513/grand-central-dispatch-tutorial-swift-3-part-1) – lots of great, detailed info here

* [Another great tutorial](https://www.appcoda.com/grand-central-dispatch/) – Follow along with this one to see how all the different dispatch priorities work!
