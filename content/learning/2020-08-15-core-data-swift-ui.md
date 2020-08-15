---
title: "Fetching objects from Core Data in a SwiftUI project"
date: 2020-08-15T11:00:00-00:00
slug: core-data-Swift-ui
link: https://www.donnywals.com/fetching-objects-from-core-data-in-a-swiftui-project/
subjects: ["ios", "swift"]
---

Very timely as I’m trying to learn more about SwiftUI and CoreData, and don’t really know all that much about either. This article is a great intro to the simple approach with the `@FetchRequest` property wrapper followed with an example of separating data layer out into an `ObservableObject`. Also links in article to [architecture in SwiftUI 2.0](https://www.donnywals.com/using-core-data-with-swiftui-2-0-and-xcode-12/) and [debugging tips using launch arguments](https://www.donnywals.com/using-launch-arguments-for-easier-core-data-debugging/).

* `@FetchRequest` is easiest, but mixes SwiftUI code with data (like managed context and fetch requests).
* Add fetch request into an extension on the model to make view simpler (I love this idea!)
* Create an `ObservableObject` with `@Published` properties that then just gets passed into the view as `@ObservedObject` (uses `NSFetchedResultsContoller` to listen for changes to objects).