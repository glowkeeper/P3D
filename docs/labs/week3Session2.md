# Lab for Week 3, Session 2 - Scripting in Unity

This lab introduces [Unity Scripting](https://docs.unity3d.com/Manual/ScriptingSection.html).

## Overview

Scripting is an essential ingredient to Unity applications because, for example, it enables your scenes to respond to user input and allows you to arrange for events to happen when they should. In fact, scripts allow you to do many things; you can create graphical effects, control physical gameplay behaviour or even customise the Unity editor itself.

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

Unity defaults to a _Time_, _Fixed Timestep_ of 0.02, which translates to _FixedUpdate_ getting called fifty times a second, and a _VFX_, _Fixed Timestep_ of 0.001666667, which translates to 60 FPS.

## A Simple Game

Below, you will create a simple game using the shipping container you created in [Week 3, Session 1](./week3Session1.md), using [ProBuilder](https://unity3d.com/unity/features/worldbuilding/probuilder).

The game you create will spawn a number of balls in the scene - it will be your job to destroy the balls as quickly as you can.

### Introduction to Scripting

Open [Unity Hub](https://docs.unity3d.com/Manual/GettingStartedUnityHub.html), and open the project you created in the [last lab](week4Session2.md).

First, create a bouncing ball using the same processes you used when creating the balls in previous sessions; i.e. create a sphere with a material and texture, then attach to that a _RigidBody_ and a _Physics Material_. You may need to find some ball assets from the [unity asset store](https://assetstore.unity.com/); if so, go there, and search for all free ball assets and add any you like. You will then need to download and import them into your project, using the _Package Manager_.
You need to make the ball a [Prefab](https://docs.unity3d.com/Manual/Prefabs.html), so that you can reuse its properties across all the balls you are going to spawn in the game. To do so, in the _Project_ tab, create a folder called _Prefabs_ and drag you ball into that. Scale the ball prefab to a size you prefer. You don't actually want this ball appearing in the game (later, in a script, you will _SetActive_ all the balls you create), so set the _Ball_ as _inactive_ in the Inspector window.

Next, you will create a spawn point at the centre of the shipping container; once the game starts, that is where the balls will appear. Create an empty _GameObject_, and rename it _SpawnPoint_. Similar to Figure 2, below, add an _icon_ to that spawn point (so you can see it in the _Scene_) and transform it so it's at the centre of the container.

![](./images/spawnPoint.png)

_Figure 2: Spawn point_

Next, create an empty _GameObject_ and call it _SpawnManager_ - you will attach to that a script for managing the creation of the balls needed for the game. In the _Scripts_ folder, create a _C# Script_ called _SpawnObjects_. It should look like this:

```csharp
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class SpawnObjects : MonoBehaviour
{
    [SerializeField] private GameObject mObject;
    [SerializeField] private Transform spawnPoint;
    [SerializeField] private int maxObjects;

    private int numObjects;

    // Start is called before the first frame update
    void Start()
    {

    }

    // Update is called once per frame
    void Update()
    {
        if (numObjects < maxObjects)
        {
            SpawnObject(numObjects);
            numObjects++;
        }  

    }

    void SpawnObject(int num)
    {
        GameObject mObjectClone = Instantiate(mObject, spawnPoint.position, Quaternion.identity) as GameObject;
        mObjectClone.SetActive(true);
    }
}
```

Drag the script onto the _SpawnManager_, then drag the _Ball_  into the script's _M Object_ field and the _Spawn Point_ into its _Spawn Point_ field. Set the _Max Objects_ field to 10. Press _Play_ - if your _Game_ tab looks something similar to Figure 3, below, then congratulations! You have created a scripted game!

![](./images/scriptedScene.png)using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class SpawnObjects : MonoBehaviour
{
    [SerializeField] private GameObject mObject;
    [SerializeField] private Transform spawnPoint;
    [SerializeField] private int maxObjects;

    private int numObjects;

    // Start is called before the first frame update
    void Start()
    {

    }

    // Update is called once per frame
    void Update()
    {
        if (numObjects < maxObjects)
        {
            SpawnObject(numObjects);
            numObjects++;
        }  

    }

    void SpawnObject(int num)
    {
        GameObject mObjectClone = Instantiate(mObject, spawnPoint.position, Quaternion.identity) as GameObject;
        mObjectClone.SetActive(true);
    }
}

_Figure 3: The scripted scene_

Now you are going to write a script that destroys the balls, so create a _C# Script_ called _Destroyer_, and make it look like this:

```csharp
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

Drag the _Destroyer_ script onto the _FPSController_ and set its _Other Tag_ field to "Ball". Add the very same tag "Ball" to the _Ball_ prefab and add a _Sphere Collider_ to that, selecting its _Is Trigger_ field and setting the _Radius_ to 1.  Press _Play_, and now you should be able to walk around the scene destroying the balls.

Finally, you are going to gamify the scene. Modify the _C# Script_ _SpawnObjects_ and make it look like this:

```csharp
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
        scoreText.text = scorePreText;
        timeText.text = timePreText;
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

There are two _UI_, _Text_ elements needed to make it all work - one for outputting the number of balls you've destroyed, and another to output the total time, once you've destroyed every ball. First, since you're using Unity's new input system (that was automatically imported when we imported the [First Person Character Controller](https://assetstore.unity.com/packages/essentials/starter-assets-first-person-character-controller-196525) in a previous lab), you need to enable that in Unity's event system; to do so, _Create_, _UI_, _Event System_, then click on _Replace with InputSystemUIInputModule_. Now you can create the text elements that are required. First, _Create_, _UI_, _Text_, set its _Font Size_ to 24 and rename it _Score Text_. Create another _UI_, _Text_ and set its _Font Size_ to 24. Rename that _Time Text_. Ensure the _Render Mode_ of the text element's parent _Canvas_ is set to _Screen Space - Overlay_. Then place the text elements on top of each other in the canvas on the scene and use the _Rect Transform_ in the _Inspector_ to place the elements in the top lefthand corner. Finally, drag the _Score Text_ UI element into the _Score Text_ field of the _Spawn Objects_ script, and the _Time Text_ UI element into the _Time Text_ field. Now press _Play_ and see if you can beat the time displayed in Figure 4, below!

![](./images/fiveSeconds.png)

_Figure 4: The finished game_

There is, of course, plenty that could be done to improve the game - if you're so inclined, that is left as an exercise. Also left as an exercise is to make the script more robust, perhaps by checking if objects exists before cloning them (for example).

## Useful Links

+ [Scripting](https://docs.unity3d.com/Manual/ScriptingSection.html)
+ [Scripting API](https://docs.unity3d.com/ScriptReference/)
+ [Unity Learn - Scripting](https://learn.unity.com/search?k=%5B%22q%3AScripting%22%5D)
+ [LEARN UNITY](https://www.youtube.com/watch?v=pwZpJzpE2lQ)
+ [Unity Debugging C# Scripts with Visual Studio](https://www.youtube.com/watch?v=d0815qbx3BA&list=PLboXykqtm8dxhCV5SVn0N76jrdCo5HV2a) (**Note**: Unity's pre-installed version of Visual Studio includes the Unity tools)