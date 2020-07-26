---
title: "WWDC 2020: Create quick interactions with Shortcuts on watchOS"
date: 2020-07-26T08:30:00-00:00
slug: wwdc-2020-shortcuts-watchos
link: https://developer.apple.com/wwdc20/10190
subjects: ["ios", "wwdc", "wwdc-2020"]
---

* Shortcuts app (on watch)
    * Choose which shortcuts to sync to watch.
    * Complications to launch specific shortcuts.
* Recap how you can offer shortcuts
    * `SiriKit` and `NSUserActivity`
* If using `NSUserActivity`, app needs to open on device, will not work on watch because it’s a jarring experience to open an app on a different device.
* Intents is the way to go, but...
    * IntentsUI does not work on watch
    * Best option is to have a watch app if user needs to do something in app
    * If no watch app, run via extension (creating a separate target for watch intent)
    * Final option, remote execution. Slower. Needs to run completely in background (`.continueInApp` cannot be used, need to support background execution).