---
title: "WWDC 2020: Meet WidgetKit"
date: 2020-06-24T15:00:00-00:00
slug: wwdc-2020-widget-kit
type: short-post
link: https://developer.apple.com/wwdc20/10028
subjects: ["ios", "wwdc", "wwdc-2020"]
---

* “Widgets are not mini apps”
* Siri shortcuts donations for smart stack.
* WidgetKitAPI to help decide when your widget is most relevant.
* 3 sizes (`.systemSmall`, `.systemMedium`, `.systemLarge`).
* Configuration options are built using intents framework.
* Inspiration from Watch complications.
* Setup
    * `StaticConfiguration` (activity) vs `IntentConfiguration` (reminders)
    * Placeholder UI is provided during initialization, placeholder interface when nothing available.
* Small single tap target, medium/large can have multiple tap targets.
* Views
    * Placeholder - before any content
    * Snapshot - first entry, quick to load
    * Timeline - series of subsequent views (combination of view and date)
        * Return 1 days worth of content
        * Reloads are where the system will wake up your extension
* ReloadPolicy - at end, after a date, never
    * Widgets viewed frequently will receive more reloads.
* Updates from timeline can occur by:
    * Background notification
    * App itself (when opened by user)
    * Background URLSession