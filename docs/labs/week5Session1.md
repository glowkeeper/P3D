# Lab for Week 5, Session 1 - Particle Systems Using Visual Effects Graphs

This lab serves as an introduction to Unity [Visual Effects Graphs](https://unity.com/visual-effect-graph).

## Overview

You can create many exciting effects using Unity's visual effect (VFX) graphs. In this lab, we are going to build a smoky fire.

## Fire

First, in the _Projects_ window, _Create_, _Visual Effects_, _Visual Effects Graph_, and name it _Smoke_. In the _Hierarchy_ window, _Create Empty_, and call that _Fire_. Now drag your _Smoke_ VFX graph into that.  

## 3D Spatial Sound

Below, you will add a simple attenuated 3D sound to the fire so that its volume increases and decreases as your FPC gets closer or moves further away.

### Adding Some Sound to the Fire

You will need the audio that makes the fire crackle and pop. Go to the [P3D GitHub repository](https://github.com/glowkeeper/P3D), where you will find a _wav_ with _fire-in-the-stove_ in the title. Add that _wav_ to your _assets/audio_ (you may need to create that, if you did not do so in an earlier lab).

No add an _AudioSource_ to the fire and drag the _wav_ into its _AudioClip_ field in the inspector. Ensure it is set to _Play on Awake_ and _Loop_. Press _Play_. You should hear the fire begin to crackle and pop.

Similarly for the radio in the previous lab, no matter the FPC's distance from the fire, the sound will maintain the same volume. To change that, in the fire's _AudioSource_, set the _Spatial Blend_ field to _1_ - that enables the _AudioClip_ to take on 3D properties. Now, in the _3D Sound Settings_, set the Max Distance to 10, and at the 10 point on the x-axis of the graph, ensure the sound volume is set to zero. Now, when you approach and walk away from the fire, the volume should increase and decrease. Experiment with the 3D settings to see their effect.  

## Useful Links

+ [Visual Effects Graphs](https://unity.com/visual-effect-graph)
+ [freesound](https://freesound.org/)