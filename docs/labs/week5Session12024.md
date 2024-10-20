# Week 5, Session 1 - Multimedia

The goal of this session is to have you include audio and video in your scenes.
![audio waveform](images/audio.jpg)

[_Figure 1: How to Set Audio Levels for Video_](https://www.premiumbeat.com/blog/how-to-set-audio-levels-for-video/)

## Audio

Audio plays a rich role in immersing your users in your scenes. Sound is pivotal in the real world, so it is vital for any 3D application or game since it helps create tension and add emotion to the virtual spaces you create; simply put, your virtual worlds would only be complete with appropriate sound effects. So, if you want to create highly immersive experiences, you should consider bringing sound design to the forefront.

Unity uses audio sources attached to GameObjects. An audio listener attached to another entity (such as the main camera) picks up those sounds. Unity can create attenuated 3D sounds whose volume increases and decreases with distance.

### Diegetic Sound

Diegetic sound emanates directly from the action; hence, it's sometimes called 'actual sound'. Its origin is the Greek diḗgēsis, meaning 'narration, narrative'.

### Non-diegetic Sound

Non-diegetic sound is audio that does not emanate directly from the action; in other words, it's the type of sound characters in a game would not hear, but we players can. Audio designers use non-diegetic sound to create exaggerated effects that add to the drama.

## Unity Audio

Unity supports audio files in AIFF, WAV, MP3, and Ogg formats. To simulate positional 3D audio, Unity requires sounds to originate from _AudioSources_ attached to _GameObjects_. An _AudioListener_ (more often than not, the main player camera) then picks up the emitted sounds.

### Mixer

Unity's Audio Mixer allows you to master and apply effects to various audio sources.

![Audio Mixer](../images/audioMixer.png)

_Figure 2: Unity's Audio Mixer_

## Video

Clever use of moving images can add a natural sparkle to the scenes you produce.

Unity uses a video player component to attach video files to game objects, which it plays on the object's texture. The video player also has access to audio sources, which means it can leverage 3D sound capabilities, too.

## Exercise

Add appropriate audio to your scene. And if you can find a suitable place to include some video, do that, too.

## Links

+ [Unity Audio](https://docs.unity3d.com/Manual/Audio.html)
+ [Audio Overview](https://docs.unity3d.com/Manual/AudioOverview.html)
+ [freesound](https://freesound.org/)
+ [Eight essential ways to use sound in video games](https://www.gamesindustry.biz/eight-ways-to-use-sound-in-video-games)
+ [Sound Effects 101: Ambient vs. Foley](https://lwks.com/blog/sound-effects-101-ambient-vs.-foley#:~:text=Understanding%20Sound%20Effects%20and%20Their%20Place%20in%20a%20Production&text=They%20set%20the%20scene%20and,or%20the%20rustling%20of%20clothing.)
+ [What is Non-diegetic Sound?](https://www.studiobinder.com/blog/what-is-non-diegetic-sound/)
+ [Tomb Raider Retrospective: Nathan McCree Interview](https://www.youtube.com/watch?v=AZOPXzgbw2s)
