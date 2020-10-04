# Lab for Week 3, Session 2 - Graphics in Unity - Meshes, Materials, Shaders and Textures  

This lab introduces you to graphics and meshes, materials, shaders and textures in [Unity](https://unity.com/).

## Overview

Meshes, Materials, Shaders and Textures

## Adding Materials

Below, you will add character to the simple room created  the [last lab](./week3Session1.md) by adding some materials to the walls. You will also add a lamp to the scene.

### Embelishing the Simple Room

Open [Unity Hub](https://docs.unity3d.com/Manual/GettingStartedUnityHub.html) and open the project you created in the [last lab](./week3Session1.md).

You will need some more assets, so go to the [unity asset store](https://assetstore.unity.com/), and add [Free Shipping Containers](https://assetstore.unity.com/packages/3d/environments/industrial/free-shipping-containers-18315), [Old USSR Lamp](https://assetstore.unity.com/packages/3d/props/electronics/old-ussr-lamp-110400), as well as Unity's [Standard Assets](https://assetstore.unity.com/packages/essentials/asset-packs/standard-assets-for-unity-2018-4-32351).  Now download and import them into your project. Before you can use the imported assets, you must update them to use URP; so go to _Edit_, _Render Pipeline_, _Universal Render Pipeline_, _Upgrade Project Materials ..._.

You are going to add the _containers_diffuse_ material to the walls of the room. Select that in _All Materials_ in the _Project_ tab, and in the _Inspector_ window, set the _Base Map_ of the _Surface Inputs_ to _containers_normals_. Figure 1, below, shows how your results might look.

![](./images/shippingContainer.png)

_Figure 1: Adding materials to the walls of the simple room_

Next, you are going to add a box, which will become a lamp stand. Go to _All Prefabs_ in the _Project_ tab, find a _Box_, and add it to the room in your scene. Rename it _Stand_. Figure 2 shows the box scaled to 1.5 times its original size across all three axis, moved to the back lefthand corner of the room, and given the same material as the walls.

![](./images/shippingContainerBox.png)

_Figure 2: Room with a Box_

You are going to put a lamp on the stand. Find the _Old_USSR_Lamp_ in _All Prefabs_, and add it to the room in your scene. Scale the lamp to 8 times its original size across all three axis and move it onto the stand. Rotate it sixty degrees on the y axis so it is pointing towards the bottom front righthand corner.

Next, you are going to make that lamp shine by adding a _sphere_ that emits colour. Create a _GameObject_, _3D Object_, _Sphere_, rename it _bulb_ then move it so it is in front of the light bulb of the lamp. Scale it so it covers the bulb as exactly as possible. Now create a new material, rename it _Bulb_, and add it to the sphere. Set the colour of the _Base Map_ and enable _Emission_ on the material. Set that to a colour of your choosing.

Now _Add Component_ to the _Main Camera_, search for the _Volume_ script, and add that. Add a _New_ profile to the volume, and as prompted, _Add Override_, _Post processing_, _Bloom_. Change the settings of the bloom until your lamp is shining as you wish. The bloom will affect your ceiling light, too, so you may wish to tone down the intensity of that. The effect should be similar to Figure 3.

![](./images/lampWithBloom.png)

_Figure 3: Lamp with Bloom_

Finally, create another  _GameObject_, _Light_, _Point Light_ that you wil use to make sure the bulb is shining within the old USSR lamp. So move it until it looks as though the old USSR lamp is emitting more light and play around with the settings until you find a colour and intensity that you like. Your lamp should look similar to that shown in Figure 4.

![](./images/lampWithLight.png)

_Figure 4: Lamp with a Point Light_

Save your scene and save your project. You will add to this in the lab.

## Useful Links

+ [Shader](https://en.wikipedia.org/wiki/Shader)
