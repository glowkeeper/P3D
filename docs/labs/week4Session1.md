# Lab for Week 4, Session 1 - 3D Physics in Unity

This lab introduces 3D physics in [Unity](https://unity.com/). This module will demonstrate [3D physics for object-oriented projects](https://docs.unity3d.com/Manual/PhysicsOverview.html), and not the newer [Data-Oriented Technology Stack (DOTS)](https://docs.unity3d.com/Packages/com.unity.physics@0.5/manual/index.html) physics package, which is still in previeq and therefore, not quite production-ready. However, should you be using DOTS already, then you are welcome to use that for your coursework.

## Overview

Unity's physics engine has a breadth of tools that ensure objects are able to interact with other objects by approximating natural forces, such as gravity, velocity, acceleration, and friction. Figure 1 shows the properties of Unity's 3D physics engine.

![](./images/physicsProperties.png)

_Figure 1: Unity's physics properties_

Figure 2 shows that a _RigidBody_ is the main component that enables physical behaviour for a _GameObject_, enabling that object to react to physics properties, such as gravity. Since a _Rigidbody_ component is responsible for the movement of the _GameObject_ to which it attached, you shouldn’t try to move the _GameObject_ by changing its _Transform_ properties. Instead, you should [apply forces to push the GameObject](https://docs.unity3d.com/Manual/RigidbodiesOverview.html) and let the physics engine calculate the results.

![](./images/rigidBody.png)

_Figure 2: RigidBody_

_Colliders_ allow Unity to register when two objects interact. They define the [shape of a _GameObject_ for the purposes of physical collisions](https://docs.unity3d.com/Manual/CollidersOverview.html), such that, a _GameObject_ will react to incoming collisions if it has a _RigidBody_ component that is associated with one or more _Collider_ components. _Colliders_ are invisible and do not need to match the shape of the mesh of the _GameObject_ to which they are associated. The primitive _colliders_, _Box Collider_, _Sphere Collider_ and _Capsule Collider_ are the simplest and least processor-intensive.

_Triggers_ function similarly to _colliders_. However, when _triggers_ interact with _colliders_, they are ignored by the physics engine. Instead, they are able to execute scripts, which means they are useful for triggering all types of events; examples are some action when a _collider_ enters an area, tutorial messages or [cutscenes](https://en.wikipedia.org/wiki/Cutscene).

## Some Simple Physics

(Gravity has a greater affect on objects with greater mass. [Drag](https://en.wikipedia.org/wiki/Drag_(physics) dampens linear [velocity](https://en.wikipedia.org/wiki/Velocity), and angular drag affects the rotational force of [angular velocity](https://en.wikipedia.org/wiki/Angular_velocity))

## Physics Debugger

The physics bebuggerer allows you to profile and inspect _colliders_ by visualising which _GameObjects_ are colliding with each other.

To open the debugger, go to _Window_, _Analysis_, _Physics Debugger_s.

## Useful Links

+ [Intro' to the Unity Physics Engine](https://learn.unity.com/tutorial/intro-to-the-unity-physics-engine-2019-3)
+ [3D Physics for object-oriented projects](https://docs.unity3d.com/Manual/PhysicsOverview.html)
+ [Unity Physics Fundamentals](https://learn.unity.com/project/unity-physics-fundamentals)
+ [Physics Debug Visualization](https://docs.unity3d.com/Manual/PhysicsDebugVisualization.html)
