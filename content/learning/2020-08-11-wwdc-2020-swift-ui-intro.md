---
title: "WWDC 2020: Introduction to SwiftUI"
date: 2020-08-11T09:30:00-00:00
slug: wwdc-2020-swift-ui-intro
link: https://developer.apple.com/wwdc20/10119
subjects: ["ios", "wwdc", "wwdc-2020"]
---

* In Xcode 12, select “multiplatform” setting when creating a new project. (iPhone, iPad, macOS).
* Add new views from canvas (preview window) or directly in code (no more storyboards).
* Cmd-click to add modifiers (either in canvas or code).
* List data items need to conform to `Identifiable`.
* Use an extension on the model to provide test data (for preview mode).
* Cmd-click and “extract code” to extract views into their own subviews.
* Pass data model to `List()` if entire list is data driven, but use `ForEach()` to add other items to the list (like a footer).
* Image modifiers like `contentMode` show instantly in preview!
* View is nothing but a `struct`
    * Doesn’t inherit any stored properties.
    * Allocated on stack.
    * Passed by value.
    * No additional allocation or reference counting for properties.
    * SwiftUI collapses view hierarchy, so make liberal use of small single purpose views.
    * Views are incredibly lightweight, extracting subview no runtime overhead.
    * Only requires `body` property.
    * Set breakpoint in body to see when framework decides it needs a refreshed view.
* `@State`
    * Allocates persistent storage for variable on view’s behalf.
    * Every time state variable is written view will re-render.
    * State variables and model constitute the SoT for entire app.
    * `@Binding` is read-write derived value (use for views that don’t own the object).
* Graph showing cure of bugs compared to mental overhead at ~28:30
* `withAnimation` to animate a property change.
* `@StateObject` for a class that acts as a store. 
* `@ObservedObject` is an object that is passed into a view that needs to be observed.
* `.environment` way to set contextual information that flows down the view hierarchy (note that `.environment`/`@Environment` is used for key paths which already exist and `.environmentObject`/`@EnvironmentObject` for custom objects/properties).