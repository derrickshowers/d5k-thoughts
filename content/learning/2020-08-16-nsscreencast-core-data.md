---
title: "NSScreencast: Core Data in iOS 10"
date: 2020-08-16T12:00:00-00:00
slug: nsscreencast-core-data
link: https://nsscreencast.com/episodes/238-core-data-in-ios-10
subjects: ["ios", "swift"]
---

* In data model setup, there is an option to set the core data model as an extension. This allows you to create your own models and Core Data specific properties and methods placed on extension.
* New in iOS 10 `NSPersistentContainer`. Before it was much harder to setup the Core Data stack.
* Container is async, KVO to know when container is available (none of this necessary with SwiftUI).
* `NSFetchedResultsController` gets the fetch request (has the delegate to respond to changes and `peformFetch()` to initiate the fetch).
    * Interesting, also separates data into sections to make it easy to implement with table and collection views (section is determined by passing a key path, see [docs](https://developer.apple.com/documentation/coredata/nsfetchedresultscontroller)).
* `performBackgroundTask:` from container gives you a background context.
* `automaticallyMergesChangesFromParent` ensures changes on contexts save up through the chain.
* Not in video, but interesting to note, Core Data can be backed by a number of storage options, (including in memory). SQLite is the default.