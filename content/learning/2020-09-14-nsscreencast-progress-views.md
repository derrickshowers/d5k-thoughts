---
title: "NSScreencast: SwiftUI Native Progress Views"
date: 2020-09-14T15:00:00-00:00
slug: nsscreencast-swiftui-progress-view
link: https://nsscreencast.com/episodes/444-swiftui-native-progress-views
subjects: ["ios", "swift", "swiftui"]
---

Overview of progress views in iOS 14.

* Basic `ProgressView` is a spinner
* Providing a precent complete, will give a linear style.
* New `Progress` type can be passed into `ProgressView` initializer, set as a published value on some controller.
    * He sets up timer using combine, very clean!
* Create your own progress view styles!
    * Triangle View
    * Circular View