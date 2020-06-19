---
title: "Self Learning Playground: Property Wrappers"
date: 2020-06-19T11:00:00-00:00
slug: playground-property-wrappers
type: short-post
link: https://gist.github.com/derrickshowers/b550f7b4af8d0428d57c037a033ffee6
subjects: ["ios", "swift"]
---

Tried something different for today’s learning. Instead of using a specific resource, spent some time digging more into property wrappers (see [screencast](/learning/nsscreencast-property-wrappers) from other day). Copied playground over to a gist. Proved to help out my understanding quite a bit, so maybe I’ll try to do this more often (instead of just linking to existing resources).

Here’s what I learned:

* General setup of a new property wrapper
* `value` (backing property) vs `newValue` (enforced by compiler when creating a property wrapper)
* How to use `projectedValue` to get the actual property wrapper (to access something like an internal log)
* Without initial values for properties, property wrapper will not get called when setting initial values on initialization (unless I’m doing something wrong).
* General realization that this is a fancy way of doing property observers but can easily be shared (also allows you to manipulate the value before setting like in the case of stripping whitespace from a string property).