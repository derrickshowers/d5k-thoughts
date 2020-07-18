---
title: "Reverse Engineering an iOS app"
date: 2020-06-08T14:00:00-00:00
slug: linkedin-meetup-reverse-engineering
subjects: ["ios"]
---

_This was an internal meeting, so not going to post a lot of specifics, or a link, but still adding notes as a reminder_

* Two types of ways to reverse engineer a binary:
    * Static analysis (strings, otool, nm, class-dump, disassembler)
    * Dynamic analysis (debugger, network traffic)
* Where to find system binaries? Search for `RuntimeRoot`, there will be libraries for iOS, watchOS, and tvOS. For each library:
    * Localization files
    * Other resources
    * Binary files
* On device binaries are all in one place, harder to deal with (use Xcode versions instead)
* UIKit is small, links to a bunch of dependencies. Use UIKitCore for common UIKit stuff.
* Disassemblers: IDA and Hopper (preferred), also OS versions Ghidra, radare2