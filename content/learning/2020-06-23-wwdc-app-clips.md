---
title: "WWDC 2020: Explore App Clips"
date: 2020-06-23T13:00:00-00:00
slug: wwdc-2020-app-clips
type: short-post
link: https://developer.apple.com/wwdc20/10174
subjects: ["ios", "wwdc", "wwdc-2020"]
---

* Create second application target, contains all code and assets to handle app clip experiences.
* Requires an app as well, needs to be submitted together.
* Make as small as possible (must be less than 10mb after thinning).
* Reorganize app into user flows to better use app clips (so a user can pick up where he/she left off in the app clip)
* Cannot access to all personal data (like health kit), but use checks as normal to see if data is available.
* Access to all iOS frameworks.
* App clips not included in iOS backups and will be deleted after inactivity.
* Cannot register for universal links or URL schemes.
* App clips can store data, but treat as temporary cache because app clip can be removed after inactivity.
* Automatically migrate authorizations for camera, microphone, bluetooth access to main app (if installed).
* Data can be stored in a shared data container (not default) and full app can pull from it.
* `SKOverlay` to be lead to full app (new).