---
title: "Associated Type"
date: 2020-03-24T20:00:00-00:00
slug: associated-type
link: https://www.hackingwithswift.com/example-code/language/what-is-a-protocol-associated-type
subjects: ["swift", "ios"]
---

Jotted this down awhile ago as something I wanted to learn more about. I think it's because I was doing a lot with Combine and associated types are relied on heavily the types for publishers and subscribers.

* Found this resource because it was the most recent at time of looking into this. There is a lot of resources out there, so might be something more current when reading this. This is resource, though, is short and to the point.
* Easiest way for me to understand:
    1. I have a class that has a generic.
    2. I want to create a protocol and enforce that generic property/function.
    3. Associated type is identifies that generic in the profile, or from the article: "[associated types] mark holes in protocols that must be filled by whatever types conform to those protocols".
* Probably easier with a specific use case, but tried to put something together in a gist to describe a simple case where you want all models in your app to conform to a protocol where one of the properties is generic (in this case, `data`).
* In Combine this is important because the input type of the publisher and subscriber is generic, but must match each other.

_See [Gist](https://gist.github.com/derrickshowers/598179ead29b40e5efb795db563b7fdb)_