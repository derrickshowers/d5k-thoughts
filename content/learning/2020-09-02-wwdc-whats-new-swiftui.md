---
title: "WWDC 2020: What’s New in SwiftUI"
date: 2020-09-02T08:00:00-00:00
slug: wwdc-2020-whats-new-swiftui
link: https://developer.apple.com/wwdc20/10041
subjects: ["ios", "wwdc", "wwdc-2020"]
---

* Apps and Widgets
    * Complete app using SwiftUI
    * `body` can return a scene (vs only `some View` before)
        * `WindowGroup` for multiple windows (macOS and iPad)
        * `Settings`
        * `DocumentGroup`
    * `.commands` modifier adds custom menus and keyboard shortcuts.
    * Multiplatform templates in Xcode
    * Launch screen info.plist key to configure launch screen (instead of storyboard)
* Lists and Collections
    * Provide a children key path to add outlines to lists.
    * `LazyVGrid` and `LazyHGrid` (collection views?)
    * `LazyVStack` and `LazyHStack`
* Toolbars and Controls
    * `.toolbar` modifier
    * Labels can include icon (will decide when to show text, for example will not show text in toolbar)
    * `.help` modifier to tooltips on macOS (a11y for a11y on iOS)
    * `ProgressView` (spinner, progress bar)
    * `Gauge`
* New effects on styling
    * `.matchedGeometryEffect` for better transitions
    * `ContainerRelativeShape()` to match modifier to parent.
    * System accent color (in asset catalog)
* System integration
    * Link to URLs or other apps