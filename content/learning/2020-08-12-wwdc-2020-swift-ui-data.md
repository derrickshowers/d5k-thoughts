---
title: "WWDC 2020: Data Essentials in SwiftUI"
date: 2020-08-12T08:00:00-00:00
slug: wwdc-2020-swift-ui-data
link: https://developer.apple.com/wwdc20/10040
subjects: ["ios", "wwdc", "wwdc-2020"]
---

* What to think about when creating a new SwiftUI view
    1. What data does this view need to do its job?
    2. How will the view manipulate that data?
    3. Where will the data come from? (SoT)
* Passed object to subview as a regular property, but because it’s a value type, would make a copy.
    * `@State` would create a new SoT.
    * `@Binding` is correct way (to be able to write from subview)
    * `$` needs to be used to pass the binding type.
* `ObservableObject`
    * `objectWillChange` is the only required method.
    * New SoT
    * One for entire app, or broken up
    * Add `@Published` to properties that might change (how does this work for CoreData?)
    * All views that use `@ObservedObject` will be notified on `objectWillChange` (will change so SwiftUI can collapse all changes).
* `@StateObject` (new in iOS 14) - SwiftUI owns the ObservableObject and is run just before body is called.
* `@EnvironmentObject` allows you to use an object in a deep down subview without a lot of boilerplate (i.e. passing it down through each view)
* Slow updates
    * Make view initialization cheap
    * Make body a pure function
* New updates for data persistence in iOS 14.