---
title: "WWDC 2019: Building AR Experiences with Reality Composer"
date: 2020-05-01T10:00:00-00:00
slug: wwdc-reality-composer
type: short-post
link: https://developer.apple.com/videos/play/wwdc2019/609/
subjects: ["ios", "swift", "wwdc", "wwdc-2019"]
---

* Anatomy of Reality Composer project: scene -> anchors, objects, behaviors.
* Anchors. 4 options: horizontal plane, vertical plane, face, image.
* Objects
    * Library of objects from Apple, including basic shapes.
    * Custom objects can be imported via `.usdz` file format (more info on Usdz [here](https://developer.apple.com/augmented-reality/quick-look/))
    * 12:00 building the solar system with objects.
* Behaviors comprised of trigger and action sequence.
* Triggers
    * Start as soon as scene is loaded)
    * User tap
    * Camera/user proximity
    * Collision (when 2 objects collide)
    * Notification (begin programatically from app)
* Actions are grouped into sequences, allowing for loops, exclusive sequences (stop other exclusive sequences), running one after the other, or all at the same time.
    * Visibility - fade in/out, scale up/down
    * Animation in place - emphasis, spin, orbit, or Usdz animation.
    * Move - move by x number of spaces x direction (think knight chess piece), move to certain spot.
    * Look at - always face camera.
    * Audio actions (play sound, play ambient, play music)
* Physics
    * Materials - choose a material to determine how object will interact with surfaces and others.
    * Forces - choose a force (like velocity) and configure gravity
    * Collisions (how objects interact with one another). Options are in the forms of shapes - box, sphere, capsule.
* Xcode integration
    * Reality Composer project can be imported in Xcode, creates reality file on build.
    * Reality File is what gets generated and included in the app bundle. ~37:00 goes into the anatomy of the file. It can also be shared to be used in quick look on iOS
    * Codegen creates a swift file for using reality file as a strongly typed object.
* Demos - around ~45:00 is when the demo on how to integrate into Xcode begins.
    * Two lines of code to load a scene (get the scene, add it to view)
    * Notify action to notify app code
    * Notification trigger to notify reality composer