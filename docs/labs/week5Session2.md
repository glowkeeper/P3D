# Lab - Week 5, Session 2 - Scripting

This lab focuses on:

+ [Scripting](https://docs.unity3d.com/Manual/ScriptingSection.html)

![Scripting](./images/scriptingIntro.jpg)

_Scripting_

## Overview

Scripting is an essential ingredient to Unity applications because they allow you to do many things, such as create graphical effects, control physical gameplay behaviour or react to user input.

Below is the basic script created by Unity whenever you _Create_, _C# Script_. It demonstrates a couple of important features.

```csharp
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class NewBehaviourScript : MonoBehaviour
{
    // Start is called before the first frame update
    void Start()
    {

    }

    // Update is called once per frame
    void Update()
    {

    }
}
```

[C#](https://docs.microsoft.com/en-us/dotnet/csharp/) is an object-oriented language featuring classes that you instantiate as objects (as and when required). The class _NewBehaviourScript_, above, inherits from Unity's [MonoBehaviour](https://docs.unity3d.com/ScriptReference/MonoBehaviour.html), which is a base class from which every Unity script inherits its functionality. _NewBehaviourScript_ overrides the _MonoBehaviour_ methods _Start_ and _Update_ - _Start_ is called when the object is first created (and before the first [frame](https://www.cprogramming.com/tutorial/animation/frames_and_layers.html) update), and _Update_ is called once every frame render.

_MonoBehaviour_ defines other behaviour, too - the one you will likely see most frequently is _FixedUpdate_, which is called by the physics system at a rate independant from the main game frame rate. For example, imagine the physics engine is running at fifty calls per second, and the frame rate is running at twenty-five frames per second (FPS) - then _FixedUpdate_ will be called twice per frame. For that reason, it is bad practice to put physics calculations in _Update_ - they should go in _FixedUpdate_, instead. Equally, user input should go in _Update_, and not _FixedUpdate_. Figure 1, below. shows a flowchart for MonoBehaviour.

![](./images/monobehaviourFlowchart.svg)

_Figure 1: MonoBehaviour Flow Chart_

Unity defaults to a _Time_ _Fixed Timestep_ of 0.02, which translates to _FixedUpdate_ getting called fifty times a second, and a _VFX_ _Fixed Timestep_ of 0.001666667, which translates to 60 FPS.

## The Lab Game

Below is the [class design](https://www.visual-paradigm.com/guide/uml-unified-modeling-language/uml-class-diagram-tutorial/) of the game described in the lab video; it includes examples of composition and inheritance.

![Lab game](./images/labGame.png)

_Lab Game_
