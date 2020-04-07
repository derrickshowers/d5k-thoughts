---
title: "LLDB Debugging: UI"
date: 2020-04-07T14:00:00-00:00
slug: lldb-debugging-ui
type: short-post
link: https://medium.com/ios-os-x-development/dynamically-modify-ui-via-lldb-expression-1b354254e1dd
subjects: ["xcode", "ios", “debugging”]
---

I can never remember how to use LLDB when it comes time, and usually that’s in the most high pressure of moments. Jotting down a few notes on how to debug UI using LLDB. Some really powerful stuff here. See linked resource for more context and further details.

* Quickly get information on a view you’re looking at:
    1. `po [[[UIApplication sharedApplication] keyWindow] recursiveDescription]`
    2. Pick the memory address of the view from the hierarchy.
    3. `po id $view = (id)0x123456f9`
* To modify that view:
    1. `po [$view setBackgroundColor:UIColor.redColor]`
    2. Here’s the trick! Refresh the view with: `[CATransaction flush]`
* Couple random things I learned from reading this (and looking a few things up)
    * `po` , `p`, `e` are all aliases of `expression` (`po` runs command with the `-O` option, run `help expression` for details on what this does). Easy just to run `po` for everything.
    * With objective-c, I always had a hard time printing objects, but realized the issue is dot notation. Use brackets when running into `property ‘someProperty’ not found on object of type ‘someObject’`
    * This article adds `(void)` before sending a message to a selector (e.g. `(void)[CATransaction flush]`). It keeps from outputting anything, but doesn’t seem necessary.
    * Adding `--` after `expression` is only required when you have options (to separate options from code you want to run).