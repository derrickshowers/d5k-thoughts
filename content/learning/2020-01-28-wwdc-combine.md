---
title: "WWDC: Introducing Combine"
date: 2020-01-28T00:00:00-00:00
slug: wwdc-intro-combine
type: short-post
link: https://developer.apple.com/videos/play/wwdc2019/722/
subjects: ["swift", "ios", "wwdc", "wwdc-2019"]
---

* Current async interfaces (iOS 12 and below):
    * Target/action
    * Notification center
    * URLSession
    * Key-value observing
    * Ad-hoc callbacks
* Combine defines what is common among all of these, creating "a unified declarative API for processing values over time"
* Using Swift allows use of generics.
* Three parts: Publishers, Subscribers, Operators
* Publishers
    * Declarative part of the API, describes how values and error are produced, not what produces them.
    * Value type, so `struct`
* Subscribers
    * Counterpart to publishers, receives values.
    * Keeps state, so `class`
* How this works (~6:50)
    1. Subscriber likely held by a controller/view model.
    2. Subscriber calls `subscribe()` on the publisher.
    3. Publisher calls `receive(subscription:)` on the subscriber.
    4. Subscriber calls `request(_:Demand)` on the subscription.
    5. Subscription calls `receive(_:Input)` on the subscriber.
    6. Over and over again, until...
    7. `receive(completion:)` is called on the subscriber (includes an error).
* Operators
    * Describes a behavior for changing values.
    * Subscribes to a `Publisher`.
    * Sends result to a `Subscriber`.
    * Value type.
    * Common is `Map<Upstream: Publisher, Output>`.
    * Interesting convenience method for above at 9:50 (what is more commonly seen in code examples).
    * Lots of operators, could be hard to navigate, but composition first means there's a lot that do a little. Very readable!
    * Async operators take multiple async operations and send _one_ to subscriber (see `zip` or `combineLatest` operators). 👍👍 Sounds like dispatch queues, but much much nicer.
