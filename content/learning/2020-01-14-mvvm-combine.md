---
title: "MVVM with Combine Tutorial for iOS: ViewModels"
date: 2020-01-14T00:00:00-00:00
slug: mvvm-combine-2
link: https://www.raywenderlich.com/4161005-mvvm-with-combine-tutorial-for-ios
subjects: ["swift", "ios"]
---

* `ObservableObject` means that the class has properties that can be used as bindings.
* Keep a reference to `AnyCancellable`s to keep async alive, otherwise will not receive responses.
* See `WeeklyWeatherView.swift` and `WeeklyWeatherViewModel.swift` for what was done today.
    * **`WeeklyWeatherView.swift`**: Some good examples on how to organize SwiftUI (complete with no data layout before data is loaded)
    * **`WeeklyWeatherViewModel.swift`**: Lots of combine magic going on in here, see specifically how fetch happens and all the functional/declarative goodness in `fetchWeather(_:)`.

Link to work done so far: [Github](https://github.com/help-debug-examples/RWTutorial-CombineWeatherApp/tree/part2-viewmodel)

To be continued...