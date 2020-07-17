---
title: "WWDC 2020: Design with iOS pickers, menus and actions"
date: 2020-06-24T13:00:00-00:00
slug: wwdc-2020-pickers-menus-actions
type: short-post
link: https://developer.apple.com/wwdc20/10205
subjects: ["ios", "wwdc", "wwdc-2020"]
---

* `UISlider` - small UI tweaks, matches macOS more.
* `UIActivityIndicatorView` - small UI changes, simpler looking.
* `UIPickerView` - minor changes, preference is to use `UIMenu` if it makes sense (see below).
* `UIPageControl` - small UI tweaks and allows unlimited pages.
* `UIColorPickerViewController` presented as a sheet or popover
    * Picking from a grid
    * Spectrum graident
    * RGB or hex codes
    * Eyedropper
* `UIDatePicker` - new calendar UI, compact or full options. No more for date/month/year!
* Menus (`UIMenu`)
    * `UIButton` and `UIBarButton` now have a `menu` property to easily add a menu.
    * `showsMenuAsPrimaryAction` causes the button to show immediately on touch.
    * `UIDeferredMenuElement` for dynamic menus
* Actions (`UIAction`)
    * No longer need to use target action.
    * Easier to share tap actions.