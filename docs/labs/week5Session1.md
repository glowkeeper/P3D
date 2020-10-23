# Lab for Week 5, Session 1 - Scripting in Unity

This lab introduces [Unity Scripting](https://docs.unity3d.com/Manual/ScriptingSection.html).

## Overview

Scripting is an essential ingredient to Unity applications because it enables your scenes to respond to user input and to arrange for events to happen when they should. Scripts can do many other things, besides; for example, you can create graphical effects, control physical gameplay behaviour or even customise the Unity editor itself.

## Basic Scripting

Open [Unity Hub](https://docs.unity3d.com/Manual/GettingStartedUnityHub.html), and open the project you created in the [last lab](week4Session2.md).

Below is the basic script created by Unity whenever you _Create_, _C# Script_. It demonstrates a couple of important features.

```
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

First, [C#](https://docs.microsoft.com/en-us/dotnet/csharp/) is an object-oriented language feauring classes that you instantiate as objects (as and when required). The class _NewBehaviourScript_, above, inherits from Unity's [MonoBehaviour](https://docs.unity3d.com/ScriptReference/MonoBehaviour.html), which is a base class from which every Unity script inherits functionality. _NewBehaviourScript_ overrides the _MonoBehaviour_ methods _Start_ and _Update_. _Start_ is called when the object is first created (and before the first [frame](https://www.cprogramming.com/tutorial/animation/frames_and_layers.html) update). _Update_ is called once every frame render.

_MonoBehaviour_ defines other behaviour, too - probably the one you will see most frequently is _FixedUpdate_, which is called by the physics system at a rate independant from the main game frame rate. For example, if the physics engine is running at fifty calls per second, and the frame rate is running at twenty-five frames per second (FPS), then _FixedUpdate_ will be called twice per frame. For that reason, it is bad practice to put physics calculations in _Update_ - they should go in _FixedUpdate_, instead. Equally, user input should go in _Update_, and not _FixedUpdate_. You will see an example of that destinction, below. Finally, the frame rate for most games is _usually_ around 60 FPS.


## Useful Links

+ [Scripting](https://docs.unity3d.com/Manual/ScriptingSection.html)
+ [Scripting API](https://docs.unity3d.com/ScriptReference/)
+ [Unity Learn - Scripting](https://learn.unity.com/search?k=%5B%22q%3AScripting%22%5D)
+ [Adding User Input](https://www.youtube.com/watch?v=pwZpJzpE2lQ)
