# Week 3, Session 2 - Lighting

The goal of this session is to add lights to your scene.

![Fe](./images/fe.png)

_[Fe](https://www.ea.com/games/fe)_

## Unity Lighting

Unity comes with various lighting techniques that approximate light's physics in the real world. The result is that Unity can generate photo-realistic graphics or something much more stylised, such as the beautiful _Fe_, shown above.

### Direct and Indirect Lighting

Unity models direct and indirect light - to get realistic effects, you must combine both. Direct light is emitted from a source, hits a surface, and gets reflected directly into a sensor (such as a virtual camera). Indirect light is all other light; it includes ambient environmental light that comes from the sky that may have been reflected many times from different surfaces before it reaches a sensor (for more technical information on this subject, please see [3D Graphics](../graphicsBackground.md)).

## Ambient Occlusion

You've already been introduced to ambient occlusion maps, which are textures that add extra shadow details to models. You can also apply ambient occlusion while lighting, enabling you to simulate the soft shadows on nearby surfaces. These surfaces occlude (block out) ambient light, so they appear darker.

### Realtime and Baked Lighting

Unity uses [realtime global illumination](https://docs.unity3d.com/Manual/realtime-gi-using-enlighten.html) and [baked lighting](https://docs.unity3d.com/Manual/LightMode-Baked.html) to model direct and indirect light. Baked lighting is light data that is computed in advance and applied_ at runtime. Realtime light data is calculated on the fly. Ultimately, the difference is a trade-off between runtime performance (realtime lighting) and the time it takes to render your 3D graphics beforehand (baked lighting). Because the complex calculations are performed in advance, baked lights reduce the rendering cost of shadows, so they help light static objects, which won't change position at runtime.

However, be careful turning on baked lighting until you get near to releasing your game. The operation is computationally expensive, and depending on your graphics card (and/or CPU), the baking process might take many hours and slow down your development. Also, if you bake some lighting but subsequently move some static objects, you might get some weird-looking results.

## Types of Lights

Unity has different types of light components that you can apply to GameObjects:

- Point Light: A light that's located at a point in the scene and emits light in all directions equally, making them useful for simulating lamps and other local sources of light
- Spot Light: A light that's located at a point in the scene and emits light in a cone shape, making them useful for artificial light sources such as flashlights, car headlights and torches 
- Directional Light: A light that's located infinitely far away and emits light in one direction only, making them useful for representing large, distant sources of light, such as the sun or the moon
- Area Light: A light that's defined by a rectangle or disc and emits light in all directions uniformly across its surface area but only from one side of the rectangle or disc, making them useful for creating a realistic street light

## Volumes

Volumes allow you to create different effects on the scene cameras - these could be post-processing effects (think of post-processing as something that happens _after_ everything else has been rendered), shadows, clouds, fog, lighting and many more. Volumes can be _Global_, whose settings are applied to all the scene cameras, no matter where they are, or _Local_, whose settings are applied only to the cameras within the local zone of influence.

## Exercise

Add lighting to your scene! You could play around with a directional light so that your building's shadows appear cast by moonlight or brightly lit by a sun that's directly overhead.

## Links

- [Unity Lighting](https://docs.unity3d.com/Manual/Lighting.html)
- [Graphics in Unity](https://docs.unity3d.com/Manual/Graphics.html)
- [3D Graphics](../graphicsBackground.md)
- [Realtime Global Illumination (GI)](https://docs.unity3d.com/Manual/realtime-gi-using-enlighten.html)
- [Baked Lighting](https://docs.unity3d.com/Manual/LightMode-Baked.html)
- [Volumes](https://docs.unity3d.com/Packages/com.unity.render-pipelines.high-definition@10.6/manual/Volumes.html)
- [Ambient Occlusion](https://docs.unity3d.com/Manual/LightingBakedAmbientOcclusion.html)
