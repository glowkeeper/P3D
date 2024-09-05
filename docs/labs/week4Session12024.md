# Week 4, Session 1 - Physics

The goal of this session is to add some physics to your scene, including:

+ Rigidbodies
+ Colliders
+ Kinematics
+ Triggers

![car physics](./images/carPhysics.webp)

[_Figure 1: Making Custom Car Physics_](https://www.youtube.com/watch?v=CdPYlj5uZeI&t=2s)

## 3D Physics

In this setting, 3D physics refers to the properties of objects and how they respond to [forces](../forces.md). Unity's built-in physics engine has a breadth of tools that ensure objects can interact with other objects by approximating natural forces, such as gravity, velocity, acceleration, and friction. Figure 1 shows the properties of Unity's 3D physics engine.

![](./images/physicsProperties.png)

_Figure 1: Unity's physics properties_

Gravity has a more significant effect on objects with greater mass. [Drag](https://en.wikipedia.org/wiki/Drag_(physics)) dampens linear [velocity](https://en.wikipedia.org/wiki/Velocity), and angular drag affects the rotational force of [angular velocity](https://en.wikipedia.org/wiki/Angular_velocity)). [Friction](https://en.wikipedia.org/wiki/Friction) is a resistive force.

## Physics Materials

Unity uses specialised physic materials to adjust the physical collider properties (such as friction and bounciness) of the GameObjects to which they're assigned.

## Rigidbodies

Figure 2 shows that a _RigidBody_ is the main component that enables physical behaviour for a _GameObject_. A _RigidBody_ is a term borrowed from the real world - it is an idealised object that does not deform under the influence of external forces; instead, it maintains its shape and size, making it ideal for analysing mechanical systems in physics and engineering and also for modelling idealised physical systems in Unity. A unity _RigidBody_ also detects and resolves collisions between colliders (see below).

Since a _Rigidbody_ component is responsible for the movement of the _GameObject_ to which it is attached, you shouldn't try to move the _GameObject_ by changing its _Transform_ properties in a script (we'll look at scripting later in the module). Instead, you should [apply forces to push the GameObject](https://docs.unity3d.com/Manual/RigidbodiesOverview.html) and let the physics engine calculate the results.

![](./images/rigidBody.png)

_Figure 2: RigidBody_

## Colliders

_Colliders_ allow Unity to register when two objects interact. They define the [physical collision shape of a _GameObject_](https://docs.unity3d.com/Manual/CollidersOverview.html), such that, a _GameObject_ will react to incoming collisions if it has a _RigidBody_ component that is associated with one or more _Collider_ components. _Colliders_ are invisible and do not _need_ to match the shape of their associated _GameObject_ mesh. The primitive _colliders_, _Box Collider_, _Sphere Collider_ and _Capsule Collider_ are the most straightforward and least processor-intensive.

## Kinematics

When something is _Kinematic_ in Unity, the physics behaviour of its _RigidBody_ component is disabled, so it does not get affected by external forces; a _Kinematic RigidBody_ can still push another _RigidBody_, but it cannot be pushed. Notably, A _Kinematic RigidBody_ still collides with other rigid bodies - that makes them ideal for platforms and elevators, because you want such things to maintain a path while still having the ability to transport that which they've collided (such as a player controller).

## Triggers

_Triggers_ function similarly to _colliders_. However, when _triggers_ interact with _colliders_, they are ignored by the physics engine. Instead, they can execute scripts, which means they are useful for triggering all types of events; examples are some actions when a _collider_ enters an area, tutorial messages or [cutscenes](https://en.wikipedia.org/wiki/Cutscene). You will take advantage of _triggers_ later in the course.

## Exercise

Add physical properties to GameObjects in your scene.

## Links

+ [Physics](https://docs.unity3d.com/Manual/PhysicsSection.html)
+ [Forces](../forces.md)
+ [Built-in 3D Physics](https://docs.unity3d.com/Manual/PhysicsOverview.html)
+ [RigidBody](https://docs.unity3d.com/Manual/class-Rigidbody.html)
+ [Introduction to Rigidbody physics](https://docs.unity3d.com/Manual/RigidbodiesOverview.html)
+ [Colliders Overview](https://docs.unity3d.com/Manual/CollidersOverview.html)
+ [Intro' to the Unity Physics Engine](https://learn.unity.com/tutorial/intro-to-the-unity-physics-engine)
+ [The Physics of AI](https://learn.unity.com/project/the-physics-of-ai)
+ [Drag](https://en.wikipedia.org/wiki/Drag_(physics))
+ [Velocity](https://en.wikipedia.org/wiki/Velocity)
+ [Angular velocity](https://en.wikipedia.org/wiki/Angular_velocity)
+ [Friction](https://en.wikipedia.org/wiki/Friction)
