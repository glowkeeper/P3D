# Lab for Week 4, Session 2 - Audio in Unity

This lab serves as an introduction to Unity [audio](https://docs.unity3d.com/Manual/Audio.html).

## Overview

Sound plays an important role in the real world, and so it also has an important role in any 3D application or video game, since it helps create tension, add emotion and immerse the user/player into the virtual space that you create for them. To put it simply, the virutal worlds you create would be incomplete without appropriate sound effects.

Unity uses Audio Sources, attached to _GameObjects_, to emit sound. Those sounds are then picked up by an Audio Listener attached to another object, which is often the main camera.

## Add Footsteps

Below, you are going to add some footsteps to the [First Person Character Controller](https://assetstore.unity.com/packages/essentials/starter-assets-first-person-character-controller-196525) (FPC) that you started using in an earlier lab.

### Adding Sound to the FPC

Open [Unity Hub](https://docs.unity3d.com/Manual/GettingStartedUnityHub.html), and open the project from the last lab.

Highlight the _PlayerCapsule_ in the _Hierarchy_, then find the script attached to the _First Person Controller_ in the _Inspector_, and open it.

First, you should add the private member variables that make the footsteps work:

```csharp
// Audio Settings
[Header("Sounds")]
private AudioSource audioSource;
[SerializeField] private AudioClip[] footstepSounds;    // an array of footstep sounds that will be randomly selected from.
[Min(1.0f)]
[SerializeField] private float stepRate = 1.0f;
private float nextStep = 0.0f;
```

Next, in the script's `Start` method, you should assign the _AudioSource_ to its member variable:

```csharp
audioSource = GetComponent<AudioSource>();
```

Now, in the script's `Move` method, you should call the method we're going to use to actually play the footstep sounds. 

```csharp
PlayFootStepAudio();
```

And now create the `PlayFootStepAudio` method:

```csharp
private void PlayFootStepAudio()
{
    // Debug.Log("Next " + nextStep);
    if (Grounded && _speed > 0.0f && Time.time > nextStep)
    {
        // Debug.Log("Time " + Time.time);
        float offset = _speed;
        if ( _speed >= stepRate ) {
            offset = (stepRate / _speed);
        } 
        nextStep = Time.time + offset;
        // pick & play a random footstep sound from the array,
        // excluding sound at index 0
        int n = Random.Range(1, footstepSounds.Length);
        audioSource.clip = footstepSounds[n];
        audioSource.PlayOneShot(audioSource.clip);
        // move picked sound to index 0 so it's not picked next time
        footstepSounds[n] = footstepSounds[0];
        footstepSounds[0] = audioSource.clip;
    }    
}
```

Before we can use the script in the game, we need to assign an _AudioSource_ to the _PlayerCapsule_ in the _Hierarchy_, and assign footstep audio clips to the `footstepSounds` array that we exposed to the _Inspector_. If you go the the [P3D GitHub repository](https://github.com/glowkeeper/P3D), you will find 4 footstep sound files in the directory _assets/audio_. Download those, then in the _Project_ tab, _Create_, _Folder_, call it _audio_, and put the downloaded footstep sounds in there. Now, in the _First Person Controller_ in the _Inspector_, set Footstep Sounds to 4, and then drag each of your footstep clips into each of the 4 available fields. Now press _Play_, and you should hear your FPC's footsteps.

There are two added exercises. First, make your footsteps code more robust by only attempting to play sound if both an _AudioSource_ has been added to the _PlayCapsule_ and audio clips have been added to the `footstepSounds` array. Secondly, also add jump and landing sounds (you will find appropriate sound files on the [P3D GitHub repository](https://github.com/glowkeeper/P3D)).

## 3D Spatial Sound

Below, you will add a simple attenuated 3D sound to a radio, so that its volume increases and decreases as your FPC gets closer or moves further away.

### A Radio Playing

First, you will need another asset, so go to the [Unity asset store](https://assetstore.unity.com/) and import [HQ PBR Old Retro Radio](https://assetstore.unity.com/packages/3d/props/hq-pbr-old-retro-radio-free-180303). As ever, ensure update it to use the _High Definition Render Pipeline (HDRP); so go to _Edit_, _Render Pipeline_, _HD Render Pipeline_, _Upgrade from Builtin Pipeline_, _Upgrade Project Materials..._.

## Useful Links

+ [Unity Audio](https://docs.unity3d.com/Manual/Audio.html)
+ [Audio Overview](https://docs.unity3d.com/Manual/AudioOverview.html)
+ [freesound](https://freesound.org/)