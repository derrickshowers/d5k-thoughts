---
title: "WWDC 2020: Diagnose Performance Issues with the Xcode Organizer"
date: 2020-08-03T14:00:00-00:00
slug: wwdc-2020-xcode-organizer
link: https://developer.apple.com/wwdc20/10076
subjects: ["ios", "wwdc", "wwdc-2020"]
---

Honestly, I had never even looked at the Xcode Organizer (window menu in Xcode), so learned that this exists! Short video about some of the changes in Xcode 12, mainly UI refresh and 2 new metrics.

* App analytics sent back via organizer window
* Xcode 11: battery usage, launch time, hang rate, memory usage, disk writes
* New metrics:
    * Scroll hitches
        * Hitch time (ms) / scroll duration (s) = hitch rate
            * < 5 ms/s - smooth
            * 5-10 ms/s - uh oh
            * > 10 ms/s - dropped frames
    * Disk write diagnostics
        * Reduce amt of writes: better perf and battery life
* Second half of video was demoing some of these new features and new UI.