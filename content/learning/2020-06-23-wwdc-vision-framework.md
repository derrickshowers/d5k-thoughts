---
title: "WWDC 2020: Detect Body and Hand Pose with Vision"
date: 2020-06-23T17:30:00-00:00
slug: wwdc-2020-vision-framework
type: short-post
link: https://developer.apple.com/wwdc20/10653
subjects: ["ios", "wwdc"]
---

* Existing
    * People
    * Face detection
    * Face landmarks
    * Human torso detection
* Hand pose (new)
    * What can be done?
        * UI control to take a selfie
        * Map emojis to hand movements
    * Four landmarks for each finger, 1 for the wrist
    * Demo: app to draw line on screen when tip of index finger and thumb are together
* Human body pose (new)
    * What can be done?
        * Apex of a jump
        * Work and safety poses for training
        * Fitness app for jumping jacks
* What’s the difference between ARKit and Vision? 
    * ARKit - newer, but fewer devices.
    * ARKit requires an AR session, so good for showing live on screen.
    * Vision framework is good for reading captured images.
    * Vision framework has more support, also can be used on macOS.
    * Seems like the preference is to go with ARKit when possible?