---
title: "WWDC 2020: Build SwiftUI Apps for tvOS"
date: 2020-07-08T10:00:00-00:00
slug: wwdc-2020-swiftui-tvos
link: https://developer.apple.com/wwdc20/10042
subjects: ["ios", "wwdc", "wwdc-2020"]
---

I was hoping I could get a feel for what it’s like to develop on tvOS, but not really. Just talks about some of the new SwiftUI goodness and how it can be applied to a tvOS app.

* CardButtonStyle for buttons that move around with remote (like all of Apple’s stuff)
    * Usage: `.buttonStyle(CardButtonStyle())`
* Context Menus now easy to implement
    * Usage: `contextMenu{}` modifier.
* Focus improvements
    * New `isFocused` environment variable.
* tvOS will geometrically determine what view should be focused (normally top left focusable element).
* Unrelated to tvOS (I think) is `@Namespace` modifier to provide a unique id (used in example to change an environment variable in just one view.
* Lazy Grids are a new SwiftUI thing and can be used to create a row of playlists in their example.