---
title: "WWDC 2019: Making Apps with Core Data"
date: 2020-09-01T15:00:00-00:00
slug: wwdc-2019-core-data
link: https://developer.apple.com/wwdc19/230
subjects: ["ios", "wwdc"]
---

* Core Data Stack. All under `NSPersistentContainer`
    * `NSManagedObjectModel`
    * `NSManagedObjectContext`
    * `NSPersistentStoreCoordinator`
* Context queues
    * `context.perform` and `context.performAndWait` sync and async.
    * `container.performBackgroundTask` is a convenience method to get background queue.
* Batch insertions can be used when inserting a lot of data at once (network request to sync from server).
* Managed objects support KVO, but Combine framework now supports binding with auto updates.
* `sortDescriptors` for sorting.
* `fetchBatchSize` for batched fetching.
* Fetched results controller (pass in fetch request instead of executing it) provides delegate methods to notify you of changes to a collection of data.
* Derived Attributes - for example, increment count based on a function (denormalization)
