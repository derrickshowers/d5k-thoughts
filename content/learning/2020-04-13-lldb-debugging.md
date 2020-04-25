---
title: "LLDB Debugging: Overview"
date: 2020-04-13T14:00:00-00:00
slug: lldb-debugging-overview
type: short-post
link: https://medium.com/flawless-app-stories/debugging-swift-code-with-lldb-b30c5cf2fd49
subjects: ["xcode", "ios", "debugging"]
---

The other day I [posted](https://blog.derrickshowers.com/learning/lldb-debugging-ui) about lldb debugging to debug the UI and that took me down a bit of a rabbit hole. So I stopped! And saved this article I found for another rainy day. Luckily it is _actually_ rainy today, so here we go.

First and foremost, print this or keep this somewhere it's easy to access. [LLDB commands map](https://www.dropbox.com/s/9sv67e7f2repbpb/lldb-commands-map.png?dl=0)

* Output using `e` (`p` and `po` are shortcuts), but also _change_ variable using `e` and variable without the `$`. (ex: `e sum = 4`)
* Use `help expression` to explore flags, but highlights:
    * `O` for object descriptions
    * `T` for types when dumping values
* `bugreport` sounds interesting, outputs a stack trace for where you're currently stopped (`bugreport unwind --outfile <path>`).
* Continue button shortcut is to just type `c` (short for `process continue`)
* Step over button shortcut is `n` (short of `thread step-over`)
* Get info on current thread with `thread info`.
* `command` lets you create a file with a list of commands (use `command source <path>`)
* Honorary mention in case I ever run into it, the `language` command offers a set of commands specific to a source language (e.g. `language swift refcount`.