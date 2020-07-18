---
title: "dotSwift 2020: Integrating SwiftUI & UIKit"
date: 2020-06-05T13:00:00-00:00
slug: dot-swift-swift-ui-ui-kit
link: https://www.dotconferences.com/2020/02/ishmael-shabazz-integrating-swiftui-and-ui-kit
subjects: ["ios"]
---

* SwiftUI overview (data flow)
    * `@ObservedObject` gets passed down view hierarchy.
    * `@EnvironmentObject` gets injected into a view.
* SwiftUI has less bugs!
    * No autolayout
    * No storyboards (merge conflicts)
    * UI not out of sync because view is always updated.
* SwiftUI project adding in UIKit
    * Lots missing: toolbars, collection views, text views, AVPlayer, etc.
    * To expose something in SwiftUI just conform to `UIViewRepresentable` and `UIViewControllerRepresentable`.
    * There’s also the concept of a coordinator that sticks around for delegates in UIKit (not really a thing in SwiftUI because structs are created and destroyed).
    * Avoid using UIKit objects in places where they will be created and destroyed frequently (gave an example of a few collections views that are in views that get recreated on each keystroke).
* UIKit project adding SwiftUI
    * Just add `UIHostingController` with the root view set as the SwiftUI view.
    * Or add a `UIHostingController` via a storyboard.
    * That’s it! It’s that easy!