---
title: "Effective Objective-C, Items 2, 3, 4"
date: 2020-01-18T00:00:00-00:00
slug: effective-objc-items-2-3-4
type: short-post
link: https://www.effectiveobjectivec.com
subjects: ["objective-c", "ios"]
---

* Item 2: Minimizing Import Headers in Headers
    * Put protocols in their own file so they can be imported separately in other header files, except delegate protocols because delegates can be implemented in class continuation category (in implementation file).
    * Always prefer conforming to protocol in implementation.
* Item 3: Prefer Literal Syntax over the Equivalent Methods
    * Prefer use for strings, numbers, arrays and dictionaries
    * Mutable array can be written `[@[@1, @2, @3, @4] mutable copy]`
* Item 4: Prefer Typed Constants to Preprocessor #define
    * Avoid preprocessor `#define` – lose type safety and can accidentally redeclare something with no compiler error.
    * `static` (for constants) tells compiler variable is "local to the translation unit" which is a fancy way of saying to the implementation file. Use this to avoid duplicate symbols when compiling (`static` and `const` means compiler doesn’t create a symbol at all, replaces occurrences just like `#define`).
    * `extern` in header file allows compiler to know there’s a constant with that name. Without it things won’t compile, but technically symbol is still created when `const int = 1` is added to implementation file.
