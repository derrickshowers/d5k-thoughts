---
title: "WWDC 2020: Meet the new Photos picker"
date: 2020-06-25T13:00:00-00:00
slug: wwdc-2020-photos-picker
type: short-post
link: https://developer.apple.com/wwdc20/10652
subjects: ["ios", "wwdc", "wwdc-2020"]
---

* If you use Photos picker, no more permissions prompting!
* `PHPickerViewController` gets config when initialized (images vs video, etc.)
* Delegate lets you know when photo or video is picked.
* PhotoKit might still be necessary when:
    * Non-destructive image editing
    * Photos library organization
* PhotoKit can be used with Photos picker. Photos picker can just serve as the UI so you don’t have to create your own and it’s more consistent with the rest of iOS (`PHPickerViewController`).
* Also new: Limited photos library. User can now select photos to be accessed.
* `AssetsLibrary` is deprecated, use `PhotoKit` (or even better, new Photos picker if you don’t need the extra stuff).