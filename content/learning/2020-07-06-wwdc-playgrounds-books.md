---
title: "WWDC 2020: Create Swift Playgrounds content for iPad and Mac"
date: 2020-07-06T14:00:00-00:00
slug: wwdc-2020-playgrounds-books
type: short-post
link: https://developer.apple.com/wwdc20/10654
subjects: ["ios", "wwdc", "wwdc-2020"]
---

Not a lot of in depth information on creating a Playgrounds book, just comparing the differences between Mac and iPad. Second half of the session is a demo where a button is conditionally shown on iPad for an ARKit experience (cool that you can do ARKit in Playgrounds!).

* Differences between platforms (Mac and iPad):
    * Code completion includes quick help on Mac and presented in a popover like view.
    * Designate which device the book is supported with key in manifest (iPad or Mac).
    * `UIRequiredDeviceCapabilites` to target capabilities (ARKit, Microphone, WiFi).
    * Use generic words like tap or select (instead of click or touch) in documentation/comments.
    * Use target checks for conditionals (similar to in app code).