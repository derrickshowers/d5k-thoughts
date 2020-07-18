---
title: "WWDC 2020: Lists in UICollectionView"
date: 2020-07-16T14:00:00-00:00
slug: wwdc-2020-lists
link: https://developer.apple.com/wwdc20/10026
subjects: ["ios", "wwdc", "wwdc-2020"]
---

Overview of all the new additions to collection views as far as lists (think UITableView). There’s lots of neat improvements including self sizing cells being default and just generally more dynamic and flexible with sizing.

* UITableView-like appearance
* Optimized self sizing
    * `preferredLayoutAttributes:` on cell subclasses if you still need set height/width
* Built on top of compositional layout.
* Return different layout configuration for each section using `NSCollectionLayoutSection`.
* `firstItemInSection` can be set by config so first item is the header (data must be aware because now first item is header)
* Swipe actions are now a feature of the cell (in a list cell)
* Separators - separator layout guide to change where separator is positioned (aligned with text, for instance)
* New accessory types, both for trailing and leading
    * Reorder accessory view automatically sets up collection view to reorder.
    * Outline disclosure to automatically create outline view (using new section snapshot APIs).