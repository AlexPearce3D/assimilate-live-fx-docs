# How to Package an Unreal Engine Project for Live FX

## Package Project

Packaging a project is the same thing as building a game.

!!! warning

```
The first time you package your project, it has to cook everything and it usually takes a long time, but after the first successful build, it usually takes a fraction of the time. For example, it might take 30 minutes to build the first time, and 2 minutes to build the second time.
```

!!! info

```
Some errors you get may be due to plugins that are enabled and do not need to be packaged. For example, I had Nvidia's OptiX denoiser and I got an error that stated
```

### Install Microsoft Visual Studio

First, you must install a specific version of Microsoft Visual Studio, in a very specific way. Follow these instructions for 5.3, or search for the version you need:

> Video/resource: [https://dev.epicgames.com/documentation/en-us/unreal-engine/setting-up-visual-studio-development-environment-for-cplusplus-projects-in-unreal-engine/2](https://dev.epicgames.com/documentation/en-us/unreal-engine/setting-up-visual-studio-development-environment-for-cplusplus-projects-in-unreal-engine/2)

Here are some other helpful resources:

EP01 Setting Up Visual Studio 2022 for Unreal Engine 5:\
[https://www.youtube.com/watch?v=HLwwpLYvY5Y](https://www.youtube.com/watch?v=HLwwpLYvY5Y)

How to install Android SDK Platform Tools (ADB & FASTBOOT) on Windows 11 / Windows 10:\
[https://www.youtube.com/watch?v=OSp5\_wBAVyQ](https://www.youtube.com/watch?v=OSp5_wBAVyQ)

### Package Project

To package your project, go to **`Platforms>Windows>Package Project.`**

Navigate to a folder where you want it to go and press accept.

<figure><img src="../../../.gitbook/assets/image (359).png" alt=""><figcaption></figcaption></figure>

## Change game mode Default Pawn to none

If you don't do this, then when the camera is not moving for 5 minutes or so, it will jump out of the camera and won't allow you to move the camera anymore.

<figure><img src="../../../.gitbook/assets/image (205).png" alt=""><figcaption></figcaption></figure>

!!! info

```
You should also be able to change the game mode by using a console command.
```

## Enable Remote Session

If you haven't done so already, make sure to enable the Plugin "Remote Session", which allows iPhones and iPads to connect via the web remote control.

## Copy Webapp into Packaged Project

For web remote to work correctly, you need to copy over a specific folder and create a specific folder structure in the built folder.

1. **Copy** the folder **Webapp** from your Unreal Engine folder, normally located in:\
   C:\Program Files\Epic Games\UE\_5.3\Engine\Plugins\VirtualProduction\RemoteControlWebInterface\WebApp
2. Navigate to the built folder, go into Windows\Engine\Plugins\
   By default, there is only a folder called Runtime in there.
3. Create a new folder here called "**VirtualProduction"**\
   &#xNAN;**\*Make sure to spell it exactly like VirtualProduction with caps and no space in between.**
4. Inside VirtualProduction, create another folder called "**RemoteControlWebInterface**"\
   \&#xNAN;**\*Make sure to spell it exactly like RemoteControlWebInterface with caps and no spaces in between.**
5. **Paste** the **WebApp** folder here.
6. Check and make sure your paths and folders look correct, if done correctly it should look like this:

<figure><img src="../../../.gitbook/assets/image (206).png" alt=""><figcaption></figcaption></figure>

## Change Project Name

To change the project name (what shows up when you open the Task Manager), you can go to the DefaultGame.ini file and rename the "ProjectName" to what you want.

<figure><img src="../../../.gitbook/assets/image (410).png" alt=""><figcaption></figcaption></figure>

## Working with Sequencer

To start an animation sequence at the start, and to have it loop 999 times, set up your Level Blueprint like this:<br>

<figure><img src="../../../.gitbook/assets/image (75) (1).png" alt=""><figcaption></figcaption></figure>

!!! info

```
To break out the settings, right-click on the Settings pin and select "Split Struct Pin".![](<../../assets/image (186).png>)<br>
```

## Change Levels

In order to be able to change levels with Command Line Arguments, you will need to make sure you package your game with the levels you need to be able to load.

<figure><img src="../../../.gitbook/assets/image (429).png" alt=""><figcaption></figcaption></figure>

Then to open your map, you need to know the path that you put here, and paste it exactly as it is after the ...exe, with no "-". For example, it should look like this:<br>

<figure><img src="../../../.gitbook/assets/image (430).png" alt=""><figcaption></figcaption></figure>

If you want to add any command line arguments, they would go after the map path. For example, this is how the whole path might look, notice the spaces.

"C:\Users\Windows\LightSail.exe" /Game/StarterContent/Maps/Minimal\_Default -RenderOffscreen
