# Setting up an LED Wall

## Overview

There are many different configurations and considerations when setting up LED walls.&#x20;

## 1. Inspect the System&#x20;

First, it's good to gather as much information about your wall and your computer settings, and write it all down or note it as you go along.

1. LED Processor Brand and LED Tile brand
2. How the wall is mapped in the processor(s)
3. Total Wall Resolution
4. Size of LED panels (normally .5 meters)
5. Number of Rows/Panels
6. Tracking system used
7. World Origin (Or Tracking Origin)
8. Basic understanding of how everything is wired ( One Displayport out from one machine? or SDI out from multiple machines?)
9. Is there an existing OBJ file for the wall? If so, are the UVs unwrapped properly and normals facing the correct way?

## 2. Nvidia Mosaic or SDI Out&#x20;

{% hint style="info" %}
If you only have one LED Processor that drives your wall(s), then you can skip this section.&#x20;
{% endhint %}

If your system architecture requires two or more LED processors, then you set up your system to either use Nvidia Mosaic or take the outputs directly from an SDI capture card.&#x20;

There are pros and cons to both methods, but generally, Nvidia Mosaic is the preferred method because SDI out will always have a few frames of delay, and directly out of your GPU will have no delay. For you to use Nvidia Mosaic, you must have a Quadro line card, like the Nvidia RTX A6000.&#x20;

[Go to this link for instructions to set up Nvidia Mosaic.](set-up-nvidia-mosaic.md)

When going out the GPU - with or without Nvidia Mosaic setup - make sure you have Vertical Sync enabled in Live FX. You can find the corresponding setting by going to the Live FX Tab ==> Settings menu (hotkey F5) under the Play Options.&#x20;

If you go out the GPU, ensure that no Video-IO devices are enabled because if they are, then LFX will sync playback on the first Video-IO output rather than the Dual Head VSync. If you do need Video-IO, then explicitly set the Sync-dropdown (in the same menu as the VSync) to "Timer" rather than "Automatic".

## 3. Setup LED Wall

1.  From the Construct, open the Projection Setup<br>

    <figure><img src="../../.gitbook/assets/image (175).png" alt=""><figcaption></figcaption></figure>
2.  Click on Edit.<br>

    <figure><img src="../../.gitbook/assets/image (176).png" alt=""><figcaption></figcaption></figure>


3.  If there is not a wall, Click Add, to add a new wall.<br>

    <figure><img src="../../.gitbook/assets/image (177).png" alt=""><figcaption></figcaption></figure>


4.  If there is no wall here, press **Create**.<br>

    <figure><img src="../../.gitbook/assets/image (178).png" alt=""><figcaption></figcaption></figure>
5.  Fill in the Wall details, for example, how many LED panels for your Columns and Rows, and the tile size (many LED panels are .5m x .5m Tile Size). Also fill in the Tile Resolution.&#x20;

    <figure><img src="../../.gitbook/assets/image (179).png" alt=""><figcaption></figcaption></figure>

    If you filled in all the information correctly, the Wall Size and the Resolution should match what your total wall is.&#x20;

    <figure><img src="../../.gitbook/assets/image (180).png" alt=""><figcaption></figcaption></figure>
6.  Make sure you fill in your Wall Curvature as well. If you don't know your wall curvature, but instead know your tile degrees, you can use the free tool [ObjGen](https://objgen.makkbe.net/) to calculate the Wall Curvature, by entering your Tile Angle and looking at the Curvature. You can also just use this tool to create an OBJ instead if you want. <br>

    <figure><img src="../../.gitbook/assets/image (173).png" alt=""><figcaption></figcaption></figure>
7. Create as many walls and ceilings as you need to.&#x20;
8.  Click on the **Mapper** tab, then click on **Map.** \
    To map your setup correctly, it's best to have your LED processor mapping up on a monitor nearby, and you need to match however the LED processor is mapped (or you could set up Live FX and then re-map in the LED processor). \
    &#x20;\
    You can click and drag around the Yellow box, which represents the mapping.  \
    \
    Notice in my example, that the wall is higher resolution than my output, so if this were a real example, I would need to scale down so the wall fits into my map.  \
    \
    You can use the **Preview** button to see the mapping on the wall. \
    \
    :bulb:One tip is you can click into Offset X and then use the arrow keys to move one pixel at a time.<br>

    <figure><img src="../../.gitbook/assets/image (181).png" alt=""><figcaption></figcaption></figure>


9.  Make sure the wall you want to use is set to **ACTIVE.** You can also use the <img src="../../.gitbook/assets/image (184).png" alt="" data-size="line">Eyeball icon to Preview the footage on the wall (once you are in a shot). \
    &#x20;

    <figure><img src="../../.gitbook/assets/image (182).png" alt=""><figcaption></figcaption></figure>

## 4. Projection Setup

Once you've set up your wall, you can use the Projection Setup to set up your shots.&#x20;

<figure><img src="../../.gitbook/assets/image (185).png" alt=""><figcaption></figcaption></figure>









