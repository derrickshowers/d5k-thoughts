---
title: "NSScreencast: Swift Property Wrappers"
date: 2020-06-17T12:00:00-00:00
slug: nsscreencast-property-wrappers
type: short-post
link: https://nsscreencast.com/episodes/423-swift-property-wrappers
subjects: ["ios", "swift"]
---

Recommend that as a really simple overview of property wrappers. He starts out incredibly easy with a basic example to print anytime get or set happens on a value. Then expands from there.

* Property wrappers “encapsulate behavior around property access and then apply in multiple places.”
* First example simple printing, next example trim whitespace (also simple).
* Params can be added to property wrappers (e.g. `Clamped` using a `range` param).
* Add property wrappers _in_ property wrappers (Swift magic!)
* More advanced example: audit log for a property (logs all changes to that property) - use for an ATM to track balance.
    * Underscore version of the property gives us the property wrapper itself (e.g. `_balance` is property wrapper and `balance` is double)
    * `projectedValue` can be used to return the property wrapper so that you can do `$balance`. This could be better because you can access it anywhere `balance` is available while `_balance` is limited to its current scope. 
    * In example, would use to get the `changes` property of the property wrapper.