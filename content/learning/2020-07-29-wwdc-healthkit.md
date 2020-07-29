---
title: "WWDC 2020: Getting started with HealthKit"
date: 2020-07-29T07:30:00-00:00
slug: wwdc-2020-healthkit
link: https://developer.apple.com/wwdc20/10664
subjects: ["ios", "wwdc", "wwdc-2020"]
---

Overview of how to get started with HealthKit. Very basic, but great if you’ve never done anything with HealthKit before (like me!)

* Why use HealthKit?
    * Central repository for all health data developers can read and write to.
    * Takes care of syncing between devices.
    * Advanced queries to pull exact data you need.
* Setup
    * Give application access.
    * Check platform availability.
    * `HKHealthStore` - entry point to HealthKit API (one instance used throughout application).
* Authorization
    * Allow data by type (don’t request all types, over 100!)
    * Broken down to read and write
    * Only ask what you need, when you need it, every time you need it (in case permissions have changed).
* Hierarchy of data objects
    * `HKObject` (parent type which includes things like device that recorded it, unique identifier for data, application that wrote it).
        * `HKSample`
            * `HKQuantitySample` - used for any quantity types (walking with miles, hearing with db level)
            * `HKCategorySample` - list of values, no unit (an event like brushing teeth)
            * `HKWorkout` - multiple values
            * And others...
        * `HKCharacteristic` - static stuff like birthday, blood type.
    * Similar hierarchical chain for `HKObjectType`
* `HKStatisticsQuery` - get data based on certain conditions
    * Deduplicates data (iPhone and watch)
    * Collection type also available to get daily/weekly/monthly values.
    * Update handler to monitor changes to health data (use case: add steps to health data, update table view when data changes)
* `HKSampleQuery` for retrieving other data.
    * Also: `HKAnchoredObjectQuery`, `HKActivitySummaryQuery` (activity rings), `HKWorkoutRouteQuery`