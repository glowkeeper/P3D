# Lab for Week 3, Session 1 - Graphics in Unity - Lighting

This lab introduces you to graphics and lighting in [Unity](https://unity.com/).

## Overview

Unity comes with a range of lighting techniques whose aim is to approximate the reality of light's behaviour. The result is that Unity can generate photo-realistic graphics, or, as in Figure 1, something much more stylised.

![](./images/fe.png)

_Figure 1: [Fe](https://www.ea.com/games/fe)_

Unity models direct and indirect light - to get realistic effects, you must combine both. Direct light is emitted from a source, hits a surface, and gets reflected directly into a sensor, such as a virtual camera. Indirect light is all other light. That includes ambient environmental light that comes from the sky, which may have been reflected many times from different surfaces before it reaches a sensor.

Unity uses a global illumination (GI) system that is supported by two separate systems, 1) Realtime GI and 2) Baked GI. Realtime lighting is calculated at runtime. Baked lighting is light data that is computed in advance and gets _applied_ at runtime (rather than calculated). Ultimately, the difference is a trade-off between runtime performance (realtime lighting) and the time it takes to render your 3D graphics beforehand (baked lighting).

All of Unity's render pipelines support Baked GI. Realtime lighting is available in Unity's legacy systems, and will soon be removed entirely.

## Lighting a Simple Scene

Below, you will create a simple scene that introduces some of the lighting capabilities of Unity.

### A Simple Room

Open [Unity Hub](https://docs.unity3d.com/Manual/GettingStartedUnityHub.html), create a new project, and choose the Universal Render Pipeline (URP) template (naming the project however you choose).

The loaded URP sample scene is an opportunity to play with Unity's lighting systems. Figure 2 shows the rotational tool being used to change the direction of lighting and change how it effects the workshop's shadows.

![](./images/sampleScene.png)

_Figure 2: Lighting the sample scene_

However, you are not going to use the sample scene, instead you are going to create your own, so click on _File_, _New Scene_. This is intended to be a room with no windows, so first, go to _Window_, _Rendering_, _Lighting Settings_, set _Skybox Material_ to _None_. Also, set _Lighting Mode_ to _Baked Indirect_ and turn on _Auto Generate_. At this point, you may also wish to set the Main Camera's _Background Type_ to a _Solid Colour_ and turn it black, so your room stands out in the Game tab.

Now use five copies of _GameObject_, _3D Object_, _Plane_, which you should transform to create a simple room similar to that shown in Figure 3. Also, create an empty _GameObject_, move the five planes into that and make it _static_ so Unity can precompute some of the lighting you are going to create.

![](./images/simpleRoom.png)

_Figure 3: A simple room_

This is a good time to save your newly created scene and project.

You are now going to light up your scene by adding a _Point Light_ - go to _GameObject_, _Light_, _Point Light_. Move it on the _z_ axis, so it sits in the centre of your room, then move it again, so it lights up the back wall and ceiling. Play around with the settings until you find a colour and intensity that you like. Additionally, this is intended to be an unlit inside scene, so delete the _Directional Light_ as you do not require any outside ambient light casting shadows in the scene. Figure 4 shows the Game tab with the _Point Light_ added.

![](./images/simpleRoomLit.png)

_Figure 4: A simple room with added materials_

Save your scene and save your project. You will add to this in the next lab.

## Reading Material

+ [Lighting](https://docs.unity3d.com/Manual/LightingOverview.html)
+ [Tutorial - Introduction to Lighting and Rendering](https://learn.unity.com/tutorial/introduction-to-lighting-and-rendering-2019-3)
+ [Types of Light](https://docs.unity3d.com/Manual/Lighting.html)
