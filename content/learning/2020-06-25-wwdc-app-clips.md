---
title: "WWDC 2020: Create app clips for other businesses"
date: 2020-06-25T14:00:00-00:00
slug: wwdc-2020-app-clips-other-businesses
link: https://developer.apple.com/wwdc20/10118
subjects: ["ios", "wwdc", "wwdc-2020"]
---

Not really applicable unless you have a Yelp-like app, but interesting to learn about how App Clips are all separate apps from the user perspective, but all just open your app. Developer is responsible for handling different “skins” of the app for each business.

* Who is this good for?
    * If your app aggregates many businesses in to a customer-facing app (Yelp!)
    * If your app is a rewards program.
* Entry point for App Clips: Messages, smart app banner, NFC/QR, location based suggestions.
* `targetContentIndentifier` in user defaults should be used to send notification to the correct app clip experience (all separate apps)
* Developer should save state in case user opens another app (still your app, but different content identifier) but then wants to go back to original app.
* App clip card designed in App Store Connect.
* Each app clip gets it own icon which comes from Maps (what happens for businesses that aren’t location based?)
* Access App Clips via recently added, spotlight, proactive suggestions, messages, maps and safari