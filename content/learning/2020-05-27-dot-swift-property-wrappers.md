---
title: "dotSwift 2020: Property Wrappers"
date: 2020-05-27T07:00:00-00:00
slug: dot-swift-property-wrappers
link: https://www.dotconferences.com/2020/02/erica-sadun-property-wrappers
subjects: ["ios"]
---

Talk from Erica Sudan on property wrappers. She doesn’t go into a ton of detail on how to implement, more of a high level overview of what they are and how they came to be.

* Swift is constantly trying to keep compiler small, so there are a lot of “looks like language like features but not part of the language.”
    * Example: an operator. Just a function, but looks like it’s part of the language!
    * Trailing closure on an extension is another example.
* In SwiftUI `@State` looks like language, but not language. Quick help shows it as a struct, which is what it is. This is a property wrapper! Like operators and trailing closures, not part of compiler but looks like it’s part of the language.
* History of property wrappers:
    * Started out to remove duplicated logic from compiler (and into libraries instead).
    * Was originally proposal 30, now at 270. Was deferred for awhile. Re-proposed as 258.
* Uses
    * String trimming (use case like example she goes into detail on)
    * Thread safety properties
    * Barriers (exclusive reads and writes)
    * Syncing with stores/web services (common user defaults example, but also can be used with Core Data, or Firebase, or...)
    * Validation on assignment
    * Data configuration
* Bottom line: really a property observer that can be used (and named) throughout code. It’s a way of sharing property observers and not duplicating it throughout each class, extension, etc.