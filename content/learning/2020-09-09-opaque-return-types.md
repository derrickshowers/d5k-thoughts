---
title: "Paul Hudson’s YouTube: Opaque Return Types"
date: 2020-09-09T15:30:00-00:00
slug: opaque-return-types
link: https://www.youtube.com/watch?v=DvHkeUxiwYY
subjects: ["ios", "swift"]
---

Still a bit confused on what opaque types are, but this video is a short and sweet explanation into them. Basically, when compared to a protocol (the most similar language feature), here are the differences:

* Protocol returns any sort of a thing and we don’t know what (other than the protocol type).
* Opaque type returns a specific sort of thing but we still don’t know what.

So for example, `Equatable` protocol we would define the underlying type that conforms to the protocol (e.g. a string) when we call it. Or, if it’s just an `Equatable` we have no idea it’s a string.

With `some Equatable` we don’t need to define the underlying type when we call it. It can just be some equatable. And we can compare that with some other equatable (compiler knows the underlying type is a string for instance).

Other things to know:
* Hides implementation details (can swap out what’s underneath in the future).
* Can only return one specific type.
* Anytime you see `some` it means opaque type.
* Introduced in Swift 5.1 (common in SwiftUI with `some View`.
