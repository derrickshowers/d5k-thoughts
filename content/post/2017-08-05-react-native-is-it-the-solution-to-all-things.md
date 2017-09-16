---
title: React Native. Is it the solution to all things?
description: My thoughts on React Native
slug: react-native
date: 2017-06-17T18:39:36-07:00
tags: ["react","web","mobile"]
image: images/uploads/ReactNativeFeaturedImage.png
comments: true
bgOverlayOpacity: 0.7
---
An engineer who can write code so it works everywhere is the ultimate dream for many companies. We try to do the same thing across one *stack* even (“full stack” developer anyone?). Is this a dream or a reality? React Native seems to be tackling this battle and *maybe* they’ve come close to cracking it. Or maybe it’ll never happen and we’ll all be writing code for specific platforms… FOREVER 😱. After all, this has been an issue for a long, long time (PC and Mac in the 80s and 90s, and I guess still?). Is React finally solving this?

The case of React Native is an interesting topic for me – I’ve spent most of my career as a web developer (although admittedly very little React) and recently transitioned to iOS development (and I absolutely ❤️ Swift 😍). So, right now, I really don’t *want* to go back to writing JS, but I recently came across a talk from [UIKonf](http://www.uikonf.com/) that intrigued me to at least hear out the case for React Native. The interesting part about this talk is its perspective given by an iOS developer, not one of the millions of people out there who can’t stop talking about how great React is. He makes some interesting points, both for and against, which I’ve recapped below.

## First, the talk from UIKonf

<iframe width="560" height="315" src="https://www.youtube.com/embed/cZ4zQWgajBg?list=PLdr22uU_wISqntV4tQmx9H6sj9gMtj7nG" frameborder="0" allowfullscreen></iframe>

## My thoughts

### What did I learn?

* Teams can push updated JS bundles without resubmitting a binary to the App Store. Coming from web, the current situation on iOS is a huge change. If I break something, it’s in front of my users… potentially for a long time. It’s not just the time it takes for Apple to approve the app (which to be fair is getting *much* better), but users have to update the app and it’s even more important not to introduce new bugs with the fix.\

* With JS bundles, the only time an app would need to be recompiled (and resubmitted) is when changing or adding a native component (at least that’s my understanding). *See [Facebook’s docs](https://facebook.github.io/react-native/docs/native-components-ios.html)for details on how to create a new native component.*

* Concept of the bridge is important with React Native, especially in terms of performance. Native listeners use bridge to communicate with JS, JS then communicates back to a native component via this bridge. If JS communicates with native components too often, things might slow down, so this is where optimizations need to take place. Here’s an illustration I ripped off the internet – it’s also in the talk – helps understand this whole concept.

![React Native bridge diagram](/images/uploads/ReactNativeBridge.jpg)

* Hot reloading is… amazing. I was able to see this when briefly playing around with React Native awhile back and it is pretty impressive. No more waiting 5 minutes for a build to compile to see if constraints are configured correctly. The down side, though, is constraints don’t really exist, at least not in a Storyboard, so if you’re like me and find creating views in Storyboard – visually seeing how elements are laid out – to be oddly fun, well… you’re outta luck.

### So… React Native is the answer?

I don’t know. Here’s where I can see it being quite useful:

* You’re an agency or a freelancer and you want to build an app across multiple platforms quickly. You’re going to win business a lot easier if you can take the estimate and cut it in half (or even a third if you include web).

* What’s cool about React Native is you don’t have to apply it for the *entire* app – you can have sections written in React Native. I see this as being a great replacement for web views because that’s normally what happens when it’s too expensive to build something across multiple platforms. Facebook seems to take this approach with their ads section of the Facebook app, for example.

### So why *not* use React Native?

Well, I can only assume there are performance issues when building apps at scale. This is mentioned in the talk, but then reasons are given why this isn’t really an issue. I don’t know, I’m not convinced. Why would Facebook not write their entire app in React Native if this is really the case?

The talk also mentions bugginess and general concerns around the framework being young as reasons to avoid it, but those things are only issues a matter of time. Honestly, it seems like a lot of the avoidance is because developers don’t want to move away from Swift and the iOS ecosystem (myself included 🙋‍♂️).

What do you think? What are the pitfalls and why would this not be the answer to an age old issue of writing code that works across multiple platforms?
