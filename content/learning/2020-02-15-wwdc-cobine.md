---
title: "WWDC: Combine In Practice"
date: 2020-02-15T10:00:00-00:00
slug: wwdc-combine-in-practice
link: https://developer.apple.com/wwdc19/721
subjects: ["swift", "ios", "wwdc", "wwdc-2019"]
---

* Notification center supports exposing its notification as a publisher.
    * Delivers notifications as output and cannot fail
    * Use map to get data from `userInfo`
    * New publisher whose output is data by using map operator.
    * New publisher whose output is `MagicTrick` (custom object) using decode operator.
    * Use `Just` to "just publish this value" synchronously (used when you already have a value, example is for a placeholder to always return a value).
* Subscribers, 3 rules:
    1. Publisher will call `receive(subscription:)` exactly once.
    2. Publisher can then provide 0 or more values `receive(_:)`
    3. Publisher can send at most a single completion (finished or failure) - no further values may be emitted.
* 4 types of subscribers
    1. Most simple: key path assignment `assign(to:on:)`
    2. `sink` operator to use closure.
    3. Subjects are a bit of a hybrid (publisher and subscriber). Use for imperative programming (existing codebases). 2 types:
        * Passthrough: stores no value, only see values after subscription.
        * CurrentValue: maintains a history allowing new subscribers to catch up.
    4. SwiftUI owns the subscriber, you just need a publisher.
* Cancellation
    * Offers a means to unsubscribe a subscriber.
    * New protocol `Cancellable`
    * `AnyCancellable` gives a way to automatically cancel subscriptions on `deinit`.
* Examples:
    * 25:25 simple example of using `@Published` property wrapper
    * 27:50 great example of `eraseToAnyPublisher` operator