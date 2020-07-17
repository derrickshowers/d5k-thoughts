---
title: "WWDC 2020: App Essentials in SwiftUI"
date: 2020-07-08T10:30:00-00:00
slug: wwdc-2020-swiftui-app-essentials
type: short-post
link: https://developer.apple.com/wwdc20/10037
subjects: ["ios", "wwdc", "wwdc-2020"]
---

This session is all about creating an entire SwiftUI app using nothing but SwiftUI. Even thought I’m not really doing a lot of SwiftUI, interesting to see how they talk about the hierarchy between App, Scenes, View. Also this app is only a few lines of code (entire app!) and works on macOS, iOS, and watchOS!

* Hierarchy is App -> Scenes -> Views
* Scenes
    * Most common is a window.
    * Could be tabs, too.
    * Parent scene could hold several scenes (tabs).
    * Views contain the content of the scene.
* Scene defined with `WindowGroup` (there is also `DocumentGroup` for document based apps, they talk a little about this at the end of the video).
* `@main` attribute designates a struct as the main start point for an app (no longer need a main.swift file).
* Navigation title used to populate a title in app switcher (or expose on iPad).
* Merge into single window (into tabs) comes for free!
* All scenes have their own state.