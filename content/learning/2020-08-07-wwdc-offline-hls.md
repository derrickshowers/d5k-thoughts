---
title: "WWDC 2020: Discover how to download and play HLS offline"
date: 2020-08-10T07:30:00-00:00
slug: wwdc-2020-offline-hls
link: https://developer.apple.com/wwdc20/10655
subjects: ["ios", "wwdc", "wwdc-2020"]
---

* Ability to download HLS introduced in 2016.
* Use when user indicates they want to download media.
* How to get started?
    1. Create a download task
    2. Monitor the download task
    3. Play the downloaded content
* Download task
    * Inherits features of URLSession
    * Automatic media selection (current device locale downloads that language/subtitles)
    * Delegate method returns progress (around 4mins)
    * `AVAggregateAssetDownloadTask` allows you to set preference for which audio and subtitle renditions to download.
    * Download tasks will continue when app is backgrounded, get download task using `URLSessionConfiguration` and identifier used when setting up task.
* Playing a download
    * Location is returned when download is complete.
    * Reuse asset for playback so it will play before download is finished.
* Offline key to be used when you want to only allow content to be played offline for a certain amount of time (e.g. movie rental)
* Fast download vs high quality - allow the user to choose.
    * iOS 14 allows for presentation size as well.
* Storage management
    * Do not move, be prepared for assets to be deleted by system.
    * Allowing system to hander allows user to delete (shows up in storage settings).