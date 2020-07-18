---
title: "dotSwift 2020: MVC: Many View Controllers"
date: 2020-05-24T11:00:00-00:00
slug: dot-swift-mvc
link: https://www.dotconferences.com/2020/02/guilherme-rambo-mvc-many-view-controllers
subjects: ["ios"]
---


Main point of the talk is that using MVC isn’t as bad as everyone makes it out to be. Just use common sense and don’t throw everything into one view controller. He starts by going through a fictional example of a company who decides they want a new architecture and search medium for the latest and greatest (calls this MDD, “Medium Driven Development” 😂). The issue, he argues, is there’s so much attention and focus put toward rewriting the app, the product itself suffers. At the end of the presentation he sums this up into a quote: “Products are more important than the tools you use to make them”.

As far as some tips on splitting up code, he recommends the following four principles.

1. Container view controllers
    * Use child view controllers.
    * `UINavigationController` and `UIPageViewController` are `UIKit` examples, but you can create your own. Maybe something called `StateViewController` that handles a common loading, error, empty state, but allows you to pass in your own content view controller.
2. Generic Controllers
    * Example of a generic collection view cell container that uses a generic view.
    * Very powerful when mixing with containment view controllers!
3. View Controllers
    * What everyone is most familiar with, but use it only to set properties and layout views.
    * Don’t forget you don’t have to stick to an M, a V, or a C. Meaning, use view models or objects or helpers where you need to.
4. Flow Controllers
    * Owns a group of view controllers, similar to the coordinator pattern.
    * Use for flows (like a checkout flow).
    * Inherit from `UIViewController` to get lifecycle methods and let system take care of memory management (vs using an object)

Also check out the  [iOS Architecture Generator](http://iosarchitecture.top). 😂🤣 There’s also a [playground](https://github.com/insidegui/mvcwithsugar) for all this.