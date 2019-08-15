---
title: Thread Safety in Swift
description: A very simple look at what exactly thread safety means
slug: thread-safety
date: 2019-08-16T11:00:00.000Z
tags:
  - iOS
image: /images/uploads/threads.jpg
bgOverlayOpacity: '0.5'
comments: 'true'
---
"But is it thread safe?" 🤔

"Dependency injection is preferred over singletons, it's thread safe!" 😳

"Immutable models! Immutable models! Immutable models! Why? They're THREAD SAFE!" 🥺

Ok, I get it. Threads are to be safe. Always. But what exactly does that means? I've always understood the basic principle, thread safety means some value should not be able to be accessed by multiple concurrent threads, or else bad things happen. For instance, an algorithm powering an ATM isn't thread safe, and multiple people withdraw money from the same bank at the same time... well, uhh... UH OH! All that makes sense, but I wanted to _see_ what can happen when two threads access a value at the same time. In doing so, I found it's actually quite easy to grok when you break it down into something super simple. So that's what I'd like to do here.

Let's start with a jar of 500 dog treats (I have very spoiled pups 🐶).

```
class Jar {
    var dogTreats = 500
}
```

Now let's say we have a shared manager (singleton) we use throughout our app. This is common practice in a lot of iOS apps (even Apple uses it: `URLSession.shared`, `FileManager.default`, etc.). It's a very easy way to manage shared state throughout your app.

```
class DoggyTreatManager {
    let jar: Jar

    init(jar: Jar) {
        self.jar = jar
    }
}
```

Notice we inject an instance of our jar into it when we create it. So somewhere at the start of our app, we'd do something like `DoggyTreatManager(jar: Jar())`.

Alright, so now let's say we added a method that dispenses treats. For some reason this dispensing process requires a lot of computational power (like I said, spoiled pups 🤷‍♂️). Let's add this method to our `DoggyTreatManager` class:

```
func dispenseTreat(forDoggy doggy: String, numberOfTreats: Int) {
    print("\(numberOfTreats) of \(jar.dogTreats) treats about to be consumed by \(doggy).")

    guard jar.dogTreats >= numberOfTreats else {
        print("Not enough treats left for \(doggy)")
        return;
    }

    backgroundQueue.async { [weak self] in
        guard let strongSelf = self else { return }

        strongSelf.someReallyExpensiveCalculation()
        strongSelf.jar.dogTreats -= numberOfTreats

        print("\(numberOfTreats) treats consumed by \(doggy). There are \(strongSelf.jar.dogTreats) left.")
    }
}
```

Because of all the effort, we want to do this on a background thread, so we abstract that away in the implementation. After all, the consumer of this class likely is not aware dispensing a treat is so tough! 😰

By the way, if you're following along, you can define `someReallyExpensiveCalculation()` like so:

```
func someReallyExpensiveCalculation() {
    Thread.sleep(forTimeInterval: 2)
}
```

Alright, so now let's call these methods.

```
doggyStuffManager.dispenseTreat(forDoggy: "Winston", numberOfTreats: 400)
doggyStuffManager.dispenseTreat(forDoggy: "Walter", numberOfTreats: 300)
```

And here is the output:

```
300 of 500 treats about to be consumed by Walter.
400 of 500 treats about to be consumed by Winston.
400 treats consumed by Winston. There are 100 left.
300 treats consumed by Walter. There are -200 left.
```

Hmm... these spoiled pups got whatever they wanted! 🤔 This is because we removed treats from the jar on a background thread after putting it to sleep for 2 seconds. The `guard` at the beginning of the method is executed at the same time, when there are plenty of treats in the jar. Both threads are accessing the `dogTreats` value at the same time... before it gets updated!

One way to fix this is by using `NSLock`. However, this can be a little risky because if you lock a thread without unlocking it (or accidentally lock the same thread twice) you're caught in a **DEADLOCK**. 😱😱😱

Here is that `dispenseTreat` method rewritten using `NSLock`:

```
let lock = NSLock()
extension DoggyTreatManager {
    func dispenseTreatWithLock(forDoggy doggy: String, numberOfTreats: Int) {

        lock.lock();

        ...same as before...

        backgroundQueue.async { [weak self] in
            ...same as before...

            lock.unlock();
        }
    }
}
```

Works. I guess. But it's messy and in my opinion signifies a bigger issue with this code. The bigger issue is the mutable `dogTreats` property, as well as the singleton (`DoggyTreatManager`). Anyhow, refactoring further is out of scope for this post, but feel free to leave any comments with further suggestions or thoughts. Hope this helps give a little more clarity to what thread safety really means in practice!

It really helps to play around with this stuff. Download the [repo](https://github.com/help-debug-examples/thread-safety-playground) and open it up in a Playground.

Oh! I almost forgot! Would be rude not to end this post without showing off the spoiled pups who robbed the treat jar! 🐶🐶

![](/images/uploads/walter-winston.jpg)
