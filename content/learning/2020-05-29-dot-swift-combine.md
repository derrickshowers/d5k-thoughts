---
title: "dotSwift 2020: The Combine Triad"
date: 2020-05-29T14:00:00-00:00
slug: dot-swift-combine
link: https://www.dotconferences.com/2020/02/donny-wals-the-combine-triad
subjects: ["ios"]
---

* Hold onto `AnyCancellable` object, once this is deallocated the entire stream is torn down.
* The triad:
    1. Publishers
        * Create subscriptions
        * Connect subscriptions to subscribers
    2. Subscriptions
        * Obtain values by generating or receivi
        * Relay obtain values to subscribers (if demand is high enough)
    3. Subscribers

Rest of the video is reimplementing sink as an extension on `Publisher`. Followed by reimplementing the actual publisher. Likely will not have to build custom subscriptions and publishers, but a good way to learn how things work. In fact, Apple does not recommend doing this.