---
title: "Content Offsets and Crashing Collection Views"
description: "It was many hours of debugging, but finally found the answer to a really annoying crash on iOS 10 and below... and it all had to do with content offsets!"
slug: collection-view-crash
date: 2018-03-25T01:45:08.869Z
tags:
  - iOS
image: /images/uploads/CollectionViewCrash.jpg
bgOverlayOpacity: '0.25'
comments: 'true'
---
Ok so this was a tricky one... which ended up taking quite a few hours to track down. In an effort to keep from forgetting about how I spent this particular Saturday afternoon tracking down this issue (since my memory is shit 👴🏻), and maybe help others who run into this issue, I thought I'd take some time to capture it in a quick blog post.

## The issue

![Layout Overview](/images/uploads/collection-views-layout-overview.gif)

So here's a quick demo. 👆 Pretty simple - a collection view above another view (in this case in a `UIStackView` so we can easily show/hide the collection view if necessary) with a bunch of cool guy cells. 😎 This works fine in iOS 11, but in iOS 10...

![Crash](/images/uploads/collection-views-crash-xcode.jpg)

## 😱

## Debugging

Now that I know the solution, it all seems pretty obvious, but it took me forever to arrive at this newfound feeling of complete clarity. I created this single page sample app to track down the issue for the app I work on for my 9-5. Well, the issue was rather difficult to reproduce, which made things very difficult to then track down. I tried everything to get it to crash to occur with the same behavior, but nothing seemed to work. Then, after reading the same console error over and over, something clicked! 💡

Here's the console error by the way:

```
2018-03-24 19:09:13.736 collection-view-woes[12299:136241] The behavior of the UICollectionViewFlowLayout is not defined because:
2018-03-24 19:09:13.736 collection-view-woes[12299:136241] the item height must be less than the height of the UICollectionView minus the section insets top and bottom values, minus the content insets top and bottom values.
2018-03-24 19:09:13.736 collection-view-woes[12299:136241] Please check the values returned by the delegate.
2018-03-24 19:09:13.736 collection-view-woes[12299:136241] The relevant UICollectionViewFlowLayout instance is <UICollectionViewFlowLayout: 0x7f94cdf0fb50>, and it is attached to <UICollectionView: 0x7f94ce849000; frame = (0 -17.5; 320 35); clipsToBounds = YES; autoresize = RM+BM; gestureRecognizers = <NSArray: 0x608000054190>; layer = <CALayer: 0x600000422620>; contentOffset: {0, 0}; contentSize: {0, 0}> collection view layout: <UICollectionViewFlowLayout: 0x7f94cdf0fb50>.
2018-03-24 19:09:13.736 collection-view-woes[12299:136241] Make a symbolic breakpoint at UICollectionViewFlowLayoutBreakForInvalidSizes to catch this in the debugger.
```

And the actual crash was: `EXC_ARITHMETIC (code=EXC_I386_DIV, subcode=0x0)` 🤔

## The Solution

I guess I sorta ignored most of the error because I knew when I was calculating the height of the cell, I was accounting for the section insets and didn't think I really needed to care about the content inset. Well, I was wrong 😞 The content inset was actually being automatically set to a value of 49! I'm actually still not too sure why this was the case and had a hard time replicating this, but 49 is the same height as the tab bar in the app I was trying to debug this for, so for some reason UIKit was automatically adjusting the content inset of my collection view... even though it's positioned no where near the tab bar. No bueno! 😡

The solution I ended up with was to reset the content inset to zero on all layout passes. This isn't ideal, but the other solution is to set `automaticallyAdjustsScrollViewInsets` to `false`. For some reason this didn't work when I set it on the view controller that contained my collection view... I had to additionally disable it on the main view controller, which is definitely not ideal.

So, bottom line, if you're running into this crash, check your content insets and make sure they're accounted for when you calculate the height/width of your self sizing cell. 👍 And you'll probably have to make sure they're zero if there's not a lot of extra room and you also have section insets. The section insets in addition to the content inset were greater than the collection view itself (hence the crash)!

## Other Resources

* [
'automaticallyAdjustsScrollViewInsets' was deprecated in iOS 11.0
](https://stackoverflow.com/questions/44390971/automaticallyadjustsscrollviewinsets-was-deprecated-in-ios-11-0)
* [UIScrollView has Difference Default contentInsets on iOS 11](https://medium.com/@hanru.yeh/ios-11-preliminary-experience-sharing-51be4de1b7d2)
* [Sample app](https://github.com/help-debug-examples/collection-view-woes) mentioned above

Feel free to comment if I'm missing something or you have an idea on why the content inset is being set in this scenario! Thanks! 👋
