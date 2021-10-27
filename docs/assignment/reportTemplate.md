# Report Template

Below is a suggested template for your report.

---
## Introduction

My scene features an industrial landscape...

### Project Plan

![](./images/basicProjectPlan.png)

## Technical Element

I used diffuse materials (Shirley, 2020) to attempt to recreate a post-industrial feel to my scene...

## Script

The script below is attached to the first-person controller. It will destroy any object tagged with _otherTag_ and which has a collider marked as a trigger.

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

## Unique Element

Figure 1, below, shows an animation controller for describing the growth of some alien spores I use to add an _other-worldly_ atmosphere to my scene.

![](./images/animationController.png)

_Figure 1: Spore animation_

## Summary

My scene demonstrates all the essential elements introduced throughout the labs, such as lighting, materials and textures, 3D physics, modelling, scripting, animation, sound and particle systems. It also incuds an ethereal element when...

## Future Work

I see more scenes, describing more worlds featuring...

## Appendix

Destroyer.cs:

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

SpawnObjects.cs:

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
        scoreText.text = scorePreText;
        timeText.text = timePreText;
    }

    // Update is called once per frame
    void Update()
    {
        if (numObjects < maxObjects)
        {
            SpawnObject();
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

    void SpawnObject()
    {
        GameObject mObjectClone = Instantiate(mObject, spawnPoint.position, Quaternion.identity) as GameObject;
        mObjectClone.SetActive(true);
        mObjects.Add(mObjectClone);
        //Debug.Log("List size " + Objects.Count);
    }
}
```

## References

Below are all the references used in my application and report.

### GitHub

GitHub homepage: https://github.com/glowkeeper/P3D

Application directory: https://github.com/glowkeeper/P3D/src/assignment

### Asset References

+ [Standard Assets](https://assetstore.unity.com/packages/essentials/asset-packs/standard-assets-for-unity-2018-4-32351)
+ [Free Shipping Containers](https://assetstore.unity.com/packages/3d/environments/industrial/free-shipping-containers-18315)
+ [Old USSR Lamp](https://assetstore.unity.com/packages/3d/props/electronics/old-ussr-lamp-110400)
+ [PBR LAMPS PACK](https://assetstore.unity.com/packages/3d/props/interior/free-pbr-lamps-70181)
+ [Ball Pack](https://assetstore.unity.com/packages/3d/props/ball-pack-446)

### Script References

...references to any scripts you've created.

### Report References

Peter Shirley, 2020, Ray Tracing in One Weekend, Diffuse Materials. Available at https://raytracing.github.io/books/RayTracingInOneWeekend.html#diffusematerials, Accessed October, 2020.
