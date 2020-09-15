---
title: "NSScreencast: SwiftUI Button Styles"
date: 2020-09-15T16:00:00-00:00
slug: nsscreencast-swiftui-button-styles
link: https://nsscreencast.com/episodes/437-swiftui-button-styles
subjects: ["ios", "swift", "swiftui"]
---

* `ButtonStyle` protocol using `makeBody` method, return `some View`.
* Provides a `Configuration` object that has the label
* Full width button very easy using `.frame(maxWidth: .infinity)`
* `Configuration also provides `isPressed` (for instance, to darken when button is tapped).
* Implicit animations (downward direction) for `isPressed`
* Use `AnyView` for type erasure - works in a ternary operator when compiler needs to know both conditions are the same type.
* Side note: `Color.secondary` and `Color.accentColor` are default color schemes