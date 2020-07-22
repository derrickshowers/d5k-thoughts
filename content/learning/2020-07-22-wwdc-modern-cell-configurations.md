---
title: "WWDC 2020: Modern Cell Configurations"
date: 2020-07-22T14:00:00-00:00
slug: wwdc-2020-modern-cell-configurations
link: https://developer.apple.com/wwdc20/10027
subjects: ["ios", "wwdc", "wwdc-2020"]
---

* In iOS 14, collections are split into three main areas: Data (diffable data source), layout (collection view layout), presentation (configurations and configuration states, this session!)
* Configurations
    * `defaultContentConiguration` always returns a fresh configuration.
        * Configurations are lightweight (value types).
        * Default configuration means you don’t have to deal with the old state!
        * Default styling based on cell and context (table view/collection view).
        * Properties are not specific to views (text/image vs label/imageVIew) - configurations can now be used on any view that supports them.
    * Set configuration with `contentConfiguration` property.
    * Background configuration for bg color, visual effect, stroke, insets, custom view.
    * Content configuration for content, e.g. image, text, secondary text, layout metrics and behaviors.
* Configuration states
    * Traits (size class, content size category, layout direction, misc states, custom states)
    * Custom state is like having a view model for each cell
    * Each cell, header, footer has its own configuration state.
    * Different class for cells and views - cell configuration state adds things like editing, swipeable, etc.)
    * `configuration.updated(for: state)` to update the state (original configuration with new state)
    * Disable automatic updates to manually update configurations (in addition to state)
    * Override `updateConfiguration:` to update configurations and any other cell properties before displayed (gives you the state so you can update cell based on current state properties)
* Color Transformer - function that returns a modified output color for an input color.
* Default configurations available for list cells, sidebar cells, etc.
* Configurations work with custom views, too. Use as an object to hold default values since object is so light.