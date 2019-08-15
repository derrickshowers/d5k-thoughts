---
title: Learning Some Android Development
description: Some brief notes on learning the fundamentals of the Android platform.
slug: android
date: 2019-08-15T17:00:46.441Z
tags:
  - android
  - mobile
image: /images/uploads/android.jpg
bgOverlayOpacity: '0.50'
comments: 'true'
---
About a month ago, my daughter Sophie was born! And while I've been spending a ton of time enjoying life with her and Sarah, she does take frequent naps. Also, talking to a 1 month old baby doesn't exactly scream (pun intended) mental stimulation. So I decided to spend some time learning the basics of Android development... because... why not? Since I didn't take a bunch of CS courses in school, I also figured I could stand to learn the basics of what seems to be the world's most popular programming language, Java (even though I'd much prefer to learn Kotlin, but that will come later).

Anyhow, jotting down some of my notes on what I've learned so far. This is _very_ basic, but if you're reading this as a developer with any Android experience and see anything incorrect, please educate me! I've tried to nail down some of the most important concepts, and compile a list of what I still want to dig deeper into in the weeks and months to come. Hey, gotta start somewhere!

## General Thoughts

* Android development isn't all that much dissimilar to iOS development in that there is a declarative view layer described through XMLs (although unlike storyboard and nibs, it seems like much less frowned upon to actually _use_ them).
* Android Studio vs Xcode. For as much as people shit on Xcode (including myself), overall I think I like Xcode better. There is just too much cruft going on. There are a gazillion buttons in the menu bar and a gazillion +1 menu options. I'm sure this is all fine and dandy for those who are used to IntelliJ, but I like the simplicity of Xcode.
* I will say, though, some of the refactoring tools in Android Studio are quite impressive. 👍👍 Importing a class via alt-enter (and compiler hints when an import is no longer needed) 👍 Type a method name and then just alt-enter to create the method in the current class 👍 Code completion in general! 👍

## Java

* Surprised at how simple it is. Unless I'm missing key parts, seems much simpler to learn than Objective-C. It's very... intuitive! ...from its access keywords to class initializers.
* **[Anonymous Classes](https://docs.oracle.com/javase/tutorial/java/javaOO/anonymousclasses.html)** are pretty neat! Allows you to override a method without subclassing it.
* `JSONObject` makes it super easy to work with JSON. [Example](https://github.com/help-debug-examples/treehouse-stormy/blob/master/app/src/main/java/com/example/stormy/MainActivity.java#L98).

## Android

Some things I've found interesting or important when learning the basics.

* **Activities** are the main entry point for a view. Most of the learning I've done so far relied heavily or activities as being 1:1 with each view, but I think fragments are more commonly used for this. Need to look into fragments a bit more and understand the activity lifecycle better.
* **Intents** are used to pass data between activities. [Example](https://github.com/help-debug-examples/treehouse-interactiveStory/blob/master/app/src/main/java/com/example/interactivestory/ui/StoryActivity.java#L47) of name retrieved from an intent captured by a previous activity (`MainActivity.java` in this case).
* **Layouts** all built in XML. [Example](https://github.com/help-debug-examples/treehouse-interactiveStory/blob/master/app/src/main/res/layout/activity_main.xml).
* **Data binding** seems cool - allows you to bind an object with a view. See [this](https://github.com/help-debug-examples/treehouse-stormy/blob/master/app/src/main/res/layout/activity_main.xml) layout for an example.
* Accessing views in code is done via `findViewById()` (if not using data binding). [Example](https://github.com/help-debug-examples/treehouse-interactiveStory/blob/master/app/src/main/java/com/example/interactivestory/ui/StoryActivity.java#L42).
* Making buttons work is as simple as [setting an onclick listener](https://github.com/help-debug-examples/treehouse-interactiveStory/blob/master/app/src/main/java/com/example/interactivestory/ui/StoryActivity.java#L80).
* `R.java` class is interesting - the key to making `findViewById` work. It's a generated file with all IDs you assign in your layout (and strings, resources).

## Dig Deeper Into...

There is still much to learn! Here are some things I think might be valuable to dig a bit deeper into

* Activity Lifecycle and Bundles
* Fragments - I have a basic understanding here, but all of the content I've watched thus far primarily use activities. It seems fragments are the preferred way of doing things in Android, and while I understand these are basically a way to reuse views within an activity, I'm not quite sure how to set them up.
* Layouts (constraint vs relative vs frame - same as iOS?)
* LiveData
* Recycler Views
* Gradle (build system)

## Resources

* [Guide to App Architecture](https://developer.android.com/jetpack/docs/guide) - great resource shared by a friend that describes all the pieces to be used in a modern Android app.
* [Beginning Android](https://teamtreehouse.com/tracks/beginning-android)
* Example Project: [Interactive Story](https://github.com/help-debug-examples/treehouse-interactiveStory) - Basic stuff like moving between activities and setting up UI.
* Example Project: [Stormy](https://github.com/help-debug-examples/treehouse-stormy) - Hooking up a web API, storing data into models, binding view elements to data.

As mentioned at the top, feel free to leave any comments with corrections or suggestions on what I should look into a bit more to better learn Java and Android core concepts. Also leave any any courses, videos, or other recommended resources!
