# Lab for Week 3, Session 1 - ProBuilder and First-Person Controllers

This lab uses Unity's [ProBuilder](https://unity3d.com/unity/features/worldbuilding/probuilder) to recreate (and improve) the simple room created in the [first Unity lab](./week3Session1.md). It also introduces a first-person [character controller](https://docs.unity3d.com/Manual/class-CharacterController.html).

## Overview

[ProBuilder](https://unity3d.com/unity/features/worldbuilding/probuilder) allows you to build, edit, and texture custom geometry, so that you can prototype and create an in-scene level design. ProBuilder also features a [Scripting API](https://docs.unity3d.com/Packages/com.unity.probuilder@4.2/manual/api.html), which means you can create customised tools via C# scripts (which are going to be introduced in the [next lab](week5Session1.md)).

A [first-person](https://en.wikipedia.org/wiki/First-person_(video_games)) controller shows the graphical perspective of the player. The roots of first-person games go back to the 1970s, with the release of [Spasim](https://en.wikipedia.org/wiki/Spasim) and [Maze War](https://en.wikipedia.org/wiki/Maze_War), and nowadays, there are many genres of game that give first-person perspectives; racing games and [flight simulators](https://en.wikipedia.org/wiki/Amateur_flight_simulation#Flight_simulators) are two notable examples.  However, it is the first-person shooters, popularised by games such as [Doom](https://en.wikipedia.org/wiki/Doom_(franchise)) and [Call of Duty](https://en.wikipedia.org/wiki/Call_of_Duty), for which the first-person perspective is perhaps best known.

## Recreating the Simple Room

Below, you will recreate the simple room you first built in [Week 1, Session 2](./week1Session2.md), but this time using ProBuilder. You will also add other features, such as stairs and an outside scene that a first-person controller can explore.

### ProBuilder

Open [Unity Hub](https://docs.unity3d.com/Manual/GettingStartedUnityHub.html), create a new project and choose the High Definition Render Pipeline (HDRP) template (naming the project however you choose).

Create a new scene by selecting _File_, _New Scene_. You can use similar lighting settings to those used in [Week 1, Session 2](./week1Session2.md), but leave the default _Skybox Material_ (since this will be an outdoor scene, too). Additionally, do not worry too much about the settings of the main camera - later, we are going to use a first-person controller that employs a camera that tracks the main camera, and most of the settings we can change there, instead.

You will need some of the assets you have already added to your [asset store](https://assetstore.unity.com/): [Starter Assets - First Person Character Controller](https://assetstore.unity.com/packages/essentials/starter-assets-first-person-character-controller-196525), [Free Shipping Containers](https://assetstore.unity.com/packages/3d/environments/industrial/free-shipping-containers-18315), [Old USSR Lamp](https://assetstore.unity.com/packages/3d/props/electronics/old-ussr-lamp-110400) and [Free PBR Lamps](https://assetstore.unity.com/packages/3d/props/interior/free-pbr-lamps-70181) so download and import those into your project.

While you're in the _Package Manager_, load the _Unity Registry_, search for _ProBuilder_ and install it. Now go to _Tools_, _ProBuilder_ and select _ProBuilder_ window. You have several options for displaying the ProBuilder tools window - play around and find whichever option suits you best.

Before you can use the imported assets, ensure they can use the High Definition Render Pipeline; so go to _Edit_, _Render Pipeline_, _HD Render Pipeline_, _Upgrade from Builtin Pipeline_, _Upgrade Project Materials..._.

To enable ProBuilder, go to _Window_, _Package Manager_. Search for _ProBuilder_ and install it. Now go to _Tools_, _ProBuilder_ and select _ProBuilder_ window. You have several options for displaying the ProBuilder tools window - play around and find whichever option suits you best.

This time, you are going to create something that looks a little more like a shipping container, so make a _New Shape_ from the ProBuilder window. Select a _Cube_, set the _x_, _y_ and _z_ coordinates to be 3, 3 and 6, respectively (making the cube three metres by three metres by six metres) and hit _Build_. Later on, you are going to put a door on the container, so select the _Face Selection_, highlight the front face of the object, and press _backspace_. Rename the cube _Inside_ (this will be the inside of the container), and with the object highlighted, select _Flip Normals_. Next, you are going to apply a container material, so again, with the container object highlighted, select ProBuilder's _Material Editor_, add _containers_diffuse_ to _Quick Material_ and _Apply_. Then open up the shader in the _Inspector_ window and set the _Base Map_ of the _Surface Inputs_ to the texture _containers_normals_. Finally, create an empty _GameObject_, name it _Container_ and make _Inside_ a child of that.

If your _Game_ tab looks something similar to Figure 1, then congratulations, you have successfully created your first ProBuilder object.

![](./images/shippingContainerProBuilder.png)

_Figure 1: A Shipping Container Using ProBuilder_

You are going to create the ground upon which the container sits. You could follow a similar process above, and use a ProBuilder cube for that - the advantage would be that you would be able to model the ground in complex ways. Alternatively, you might even create a _GameObject_, _3D Object_, _Terrain_, and put your container on a [grassy field](https://docs.unity3d.com/Manual/terrain-Grass.html). However, those options are left as an exercise. For now, create a _GameObject_, _3D Object_, _Plane_. Set its _x_ and _z_ coordinates to 100 and position the plane, so it sits underneath the container and envelopes it equally on all sides. Rename it to _Ground_. At this point, you could apply whichever material and texture you wish.

Save your scene.

You are now going to add a first-person controller to the scene. The simplest method to do that is via _Tools_, _Starter Assets_, _Reset First Person Controller_.  Hopefully, your scene looks similar to Figure 2. Now, when you press _play_, you should be able to look and move around your scene using the mouse and the arrow keys (or _w_, _a_, _s_, _d_) and _spacebar_.

![](./images/fpcScene.png)

_Figure 2: Scene with First Person Controller_

If you walk around the outside of your container, you will notice the walls are transparent due to [culling](https://docs.unity3d.com/Manual/SL-CullAndDepth.html), an affect we saw in an earlier lab whereby Unity does not render polygons facing away from the viewer (and, above, you flipped the normals of the container). You are going to 'fix' that by modelling the inside and outside of the container. First, ensure you have stopped the playback of your game. Now, duplicate _Inside_, rename the duplicated object _Outside_, then _Flip Normals_.  Now, when you press _Play_, you should be able to walk around a correctly rendered shipping container.

Next, you are going to put some stairs next to the container so you can walk up to its roof. Create a _New Shape_ from the ProBuilder window. Select a _Stair_ with 6 steps, a height of 3 metres and a depth of 6. Hit _Build_, then _Transform_ the stairs so they look like Figure 3 - facing forward and to the left of the container.

![](./images/shippingContainerStairs.png)

_Figure 3: Shipping container stairs_

Now, when you press _Play_, you should be able to walk up the stairs and then walk off the roof of the container and fall to the ground.

Stop playback, as you are now going to put a door wall on the front of the container. Create a _New Shape_ from the ProBuilder window. Select a _Door_, with a width and height of 3 metres, a door height and leg width of 0.5 metres and a depth of 0.1 metres. Hit _Build_, then _Transform_ the door so it is on the front of the container. Set the material and texture, so it matches those of the _Inside_ and _Outside_ walls. Finally, make the door a child of your container. Figure 4 shows how it might look.

![](./images/shippingContainerDoor.png)

_Figure 4: Shipping container with a door_

Press _Play_ and explore your scene.

When you have finished exploring, stop playback. You still have a fair amount to do to recreate the scene from earlier labs:

1. You need to put a lampstand in the back lefthand corner of the container (you could use ProBuilder to create a cube for that).
2. Place the _Old_USSR_Lamp_ on the stand.
3. Add a _Large round lamp_ to the ceiling.
4. Both lights need lighting with a _Point Light_.
5. Put four balls inside the container and add the appropriate physics, so they fall and bounce correctly.
6. You could have some fun with the balls, and while playing back your game, you could enter the container and 'kick' the balls out of the door. Or something ;)

Those are all left as exercises.

## Useful Links

+ [ProBuilder](https://unity3d.com/unity/features/worldbuilding/probuilder)
+ [Unity Starter Assets Overview](https://www.youtube.com/watch?v=4QuPlKzdq14)
+ [Z-Fighting](https://www.unity3dtips.com/unity-z-fighting-solutions/)
