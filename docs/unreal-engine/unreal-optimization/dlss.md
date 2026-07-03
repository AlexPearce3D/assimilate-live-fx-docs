# DLSS

## Overview

DLSS is a major performance enhancer for Unreal Engine, that is easy to set up and doesn't cost anything!

!!! warning

```
You may not get any performance increases in the editor or even in Play mode, you might have to Play the Project as a game or package to an .exe file to see any benefits.
```

To launch your game like a packaged project, you can go to the Play menu, Quick Launch, and click on your Desktop name. (You may need to set up your package settings first, and the first time you package, it may take a long time to package. Even for a simple scene, it can take 30 minutes on a powerful machine for the first build. Subsequent builds can be less than 5 minutes).

A heavy scene for comparison, these were the results:

Unpackaged project, Play in window, fullscreen = 17-34fps, mostly \~34fps

Packaged Project, full screen = 50-55fps, mostly \~55fps.

The definition from Nvidia's website:

NVIDIA DLSS 3.5 is a suite of AI rendering technologies powered by Tensor Cores on GeForce RTX GPUs for faster frame rates, better image quality, and great responsiveness. DLSS now includes Super Resolution & DLAA (available for all RTX GPUs), Frame Generation (RTX 40 Series GPUs), and Ray Reconstruction (available for all RTX GPUs). To get the full benefits of DLSS, download both DLSS Super Resolution and DLSS Frame Generation SDKs/Plugins.

## Setup your PC

!!! warning

```
You must go to Settings, Graphics Settings, and Turn on Hardware-Accelerated GPU Scheduling to see any difference in performance from DLSS!
```

Press the Windows key and search for Graphics Settings, and turn on Hardware-accelerated GPU scheduling. Restart your computer.

Optionally, you may want to update your GPU drivers.

## Download and Install the Plugins

1. Go to [https://developer.nvidia.com/rtx/dlss/get-started#ue-requirements](https://developer.nvidia.com/rtx/dlss/get-started#ue-requirements) and download the plugins.<br>
2. Unzip the folder and go into the folder. Go to the folder inside called Plugins, and copy these plugins.<br>
3.  You can install the plugins to your Unreal Engine plugins or to your project plugins. We recommend installing it to individual projects. To do this, go to your project folder, if there is not already a folder called "Plugins", create one. Make sure to capitalize the P and make sure it's spelled exactly Plugins.

    Paste the folders inside this Plugins folder.<br>
4. If you had Unreal Engine open, restart it now.
5. Check to make sure Nvidia Dlss Frame Generation, Super Resolution, and NIS are enabled.<br>

## Working with DLSS in Unreal Engine

You can change the settings by going to Project Settings and typing in dlss.

In the Command Prompt, enter "stat gpu" and check to see if DLSS shows up. You can type "stat gpu" again to make the overlay go away.

## Helpful Console Commands

### Nvidia Image Scaling (NIS)

NIS upscaling in-game: The following console variables can be set to enable NIS:

1\. r.NIS.Enable 1\
2\. r.NIS.Upscaling1\
3\. r.ScreenPercentage 50\
4\. r.TemporalAA.Upsampling0 5. r.TemporalAA.Upscaler 0\
6\. Optional r.NIS.Sharpness 0.5

NIS sharpening in-game: The following console variables can be set to enable a NIS sharpening pass regardless of whether temporal or spatial upscaling is used.

1\. r.NIS.Enable 1\
2\. r.NIS.Sharpness 0.5

### Super Resolution

1\. r.NGX.Enable 1 (can be overriden on the command line with -ngxenable)\
2\. r.NGX.DLSS.Enable 1\
3\. r.ScreenPercentage 66.7

### Frame Generation

The DLSS Frame Generation plugin uses various engine side hooks, which can be configured by the following cvars. Their default values

r.Streamline.ViewIdOverride\
0: use ViewState.UniqueID\
1: on set view ID to 0 (default)

r.Streamline.TagSceneColorWithoutHUD\
Pass scene color without HUD into DLSS Frame Generation (default = true)

r.Streamline.Editor.TagSceneColorWithoutHUD\
Pass scene color without HUD into DLSS Frame Generation in the editor (default = false)

r.Streamline.ClearSceneColorAlpha\
Clear alpha of scenecolor at the end of the Streamline view extension to allow subsequent UI drawcalls be represented correctly in the alpha channel (default=true)

r.Streamline.Editor.TagUIColorAlpha\
Experimental: Pass UI color and alpha into Streamline in Editor PIE windows (default = false)

Finetuning motion vectors for DLSS Frame Generation

DLSS Frame Generation requires correct motion vectors to function properly. The following console variable can be used to tweak values during game development

r.Streamline.DilateMotionVectors

0: pass low resolution motion vectors into DLSS Frame Generation (default)\
1: pass dilated high resolution motion vectors into DLSS Frame Generatio. This can help with improving image quality of thin details.

r.Streamline.MotionVectorScale\
Scale DLSS Frame Generation motion vectors by this constant, in addition to the scale by 1/ the view rect size. (default = 1.0)

Finetuning depth for DLSS Frame Generation

r.Streamline.CustomCameraNearPlane\
Custom distance to camera near plane. Used for internal DLSS Frame Generation purposes, does not need to match corresponding value used by engine. (default = 0.01)

r.Streamline.CustomCameraFarPlane\
Custom distance to camera far plane. Used for internal DLSS Frame Generation purposes, does not need to match the corresponding value used by engine. (default = 75000.0)
