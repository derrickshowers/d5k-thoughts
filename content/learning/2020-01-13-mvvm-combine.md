---
title: "MVVM with Combine Tutorial for iOS: Data Layer"
date: 2020-01-13T00:00:00-00:00
slug: mvvm-combine-1
type: short-post
link: https://www.raywenderlich.com/4161005-mvvm-with-combine-tutorial-for-ios
subjects: ["swift", "ios"]
---

* Overview on MVVM
    * MVC is confusing because it's circular (view talks to controller, which talks to model and then back where model talks to controller which talks to view 😩)
    * With MVVM:
        * View -> ViewModel (not vice-versa)
        * ViewModel -> Model (not vice-versa)
        * View has no ref to the model
    * Advantages to MVVM: testing and views without a ton of business logic (that all goes in ViewModel)
    * Delegation can be used to communicate back to view, but you lose declarative approach.
* Data layer mostly makes sense, creating a data task that returns a publisher using `Decodable` to map server data to response object
* Still not 💯 clear on what `eraseToAnyPublisher` is doing 🤔

Link to work done so far: [Github](https://github.com/help-debug-examples/RWTutorial-CombineWeatherApp/tree/part1-datalayer)

To be continued...