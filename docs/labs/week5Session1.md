# Lab for Week 5, Session 1 - Scripting in Unity

This lab introduces [Unity Scripting](https://docs.unity3d.com/Manual/ScriptingSection.html).

## Overview

Scripting is an essential ingredient to Unity applications because it enables your scenes to respond to user input and to arrange for events to happen when they should. Scripts can do many other things, besides; for example, you can create graphical effects, control physical gameplay behaviour or even customise the Unity editor itself.

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

[C#](https://docs.microsoft.com/en-us/dotnet/csharp/) is an object-oriented language featuring classes that you instantiate as objects (as and when required). The class _NewBehaviourScript_, above, inherits from Unity's [MonoBehaviour](https://docs.unity3d.com/ScriptReference/MonoBehaviour.html), which is a base class from which every Unity script inherits its functionality. _NewBehaviourScript_ overrides the _MonoBehaviour_ methods _Start_ and _Update_ - _Start_ is called when the object is first created (and before the first [frame](https://www.cprogramming.com/tutorial/animation/frames_and_layers.html) update), and _Update_ is called once every frame render.

_MonoBehaviour_ defines other behaviour, too - the one you will likely see most frequently is _FixedUpdate_, which is called by the physics system at a rate independant from the main game frame rate. For example, imagine the physics engine is running at fifty calls per second, and the frame rate is running at twenty-five frames per second (FPS), then _FixedUpdate_ will be called twice per frame. For that reason, it is bad practice to put physics calculations in _Update_ - they should go in _FixedUpdate_, instead. Equally, user input should go in _Update_, and not _FixedUpdate_. Unity defaults to a _Time_, _Fixed Timestep_ of 0.02, which translates to _FixedUpdate_ getting called fifty times a second, and a _VFX_, _Fixed Timestep_ of 0.001666667, which translates to 60 FPS.

## A Simple Game

Below, you will create a simple game out of the shipping container you created in [Week 4, Session 2](./week4Session2.md), using [ProBuilder](https://unity3d.com/unity/features/worldbuilding/probuilder).

### Introduction to Scripting

Open [Unity Hub](https://docs.unity3d.com/Manual/GettingStartedUnityHub.html), and open the project you created in the [last lab](week4Session2.md).




SpawnManager:

```
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.UI;

public class SpawnObjects : MonoBehaviour
{
    [SerializeField] private GameObject mObject;
    [SerializeField] private Transform spawnPoint;
    [SerializeField] private int maxObjects;
    [SerializeField] private Text scoreText;
    [SerializeField] private Text timeText;

    private string scorePreText = "Game Score: ";
    private string timePreText = "Total Time: ";

    private List<GameObject> mObjects;
    private int numObjects;

    // Start is called before the first frame update
    void Start()
    {
        mObjects = new List<GameObject>();
    }

    // Update is called once per frame
    void Update()
    {
        if (numObjects < maxObjects)
        {
            SpawnObject(numObjects);
            numObjects++;
        } else
        {
            for (int i = 0; i < mObjects.Count; i++)
            {
                if (mObjects[i] == null)
                {
                    string gameTime = Time.realtimeSinceStartup.ToString("f2");
                    mObjects.RemoveAt(i);
                    int count = (maxObjects - mObjects.Count);
                    scoreText.text = scorePreText + count;
                    //Debug.Log("Objects left: " + Objects.Count);
                    if (mObjects.Count == 0)
                    {                        
                        //Debug.Log("In here? " + gameTime);
                        timeText.text = timePreText + gameTime;
                    }
                }
            }
        }        

    }

    void SpawnObject(int num)
    {
        GameObject mObjectClone = Instantiate(mObject, spawnPoint.position, Quaternion.identity) as GameObject;
        mObjectClone.SetActive(true);
        mObjects.Add(mObjectClone);
        //Debug.Log("List size " + Objects.Count);
    }
}
```

Destroyer:

```
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class Destroyer : MonoBehaviour
{
    [SerializeField] private string otherTag;

    private void OnTriggerEnter(Collider other)
    {
        if(other.gameObject.tag == otherTag )
        {
            Destroy(other.gameObject);
        }
    }
}
```

## Useful Links

+ [Scripting](https://docs.unity3d.com/Manual/ScriptingSection.html)
+ [Scripting API](https://docs.unity3d.com/ScriptReference/)
+ [Unity Learn - Scripting](https://learn.unity.com/search?k=%5B%22q%3AScripting%22%5D)
+ [Adding User Input](https://www.youtube.com/watch?v=pwZpJzpE2lQ)
+ [Unity Debugging C# Scripts with Visual Studio](https://www.youtube.com/watch?v=d0815qbx3BA&list=PLboXykqtm8dxhCV5SVn0N76jrdCo5HV2a) (**Note: Unity's pre-installed version of Visual Studio includes the Unity tools)
