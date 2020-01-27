---
title: "Effective Objective-C, Item 9"
date: 2020-01-24T00:00:00-00:00
slug: effective-objc-item-9
type: short-post
link: https://www.effectiveobjectivec.com
tags: ["objective-c"]
---

* Item 9: Use the Class Cluster Pattern to Hide Implementation Detail
    * Basic idea is having subclasses all inherit from the same superclass, and have the superclass return the subclass as itself
    * Keeps code from having a bunch of conditionals, and hides implementation details of the subclasses.
    * Example is `UIButton`, has multiple types, but always returns as a `UIButton` when initialized (`buttonWithType:`)
    * Any methods that need to be public, would be defined in base class and overridden.
    * No way to designate base class as abstract, use code documentation and do not provide initializers.
    * `NSArray` (and most collection types) are class clusters, that's how `NSArray` and `NSMutableArray` share code (all immutable methods, shared by both, are defined in the abstract class).