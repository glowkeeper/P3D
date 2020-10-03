# Lab for Week 3, Session 1 - Graphics in Unity - Lighting

This lab introduces you to graphics and lighting in [Unity](https://unity.com/).

## Overview

Unity comes with a range of lighting techniques whose aim is to approximate the reality of light's behaviour. The result is that Unity can generate photo-realistic graphics, or, as in Figure 1, something much more stylised.

![](./images/fe.png)

_Figure 1: [Fe](https://www.ea.com/games/fe)_

Unity models direct and indirect light - to get realistic effects, you must combine both. Direct light is emitted from a source, hits a surface, and gets reflected directly into a sensor, such as a virtual camera. Indirect light is all other light. That includes ambient environmental light that comes from the sky, which may have been reflected many times from different surfaces before it reaches a sensor.

Unity uses a global illumination (GI) system that is supported by two separate systems, 1) Realtime GI and 2) Baked GI. Realtime lighting is calculated at runtime. Baked lighting is light data that is computed in advance and gets _applied_ at runtime (rather than calculated). Ultimately, the difference is a trade-off between runtime performance (realtime lighting) and the time it takes to render your 3D graphics beforehand (baked lighting).

All of Unity's render pipelines support Baked GI. Realtime lighting is available in Unity's legacy systems, and will soon be removed from the platform entirely.

## Lighting a Simple Scene

Below, you will create a simple scene that introduces some of the lighting capabilities of Unity.

### A Simple Room

Open [Unity Hub](https://docs.unity3d.com/Manual/GettingStartedUnityHub.html), create a new project, and choose the Universal Render Pipeline (URP) template (naming the project however you choose). T

The loaded URP sample scene is your first opportunity to play with Unity's lighting systems. Figure 2 shows the rotational tool being used to change the direction of lighting effecting how shadows fall across the workshop.

![](./images/sampleScene.png)

_Figure 2: Lighting the sample scene_

However, you are not going to use the sample scene, instead you are going to create your own, so click on _File_, _New Scene_. Now use five copies of _GameObject_, _3D Object_, _Plane_, which you should transform to create a simple room similar to that shown in _Figure 3.

![](./images/simpleRoom.png)

_Figure 3: A simple room_

Delete the _Directional Light_ - this is intended to be an unlit inside scene, so it does not require any ambient light from outside casting shadows. Unfortunately, you will now have a black box, so to to distinguish the walls, you should colour them. 



## Reading Material

+ [Lighting](https://docs.unity3d.com/Manual/LightingOverview.html)
+ [Introduction to Lighting and Rendering](https://learn.unity.com/tutorial/introduction-to-lighting-and-rendering-2019-3)
+ [Types of Lighting](https://learn.unity.com/tutorial/introduction-to-lighting-and-rendering-2019-3)
+ [LIGHTING in Unity](https://www.youtube.com/watch?v=VnG2gOKV9dw)
