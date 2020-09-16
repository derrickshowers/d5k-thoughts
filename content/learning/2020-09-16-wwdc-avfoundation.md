---
title: "WWDC 2019: Advances in AVFoundation"
date: 2020-09-16T09:00:00-00:00
slug: wwdc-advances-avfoundation
link: https://developer.apple.com/wwdc16/503
subjects: ["ios", "wwdc"]
---

* Kinds of playback
    * Local file (.mov)
    * Progressive file (.mov)
    * HTTP live streaming (HLS)
* Automatic waiting for buffering
    * `automaticallyWaitsToEliminateStalling` or autoplay
    * paused -> waiting -> playing
    * `playImmediately(atRate:)` to skip waiting state (may lead to a stall)
    * `AVPlayer.rate` when player clicks play (works for both progressive and HLS) to automatically wait to buffer to avoid stalling.
    * Playback will auto resume when buffered (for network issues)
    * `AVPlayer.timeControlStatus` to get current status.
    * `AVPlayer.reasonForWaitingToPlay` to get the reason.
    * ~8:30 demo on slow network
* Simple way to loop playback
    * `AVQueuePlayer` is a subclass of `AVPlayer` to handle preroll (items to be played in the near future, not a playlist)
    * `AVPlayerLooper` implements the “treadmill” pattern.
* Best practices for being awesome
    * Create `AVPlayer` without a player item so it doesn’t start as audio only.
    * Call `replaceCurrentItemWithPlayerItem` after `play()` so it doesn’t show the first frame (might shave off a few ms).
    * Master playlist and content keys can be downloaded ahead of time.
    * `preferredForwardBufferDuration` to load more than what you need (set back to zero when starting playback)