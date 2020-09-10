---
title: "Swift Docs: Opaque Return Types"
date: 2020-09-10T08:00:00-00:00
slug: swift-docs-opaque-return-types
link: https://docs.swift.org/swift-book/LanguageGuide/OpaqueTypes.html
subjects: ["ios", "swift"]
---

Read through Apple’s docs on opaque return types (to better understanding from previous learning). I highlighted below some of the excerpts I found most helpful.

 * A function or method with an opaque return type hides its return value’s type information.
 * Unlike returning a value whose type is a protocol type, opaque types preserve type identity—the compiler has access to the type information, but clients of the module don’t.
 * You can think of an opaque type like being the reverse of a generic type. Generic types let the code that calls a function pick the type for that function’s parameters and return value in a way that’s abstracted away from the function implementation. Those roles are reversed for a function with an opaque return type. An opaque type lets the function implementation pick the type for the value it returns in a way that’s abstracted away from the code that calls the function.
 * Generally speaking, protocol types give you more flexibility about the underlying types of the values they store, and opaque types let you make stronger guarantees about those underlying types.