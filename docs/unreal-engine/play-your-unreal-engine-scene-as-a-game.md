# Play your Unreal Engine scene as a Game

## Overview

If you are using an LED workflow, you will want to run your Unreal Engine project as a game or [Package your project to a stand-alone .exe file.](how-to-package-an-unreal-engine-project-for-live-fx/)

The main reason you need to do this is so that you can render the viewport offscreen, as Live FX will read the texture share and show it in the Live FX viewport.

Rendering offscreen has some performance benefits but even if your computer can handle the scene without rendering offscreen, other artifacts can show up on LED walls or second monitors by rendering the viewport twice, and if you didn't set your project settings to not "Use less CPU when in background", it may also go very slow.

!!! warning

```
The path to your Unreal Engine project should be short, if not you may run into issues where you cannot put in all the command line variables you need to. Keeping folder and file names short or moving your project somewhere with a short path is the best practice.
```

## Create the shortcut

The first few times you do this process, it will seem confusing, but once you've done it a few times, it's not difficult.

!!! warning

```
Make sure you pay close attention to spelling, spaces, and quotation marks, it's easy to make a mistake in the written part of the text.
```

1.  Create a shortcut for Unreal Engine. It's default location is:\
    C:\Program Files\Epic Games\UE\_5.3\Engine\Binaries\Win64\UnrealEditor.exe

    You can create a shortcut here and move that shortcut wherever you want.

    Another way to create the shortcut is to go to the Epic Games Launcher, click on the dropdown menu of the version of the engine you want to use, and select **Create Shortcut**, which will place a shortcut on your desktop.

## Customize the shortcut

1.  Right-click on the shortcut and select **Properties**.<br>

    The target field has the path to the Unreal Engine .exe<br>
2. Find the location of the project you want to open and copy the full path. There are different ways to do it, but one way is to copy the path at the top, then add the full project name including ".uproject".<br>
3. In the target field of the shortcut, right after the .exe" add one space, one quotation mark then paste the Project location, followed by another quotation mark. In this example, this is how the full target line would read, with only one space between the engine path and the project path:\
   "C:\Program Files\Epic Games\UE\_5.3\Engine\Binaries\Win64\UnrealEditor.exe" "C:\Users\Demon\Documents\Unreal Projects\PackagingTests\PackagingTests.uproject"<br>
4. After the last quotation marks you can put in whatever [Command Line flags that you'd like.](how-to-package-an-unreal-engine-project-for-live-fx/command-line-arguments.md) You will at the very least need to use the -game and you will likely want to specify the Resolution with the ForceRes flag.<br>

-game -ForceRes -ResX=1920 -ResY=1080 -RCWebControlEnable -RCWebInterfaceEnable -t.maxfps = 23.976 -
