# Console Commands / Command Line Arguments

## Overview

There are many properties that you can change in Unreal by passing console commands or by adding command line arguments to .exe files.

If you are in Unreal Engine, at the bottom left of the screen you can enter these commands where it says "Enter Console Command"

<figure><img src="../../../assets/image (113).png" alt=""><figcaption></figcaption></figure>

If you are simulating the game, or have already packaged a project, you can press the \` key on the keyboard (same place as \~) and it will prompt you.

These commands are only active until you close the project or game. When you re-open your project, it will be set back to whatever the default values are. If you want the changes to persist, you can change them in their .ini files. 

Console commands and the .ini files are formatted a little differently, for example in the console you would enter "sg.ResolutionQuality 50" (notice the space between the world and the number)

<figure><img src="../../../assets/image (114).png" alt=""><figcaption></figcaption></figure>

In the .ini file, you would enter the same command "sg.ResolutionQuality=50" (notice the equal sign between the word and the number).

<figure><img src="../../../assets/image (116).png" alt=""><figcaption></figcaption></figure>

!!! info

    The commands are not case-sensitive, but it's good practice to match what Unreal Engine does.


cvars = Console Variables



## Output Log

#### Unreal Engine



#### Packaged Project

In a packaged project, the way to see the output log is to create a shortcut and pass the cvar "-log"

<figure><img src="../../../assets/image (117).png" alt=""><figcaption></figcaption></figure>

## Location of .ini files

#### Unreal Engine



#### Packaged Project

\[Path to where you put the packaged file]

\Windows\LightSail\_VP\_Scenes\Saved\Config\Windows\GameUserSettings.ini

The GameUserSettings.ini file is the main file to edit.



## These settings sped up frame rate

r.Shadow.Virtual.ResolutionLodBiasDirection -1  (Default was 0, 5 was also good)



## Change Scalability Settings

In the GameUserSettings.ini file, you can paste this text in there, and adjust them as needed.

\[ScalabilityGroups]   
sg.ResolutionQuality=100   
sg.ViewDistanceQuality=0   
sg.AntiAliasingQuality=1 sg.ShadowQuality=1   
sg.PostProcessQuality=1   
sg.TextureQuality=1   
sg.EffectsQuality=0 sg.FoliageQuality=0   
sg.GlobalIlluminationQuality=3   
sg.ReflectionQuality=3   
sg.ShadingQuality=3

\[/Script/Engine.GameUserSettings]   
bUseVSync=False   
bUseDynamicResolution=False ResolutionSizeX=1920   
ResolutionSizeY=1200   
LastUserConfirmedResolutionSizeX=1920 LastUserConfirmedResolutionSizeY=1200   
WindowPosX=-1   
WindowPosY=-1   
FullscreenMode=1 LastConfirmedFullscreenMode=1   
PreferredFullscreenMode=1   
Version=5   
AudioQualityLevel=0 LastConfirmedAudioQualityLevel=0   
FrameRateLimit=23.976000   
DesiredScreenWidth=1280 bUseDesiredScreenHeight=False   
DesiredScreenHeight=720 LastUserConfirmedDesiredScreenWidth=1280   
LastUserConfirmedDesiredScreenHeight=720 LastRecommendedScreenWidth=-1.000000   
LastRecommendedScreenHeight=-1.000000 LastCPUBenchmarkResult=-1.000000   
LastGPUBenchmarkResult=-1.000000   
LastGPUBenchmarkMultiplier=1.000000  
bUseHDRDisplayOutput=False   
HDRDisplayOutputNits=1000
