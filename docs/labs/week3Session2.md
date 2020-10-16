# Lab for Week 3, Session 2 - Graphics in Unity - Meshes, Materials, Shaders and Textures  

This lab introduces you to graphics and meshes, materials, shaders and textures in [Unity](https://unity.com/).

## Overview

Rendering in Unity relies on a close relationship between meshes, materials, shaders and textures; textures are applied to objects using materials, and materials use specialised graphics programs called shaders to render a texture onto the surface of a mesh.

+ [Meshes](https://docs.unity3d.com/Manual/AnatomyofaMesh.html) are a graphics primitive that define the shape of an object.
+ Materials define the properties of a surface of an object. They include references to textures and specifiy how those textures are tiled and coloured.
+ Shaders are small scripts that contain the algorithms for calculating the colour of each pixel.
+ [Textures](https://docs.unity3d.com/Manual/Textures.html) are [bitmap](https://en.wikipedia.org/wiki/Bitmap) images that define the fine detail of a material's surface; think of them as images that are printed on a rubber sheet and stretched and pinned onto a mesh.

Each material specifies which shader to use, and that determines the options available. The shader expects one or more texture variables, each of which can be assigned different texture assets. Unity's [standard shader](https://docs.unity3d.com/Manual/shader-StandardShader.html) is often the best choice as it is highly customisable and capable of rendering many types of surface. However, there may be occasions where a [custom written shader](https://docs.unity3d.com/Manual/ShadersOverview.html) may be appropriate; examples could be if you are creating liquids or some highly-specialised artistic special effects.

## Adding Materials

Below, you will add some character to the simple room created during the [last lab](./week3Session1.md) by adding some materials and textures to the walls. You will also add a lamp to the scene.

### Adding to the Simple Room

Open [Unity Hub](https://docs.unity3d.com/Manual/GettingStartedUnityHub.html) and open the project you created in the [last lab](./week3Session1.md).

You will need some more assets, so go to the [unity asset store](https://assetstore.unity.com/), and add [Free Shipping Containers](https://assetstore.unity.com/packages/3d/environments/industrial/free-shipping-containers-18315) and [Old USSR Lamp](https://assetstore.unity.com/packages/3d/props/electronics/old-ussr-lamp-110400).  Now download and import them into your project. Before you can use the imported assets, you must update them to use URP; so go to _Edit_, _Render Pipeline_, _Universal Render Pipeline_, _Upgrade Project Materials ..._.

You are going to add the _containers_diffuse_ material to the walls of the room. Select that in _All Materials_ in the _Project_ tab, and drag it onto each of the surfaces of your room. Then, in the _Inspector_ window, set the _Base Map_ of the _Surface Inputs_ to the texture _containers_normals_. Figure 1, below, shows how your results might look.

![](./images/shippingContainer.png)

_Figure 1: Adding materials and textures to the walls of the simple room_

Next, you are going to add a box, which will become a lampstand. Create a _GameObject_, _3D Object_, _Cube_ and add the same _containers_diffuse_ material to it as you did the walls, above. Rename it _Stand_. Figure 2 shows the box scaled to 2.5 times its original size across all three axes and moved to the back lefthand corner of the room.

![](./images/shippingContainerBox.png)

_Figure 2: Room with a Box_

You are going to put a lamp on the stand. Find the _Old_USSR_Lamp_ in _All Prefabs_, and add it to the room in your scene. Scale it to 8 times its original size across all three axes and move it onto the stand. Rotate it sixty degrees on the y-axis, so it is pointing towards the bottom front right-hand corner.

Next, you are going to make that lamp shine by adding a _sphere_ that emits colour. Create a _GameObject_, _3D Object_, _Sphere_, rename it _bulb_ then move it, so it is in front of the light bulb of the lamp. Scale it, so it covers the bulb as precisely as possible. Now create a new material, rename it _Bulb_, and add it to the sphere. Set the colour of the _Base Map_ and enable _Emission_ on the material. Set that to a colour of your choosing.

Now _Add Component_ to the _Main Camera_, search for the _Volume_ script and add that. Add a _New_ profile to the volume, and as prompted, _Add Override_, _Post processing_, _Bloom_. Change the settings of the bloom until your lamp is shining as you wish. The bloom will affect your ceiling light, too, so you may want to tone down the intensity of that. The effect should be similar to Figure 3.

![](./images/lampWithBloom.png)

_Figure 3: Lamp with Bloom_

Create another  _GameObject_, _Light_, _Point Light_ that you will use to make sure the bulb is shining within the old USSR lamp. So move it until it looks as though the old USSR lamp is emitting more light and play around with the settings until you find a colour and intensity that you like.

Finally, add a [_Reflection Probe_](https://docs.unity3d.com/Manual/class-ReflectionProbe.html) and transform it so it matches the size and shape of your room; it will subtly affect the reflective materials in the room so they look more natural.

Your lamp should look similar to that shown in Figure 4.

![](./images/lampWithLight.png)

_Figure 4: Lamp with a Point Light_

Save your scene and save your project. You will add to this in the lab.

## Useful Links

+ [Meshes, Materials, Shaders and Textures](https://docs.unity3d.com/Manual/Shaders.html)
+ [Anatomy of a Mesh](https://docs.unity3d.com/Manual/AnatomyofaMesh.html)
+ [Textures](https://docs.unity3d.com/Manual/Textures.html)
+ [Shader](https://en.wikipedia.org/wiki/Shader)
