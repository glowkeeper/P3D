# Lab for Week 5, Session 2 - Animations in Unity

This lab focuses on Unity [animations](https://docs.unity3d.com/Manual/AnimationSection.html).

## Overview

Unity enables you to create simple animations using a standard set of tools.

You can animate _GameObjects_ in Unity using traditional keyframe animation techniques. [Keyframes](https://en.wikipedia.org/wiki/Key_frame) are points on a timeline that contain data about the GameObject animation, such as its Transform data. Essentially _keyframes_ indicate a change that produces an animation, so that, when it plays, Unity is able to interpolate the data from one keyframe to the next and animate the object.

## Make a Plant Grow

Below, you are going to make a plant grow (and wither) using a key press.

### The Animation

Open [Unity Hub](https://docs.unity3d.com/Manual/GettingStartedUnityHub.html), and open the project you created for [Week 4, Session 2](week4Session2.md).

First, you will need another asset, so go to the [Unity asset store](https://assetstore.unity.com/) and import [Lowpoly Flowers](https://assetstore.unity.com/packages/3d/vegetation/plants/lowpoly-flowers-47083).  Before you can use the imported asset, you must update it to use URP; so go to _Edit_, _Render Pipeline_, _Universal Render Pipeline_, _Upgrade Project Materials ..._.

Create an empty _GameObject_, and name it _Flower_, then drag one of the _Lowpoly Flowers_ into that. This step means that any animation you create on the _Lowpoly Flower_ will be animated relative to the position of the _Flower GameObject_ and not the scene itself. Position the _Flower_ parent so that it is front of the door, then scale the _Lowpoly Flower_ so it is 10 across all three axis, and postion it so it is standing on the floor. 

Animation window,

```
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class Grow : MonoBehaviour
{
    [SerializeField] private string playerTag;
    [SerializeField] private string dieTrigger;
    [SerializeField] private string growTrigger;

    private Animator animator;
    private bool inTrigger = false;

    // Start is called before the first frame update
    void Start()
    {
        animator = GetComponentInChildren<Animator>();
    }

    // Update is called once per frame
    void Update()
    {
        if((Input.GetKeyDown(KeyCode.G)) && inTrigger )
        {
            animator.SetTrigger(growTrigger);
        }
    }

    private void OnTriggerEnter(Collider other)
    {
        //Debug.Log("In here");
        if(other.tag == playerTag)
        {
            inTrigger = true;
        }
    }

    private void OnTriggerExit(Collider other)
    {
        //Debug.Log("Exiting here");
        if (other.tag == playerTag)
        {
            inTrigger = false;
            animator.SetTrigger(dieTrigger);
        }
    }
}
```

## Useful Links

+ [Animations](https://docs.unity3d.com/Manual/AnimationSection.html)
+ [How to Animate in Unity 3D](https://www.youtube.com/watch?v=sgHicuJAu3g)
