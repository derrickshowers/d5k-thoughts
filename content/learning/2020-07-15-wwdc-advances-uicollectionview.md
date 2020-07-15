---
title: "WWDC 2020: Advances in UICollectionView"
date: 2020-07-15T15:00:00-00:00
slug: wwdc-2020-advances-uicollectionview
type: short-post
link: https://developer.apple.com/wwdc20/10097
subjects: ["ios", "wwdc"]
---

Good overview of all the new stuff for UICollectionView this year. New stuff for diffable data source, lists (collection view looks like a table view!), and cell configurations.

* Since the beginning, collection view APIs have separated concerns:
    * Data - `UICollectionViewDataSource`
    * Layout - `UICollectionViewLayout`
    * Presentation - cell, reusable cells
* New last year
    * Data - diffable data source
    * Layout - Compositional layout
* New _this_ year
    * Data - section snapshots
    * Layout - list configuration
    * Presentation - list cell, view configuration
* Overview of the new stuff this year:
    * Section snapshots - encapsulate the data for a single section in a UICollectionView
        * More composable into section size chunks of data.
        * Modeling of hierarchical data.
    * Lists
        * UITableView like appearance
        * Swipe actions, cell layouts
    * Cell registrations are a new API to configure cells (no need for reuse identifier)
    * Cell content configurations to easily get a default configuration (value cell, subtitle cell, etc.)