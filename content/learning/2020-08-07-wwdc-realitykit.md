---
title: "WWDC 2020: What’s New in RealityKit"
date: 2020-08-07T07:00:00-00:00
slug: wwdc-2020-reality-kit
link: https://developer.apple.com/wwdc20/10612
subjects: ["ios", "wwdc", "wwdc-2020"]
---

1. Video materials
    * Glow effect
    * Instructional videos (map video to a plane)
    * Video play spatialized audio (acts as if the sound source is from a specific location)
    * Uses `AVFoundation`/`AVPLayer` passed as a material.
2. Scene understanding using LiDAR
    * Occlusion (hides behind real world objects)
    * Receives lighting (add shadows on real world surfaces)
    * Physics
    * Collision
    * Summary of scene understanding:
        * Goal: make content interact with real world.
        * Occlusion and shadows improve realism.
        * Physica and collision against real world meshes.
        * Scene understanding entity created and managed by RealityKit.
3. Improved rendering debugging
4. Face tracking (ARKit 4)
5. Location anchors (ARKit 4)