---
title: "WWDC 2020: Sync a Core Data store with the CloudKit public database"
date: 2020-08-30T08:10:15-00:00
slug: wwdc-2020-core-data-cloudkit
link: https://developer.apple.com/wwdc20/10650
subjects: ["ios", "wwdc", "wwdc-2020"]
---

* Concepts (CoreData / CloudKit)
    * Objects - NSManagedObject / CKRecord
    * Models - NSManagedObjectModel / Schema
    * Stores 0 NSPersistentStore / CKRecordZone or CKDatabase
* `recordName` and `modifiedAt` need to be added in CloudKit dashboard for public databases.
* Good example for a public database would be a high score table.
* Public database does not support push notifications, uses polling.
    * Polling only happens on launch or after 30 minutes, data is not always up to date.
* Read/write access
    * For private databases, read/write/modify only when signed in.
    * For public databases, read available when not signed in, but write and modify need user to be signed in (some exceptions with modify)
* `canUpdateRecord` used to check if records can be modified
* `canDeleteRecord` will return false if record is stored in public database (changes won’t be propagated to other devices) - use something like `isTrashed` property on object.