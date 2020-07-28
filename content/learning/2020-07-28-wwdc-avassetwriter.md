---
title: "WWDC 2020: Author Fragmented MPEG-4 Content With AVAssetWriter"
date: 2020-07-28T07:30:00-00:00
slug: wwdc-2020-avassetwriter
link: https://developer.apple.com/wwdc20/10011
subjects: ["ios", "wwdc", "wwdc-2020"]
---

* Workflow: source material -> media encoder -> segmenter -> web server
* AVAssetWriter - outputs media in fragmented MP4 format.
* Either source file or capture (live) video to fragmented files via AVAssetWriter.
* Format structure
    * MP4: file type, movie, media data
    * Fragmented movie (fMP4): file type, media data, movie, media data, movie fragment, media data, movie fragment,...
* Code example of how to configure AVAssetWriter (~5:30).
* Lots of detailed examples throughout rest of session.