---
title: "NSScreencast: SwiftUI Function Builders"
date: 2020-09-08T16:00:00-00:00
slug: nsscreencast-function-builders
link: https://nsscreencast.com/episodes/430-swiftui-function-builders
subjects: ["ios", "swift", "swiftui"]
---

Short 7 minute video worth checking out to understand function builders at a basic level. In reality all they are is a way to return multiple views in a closure. So for example, you want to return multiple `Text()` views, you use a `@ViewBuilder` decorator before the closure and it will compile.

Also interesting in this video is how to setup a view as a generic (he used a generic view as the `Content` of a custom modal).

See also: [Apple docs](https://developer.apple.com/documentation/swiftui/viewbuilder) on ViewBuilder.