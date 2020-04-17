---
title: "WWDC 2019: Introducing Combine"
date: 2020-04-17T10:00:00-00:00
slug: wwdc-introducing-combine
type: short-post
link: https://developer.apple.com/videos/play/wwdc2019/722
subjects: ["ios", “swift”, “wwdc”]
---



* Current available async interfaces: target/action, KVO, notification center, `URLSession`, key-value observing, callbacks.
* Combine _combines_ all of these into a unified API for processing values over time.
* Features: heavy use of generics, type safe, composition first (core concepts are easy, but powerful put together)
* Publishers
    * Value type (`struct`)
    * Defines how values are produces.
    * Doesn’t send the actual value, that’s the job of the subscriber.
    * Declarative part of the API.
    * One function: `subscribe:`, returns a subscription.
* Subscribers
    * Reference type (`class`)
    * Counterpart to publishers.
    * Main functions: `receive:`, `receive:subscription:`, `receive:completion:`.
* How does this fit together? The publisher’s `subscribe:` function gets called, returns the subscription. The subscription then requests `n` number of values from publisher.
* Operators (Second half of video is focused 100% on specific operators such as combineLatest, zip, compactMap, filter, ...)
    * Describes a behavior for handling values (simplest example is turning a notification object into a primitive type to match subscriber).
    * Subscribes to a publisher (“upstream”), sends results to a subscriber (“downstream”).
    * Instead of a small amount of operators that do a lot, framework provides a lot of operators that do a little (adheres to overall mission of composition).