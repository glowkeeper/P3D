# Week 3, Session 2 - Lighting

The goal of this session is to add lights to your scene.

![Fe](./images/fe.png)

_[Fe](https://www.ea.com/games/fe)_

## Unity Lighting

Unity comes with various lighting techniques that approximate light's physics in the real world. The result is that Unity can generate photo-realistic graphics or something much more stylised, such as the beautiful _Fe_, shown above.

### Direct and Indirect Lighting

Unity models direct and indirect light - to get realistic effects, you must combine both. Direct light is emitted from a source, hits a surface, and gets reflected directly into a sensor (such as a virtual camera). Indirect light is all other light; it includes ambient environmental light that comes from the sky that may have been reflected many times from different surfaces before it reaches a sensor (for more technical information on this subject, please see [3D Graphics](../graphicsBackground.md)).

### Ambient Occlusion

You've already been introduced to ambient occlusion maps, which are textures that add extra shadow details to models. You can also apply ambient occlusion while lighting, enabling you to simulate the soft shadows on nearby surfaces. These surfaces occlude (block out) ambient light, so they appear darker.

## Computing Light

Unity uses [realtime global illumination](https://docs.unity3d.com/Manual/realtime-gi-using-enlighten.html) and [baked lighting](https://docs.unity3d.com/Manual/LightMode-Baked.html) to model direct and indirect light.

### Realtime and Baked Lighting

Baked lighting is light data that is computed in advance and _applied_ at runtime. Realtime light data is calculated on during game play. Ultimately, the difference is a trade-off between runtime performance (realtime lighting) and the time it takes to render your 3D graphics beforehand (baked lighting). Because the complex calculations are performed in advance, baked lights reduce the rendering cost of shadows, so they help light static objects, which won't change position at runtime.

However, be careful turning on baked lighting until you get near to releasing your game. The baking operation is computationally expensive, and depending on your graphics card (and/or CPU), the baking process might take many hours and slow down your development. Also, if you bake some lighting but subsequently move some static objects, you might get some weird-looking results.

### Lighting Modes

The Lighting Mode determines the behavior of any scene lighting that uses the [Lighting Settings Asset](https://docs.unity3d.com/Manual/class-LightingSettings.html). The available modes are:

- _Shadowmask_ combines real-time direct lighting with baked indirect lighting. It supports baked shadows for distant GameObjects (with Shadow masks) and blends them automatically with real-time shadows (Shadow maps). _Shadowmask_ is the most realistic. It is the most resource-intensive mode.
 _Baked Indirect_ combines real-time direct lighting with baked indirect lighting. This mode provides real-time shadowing and offers realistic lighting and reasonable shadow fidelity
- _Subtractive_ provides baked direct and indirect lighting. It renders direct real-time shadows for one Directional Light only. The results aren't particularly realistic, but that might be the styling you're after! It is the most performant

### Light Mapping

Lightmapping is the process of pre-calculating the brightness of an object's surface and storing the result in a texture called a _lightmap_. Lightmaps can include both direct and indirect light, and the shader of an object's material can combine them with other surface maps, such as albedo (colour) and normals (perpendicular rays).

## Types of Lights

Unity has different types of light components that you can apply to GameObjects:

- Point Light: A light that's located at a point in the scene and emits light in all directions equally, making them useful for simulating lamps and other local sources of light
- Spot Light: A light that's located at a point in the scene and emits light in a cone shape, making them useful for artificial light sources such as flashlights, car headlights and torches 
- Directional Light: A light that's located infinitely far away and emits light in one direction only, making them useful for representing large, distant sources of light, such as the sun or the moon
- Area Light: A light that's defined by a rectangle or disc and emits light in all directions uniformly across its surface area but only from one side of the rectangle or disc, making them useful for creating a realistic street light

## Volumes

Volumes allow you to create different effects on the scene cameras - these could be post-processing effects (think of post-processing as something that happens _after_ everything else has been rendered), shadows, clouds, fog, lighting and many more. Volumes can be _Global_, whose settings are applied to all the scene cameras, no matter where they are, or _Local_, whose settings are applied only to the cameras within the local zone of influence.

## Exercise

Add lighting to your scene! You could add some global volumes that affect the lighting of your whole scene, and play around with a directional light so that your building's shadows appear cast by moonlight or brightly lit by a sun that's directly overhead. Also, add local volumes to create different effects in different parts of your scenes.

## Links

- [Unity Lighting](https://docs.unity3d.com/Manual/Lighting.html)
- [Choose a Lighting Setup](https://docs.unity3d.com/Manual/choose-a-lighting-setup.html)
- [Creative Core Lighting](https://learn.unity.com/project/creative-core-lighting)
- [Graphics in Unity](https://docs.unity3d.com/Manual/Graphics.html)
- [Realtime Global Illumination (GI)](https://docs.unity3d.com/Manual/realtime-gi-using-enlighten.html)
- [Baked Lighting](https://docs.unity3d.com/Manual/LightMode-Baked.html)
- [Volumes](https://docs.unity3d.com/Packages/com.unity.render-pipelines.high-definition@10.6/manual/Volumes.html)
- [Ambient Occlusion](https://docs.unity3d.com/Manual/LightingBakedAmbientOcclusion.html)
- [3D Graphics](../graphicsBackground.md)