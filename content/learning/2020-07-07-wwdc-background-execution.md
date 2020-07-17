---
title: "WWDC 2020: Background execution demystified"
date: 2020-07-07T11:00:00-00:00
slug: wwdc-2020-background-execution
type: short-post
link: https://developer.apple.com/wwdc20/10063
subjects: ["ios", "wwdc", "wwdc-2020"]
---

Almost didn’t watch because they started out saying it was more of an advanced course on background execution, but not really. Great overview of the different background modes and how the system prioritizes tasks based on a number of factors.

* Your app has its own concerns (stay updated, etc.), but that needs to be balanced with system concerns, including:
    * All-day battery
    * Performance
    * Privacy
    * Respecting user intent
* Factors considered when choosing whether or not your app can run:
    * Critically low battery
        * Below 20%, essential work only
    * Low power mode
        * Different from above because it’s user indicated.
        * Could be more restrictive, but app can access/be notified if it’s enabled.
    * App usage
        * Apps user uses the most, at the current time of day.
    * App switcher
        * Constraints to apps still visible in the switcher. Pretty much applies to all background tasks (if user closes app from app switcher).
    * Background app refresh switch
        * Defaults to on.
        * Notification when user enables/disables.
    * System budgets
        * Energy and data budget, distributed throughout the day.
        * Developer can tip this by:
            * Hardware intensive resourcess (GPS and acceleomater)
            * Using cellular data
    * Rate limiting
        * System reasonably spaces out launches depending on what’s appropriate.
* Specific background modes
    1. Background app refresh tasks - run app periodically in the background so app is fresh when user launches (social media feed, stock price, etc.)
    2. Background pushes - alerts the application not the user (low priority like muted messages, emails, etc.)
        * Factors: Everything except for app usage
        * Rate limiting _does_ apply. Delays the delivery of some pushes while maintaining a frequent launch pushes (so don’t depend on getting a silent push each time).
    3. Background URL sessions - downloads or uploads that are transferred to the system (file uploads, photo uploads, social media feed content)
        * Config option to prevent transfer from using cellular - use it!
        * `sessionSendsLaunchEvents` requests the system launch app after background transfer is complete.
        * `isDiscretionary` allows transfers to be deferred (when phone is plugged in, etc.)
        * When starting a task from background the system will ignore `isDiscretionary` and treat as true (only works on foreground)
        * Rate limiting and app usage do not apply to non discretionary transfers (except for launch event upon completion).
        * Discretionary transfers are only stopped by app switcher and _some_ system budgets (doesn’t even follow app refresh switch)
    4. Background processing task - tasks that take several minutes when user not accessing device while plugged in (CoreML  training!)