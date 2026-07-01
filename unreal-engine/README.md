# 🎮 Unreal Engine

## Quick Tips

* As of right now, UE <> Live FX only works on Windows
* Recommended to use 5.3 (or later)
* Make sure under the Camera tab, that there is an active camera, even if you don’t have tracking.
* You may need to disable the Firewall to allow the signal to pass through your system.

## Overview

Live FX works differently with Unreal Engine than many other media servers. There are many benefits to the way we handle certain aspects of the Unreal Engine workflow.&#x20;

The main preferred way of working with Unreal Engine and LED walls is to run the Unreal Engine project as a game or to package the project to an .exe file. There are a few benefits to working this way that we will go over in different ways throughout the documentation.&#x20;

The main method we use to control parameters in Unreal Engine is through Web Remote Control.&#x20;

## LED Unreal Workflow

We do not require an nDisplay setup but rather take the output of the cine camera actor and project that onto the LED volume in Live FX.&#x20;

The image from UE to LFX can be sent ideally via UE Textureshare SDK, in case UE and LFX run on the same system.&#x20;

If they run on separate systems, you can send them with SDI or NDI.&#x20;

Live FX also has a live link plugin for Unreal, where it can send timecode, tracking data, scene, take, and record start/stop to UE.&#x20;

But you can of course also pipe tracking directly into UE and just capture the image output back into LFX for projection mapping.

Our workflow has the advantage, that it is very fast to set up, and also comes with the lowest possible latency.&#x20;

The main downside is, that we can only work with one instance of Unreal.&#x20;

If (for whatever reason) you require multiple UE render nodes, then our setup won't work.

### Outer Frustum

One thing that we are still working on, is the outer frustum.&#x20;

Since we take in the output of the cine camera actor, we only get what the UE camera sees - i.e. the inner frustum.&#x20;

For the outer frustum, there are several options, by setting up a second camera actor, with a somewhat wider lens, being static/untracked: If the output of both cine camera actors comes in via NDI, that just works.&#x20;

If the inner frustum comes in via UE Texture share, the outer frustum needs to come in via NDI.&#x20;

This in turn will however cause both streams to be slightly out of sync. This is not an issue if you're not shooting thunder and lightning scenes, where inner and outer frustum need to be totally in sync.&#x20;

The alternative would be a rendered ProRes out of UE that can be used as outer frustum - same sync limitation, though.&#x20;

Lastly, if the scene is calm and quiet, you could work with only one cine camera actor (inner frustum), move that back a little to capture more of the scene, pull a snapshot inside LFX, and use that as the background. It'll be static of course, but that's not an issue for many setups.&#x20;

## Green Screen Workflow

Live FX can bring in the camera signal easily and use several different qualifiers to pull a good key and composite the Unreal Engine background. You can also work with hardware keyers such as Blackmagic Ultimatte.&#x20;

The Live Link plug-in allows for triggering Take Recorder as well, so you can go back and re-render your Unreal project with higher resolution and higher quality if you need to.&#x20;

Live FX also allows for a more advanced online/offline workflow. You can import your camera raw files, sync to timecode, apply color correction, and finish all from Assimilate Scratch (included in Live FX Studio).&#x20;

