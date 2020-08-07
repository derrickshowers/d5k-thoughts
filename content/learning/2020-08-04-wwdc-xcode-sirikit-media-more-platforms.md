---
title: "WWDC 2020: Expand Your SiriKit Media Intents to More Platforms"
date: 2020-08-04T07:30:00-00:00
slug: wwdc-2020-sirikit-media-more-platforms
link: https://developer.apple.com/wwdc20/10061
subjects: ["ios", "wwdc", "wwdc-2020"]
---

Ok, so not a lot of information, but it is a short video. Specific to using media intents (audio) on Apple TV and HomePod. Basically media intents run on those platforms now, and there’s one new feature, alternative results.

* Apple TV
    * “Play music on your app”
    * Same way you implement on iOS (via intent extension)
    * Guess this works for HomePod, too? (they didn’t really say)
* New Features
    * Alternative options - “maybe you wanted” surfaces options user may have wanted by implementing `successes(resolvedMediaItems:_)` (plural version of what you would implement before)
* App prewarming can launch app sooner to do things like fetching data such as authentication details earlier (need to “work with Apple” to get this working, not sure what that means).