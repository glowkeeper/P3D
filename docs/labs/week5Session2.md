# Lab for Week 5, Session 2 - Animations in Unity

This lab focuses on Unity [animations](https://docs.unity3d.com/Manual/AnimationSection.html).

## Overview

You can animate _GameObjects_ in Unity using traditional [Keyframe](https://en.wikipedia.org/wiki/Key_frame) animation techniques. Keyframes are points on a timeline that contain data about the animation, such as a _GameObjects_ position or scale. Essentially _keyframes_ indicate a change that produces an animation, so that, when it plays, Unity is able to interpolate the data from one keyframe to the next, thus animating the object.

## Make a Plant Grow

Below, you are going to make a flower grow. This is a special flower that only blooms for you - it will only grow when you are near and when you tell it to. And when you leave, it whithers away.

### The Animation

Open [Unity Hub](https://docs.unity3d.com/Manual/GettingStartedUnityHub.html), and open the project you created for [Week 4, Session 2](week4Session2.md).

First, you will need another asset, so go to the [Unity asset store](https://assetstore.unity.com/) and import [Lowpoly Flowers](https://assetstore.unity.com/packages/3d/vegetation/plants/lowpoly-flowers-47083).  Before you can use the imported asset, you must update it to use URP; so go to _Edit_, _Render Pipeline_, _Universal Render Pipeline_, _Upgrade Project Materials ..._.

Create an empty _GameObject_, and name it _Flower_, then drag one of the _Lowpoly Flowers_ into that. This step means that any animation you create on the _Lowpoly Flower_ will be animated relative to the position of the _Flower GameObject_ and not the scene itself. Position the _Flower_ parent so that it is front of the door, then scale the _Lowpoly Flower_ so it is 10 across all three axis, and postion it so it is standing on the floor, as it is in Figure 1, below.

![](./images/flower.png)

_Figure 1: The Flower_

Now we're going to animate the flower using two animations - one for when it is hibernating, waiting for you to come nearby, and the other for when you tell it to grow.

First, create an _Animations_ folder in the _Project_ tab. Next, go to _Window_, _Animation_, and dock the tab wheresoever you wish. Select the _Lowpoly Flower_ in the _Hierarchy_ and click on _Create_ in the _Animation_ window. Select the _Animations_ folder you created above and call the animation _Hibernation_. With the animation timeline at 0, press _Record_, then move the flower so it is below ground. Stop recording. Move the animation timeline forward half-a-second and press _Record_ once more. Move the flower's position ever-so-slightly, but ensure it remains below ground. Stop recording. Now _Create New Clip_, call it _Flourish_, and with the animation timeline at 0, press _Record_. Again move the flower so it is below ground and Stop recording. Move the animation timeline forward two seconds and press _Record_ once more. This time, move the flower's postion so it is above ground. Stop recording.

Find the _Flourish_ animation in the _Project_ tab, and in the _Inspector_ tab, unset _Loop Time_ - you want the flower to stay in bloom until you leave.

Select the _Lowpoly Flower_ in the _Hierarchy_, and from the _Inspector_ tab, open up the _Animator Controller_. In the controller's _Parameters_, add two Triggers, "Grow" and "Hibernate". Now add a transition from _Hibernation_ to _Flourish_, and visa-versa. Highlight the transition from _Hibernation_ to _Flourish_ and add the "Grow" _condition_. Highlight the transition from _Flourish_ to _Hibernation_ and add the "Hibernate" _condition_. Figure 2 shows what your _Animator Controller_ should look like.

![](./images/animationController.png)

_Figure 2: Animation controller_

Finally, you need a script to make the flower bloom and hibernate, so create a _C# Script_ called _Grower_, and make it look like this:

```
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class Grower : MonoBehaviour
{
    [SerializeField] private string playerTag;
    [SerializeField] private string hibernateTrigger;
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
            animator.SetTrigger(hibernateTrigger);
        }
    }
}
```

Drag the _Grower_ script onto the _Flower_ parent in the hierarchy. Set the _Player_ field to "Player", the _Hibernate_ field to "Hibernate" and the _Grow_ field to "Grow". Ensure your _FPSController_ has the "Player" tag set. Finally, add a _Box Collider_, set _Is Trigger_ and position and size the collider so it looks similar to Figure 3, below.

![](./images/boxCollider.png)

_Figure 3: Box collider_

Press _Play_. Now, when you walk near the flower and press _G_ on your keypad, your flower will grow and bloom, as in Figure 4. And when you walk away, it will wither away, waiting for you to come near, again.

![](./images/flowerInBloom.png)

_Figure 4: Flower in bloom_

You can play around with the timings of the transitions to make the flower grow and wither at different speeds. Those are left as exercises.

## Useful Links

+ [Animations](https://docs.unity3d.com/Manual/AnimationSection.html)
+ [How to Animate in Unity 3D](https://www.youtube.com/watch?v=sgHicuJAu3g)
