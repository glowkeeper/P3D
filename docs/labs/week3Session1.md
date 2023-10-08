# Lab - Week 3, Session 1 - Lighting

The lab focuses on:

- Lighting a scene through volumes

![Fe](./images/fe.png)

_[Fe](https://www.ea.com/games/fe)_

## Overview

Unity comes with a range of lighting techniques whose aim is to approximate the reality of light's behaviour. The result is that Unity can generate photo-realistic graphics, or, as something much more stylised, such as the beautiful _Fe_, shown above.

### Direct and Indirect Lighting

Unity models direct and indirect light - to get realistic effects, you must combine both. Direct light is emitted from a source, hits a surface, and gets reflected directly into a sensor (such as a virtual camera). Indirect light is all other light; it includes ambient environmental light that comes from the sky that may have been reflected many times from different surfaces before it reaches a sensor (for more technical information on this subject, please see [3D Graphics](../graphicsBackground.md)

### Realtime and Baked Lighting

Unity uses Realtime Global Illumination (GI) and Baked GI systems to model direct and indirect light. Baked lighting is light data that is computed in advance and gets _applied_ at runtime. Realtime light data is calculated on the fly. Ultimately, the difference is a trade-off between runtime performance (realtime lighting) and the time it takes to render your 3D graphics beforehand (baked lighting).

## Volumes

Volumes allow you to create different effects on the scene cameras - these could be post-processing effects (think of post-processing as something that happens _after_ everything else has been rendered), shadows, clouds, fog, lighting and many more. Volumes can be _Global_, whose settings are applied to all the scene cameras, no matter where they are, or _Local_, whose settings are applied only to those cameras that are within the local zone of influence.
