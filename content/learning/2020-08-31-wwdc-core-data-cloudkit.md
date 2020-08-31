---
title: "WWDC 2019: Using Core Data With CloudKit"
date: 2020-08-31T14:00:00-00:00
slug: wwdc-2019-core-data-cloudkit
link: https://developer.apple.com/wwdc19/202
subjects: ["ios", "wwdc", "wwdc-2020"]
---

First part of this session was showing how to get started from scratch letting Xcode setup everything needed for a Core Data app with CloudKit. There are some manual steps, like adding the capabilities (iCloud and CloudKit, Push Notifications, Background Modes - remote notifications), but the rest is done for you. It’s really as easy as replacing `NSPersistentContainer` with `NSPersistentCloudKitContainer`. Some other topics the presenter touched on:

* Everything from CloudKit is local
     * Read/write is faster locally, then syncs to CloudKit
     * `NSManagedObject` -> `CKRecord` by `NSPersistentCloudKitContainer`
* Some tips on using multiple stores for data segregation or keeping some objects local and others in the cloud.
* Toward the end, strategies on using relationships to better handle merging between devices.