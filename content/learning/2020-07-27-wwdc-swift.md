---
title: "WWDC 2020: What’s new in Swift"
date: 2020-07-27T08:00:00-00:00
slug: wwdc-2020-swift
link: https://developer.apple.com/wwdc20/10170
subjects: ["ios", "wwdc", "wwdc-2020"]
---

* Xcode 12 Swift 5.3
* Runtime
    * Code size smaller (Swift 4 2.3x Objc version, 5.3 down to 1.5x)
    * SwiftUI app 43% reduction (Xcode 11 to Xcode 12)
    * See ~4:00 for interesting memory layout example, why value types are more performant.
    * Heap usage overhead uses a third of what it did.
    * Sits below foundation framework, can be used where previously C has to be used.
* Improvements to diagnostics and code completion (speed and accuracy)
* Increased robustness in debugging (lldb)
* Official support for windows
* New language features
    * Multiple trailing closure closure syntax (SE-0279)
    * KeyPath expressions as functions (SE-0249)
    * `@main` (SE-0281)
    * Increased availability of implicit self in closures (SE-0269) - including self in capture list doesn’t mean you need it in the body or if struct can remove it.
    * Multi-pattern catch clauses (SE-0276)
    * Enum enhancements
    * Embedded DSL enhancements
    * And more...