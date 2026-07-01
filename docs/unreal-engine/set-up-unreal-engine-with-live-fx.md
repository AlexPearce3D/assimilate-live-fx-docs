# Set up Unreal Engine with Live FX

!!! info "Official reference"

    For the official Unreal Live Link context, see [Live Links and Camera Tracking](../official-reference/live-links-and-camera-tracking.md).

## Overview

**Live FX works with Unreal Engine** in various ways, but here is the basic overview:

* Live FX takes in **Camera Tracking data.**
* Live FX forwards tracking information to Unreal Engine and **moves the Virtual Camera.**
* Unreal Engine **Texture Share SDK** is used to share the image from UE to Live FX.
* Live FX then uses the image with **LED and Greenscreen workflows.**

Live FX implements camera tracking directly and **forwards it to Unreal Engine**, which means that even if your camera tracking solution doesn't have their own Unreal Engine plugin, or if it is outdated, it will still work as long as it is supported in Live FX.

You can also leverage [Unreal Engine's Web Remote Control](unreal-web-remote-control-optional.md) to make changes to your unreal scene from other computers or tablets.

!!! warning

    Make sure to follow each step as you go along.


## 1. Required Setup

Currently, you must be on a **Windows machine** and use **Unreal Engine 5.3** for Live FX to work properly. There is a workaround for earlier versions of Unreal, make sure to [contact us and let us know](mailto:support@assimilate.com) if you need it.

***

## 2. Download and install Live FX Plugin for Unreal Engine Plugin

Download and Install the Live FX Plugin for UE.<br>

1. Download the latest **Live FX Unreal Engine Plugin** here:  
   [https://www.assimilatesupport.com/akb/Download51050.aspx](https://www.assimilatesupport.com/akb/Download51050.aspx)
2. **Unzip** and place the whole Plug-in folder into your **Project Plugins folder** (recommended) or Engine Plugins folder.
3. If your project does not have a Plugins folder, you can create one.   
   **Make sure to capitalize P and spell it “Plugins”.**  
     
   Your folder structure should look like this:  
   ![](https://lh7-us.googleusercontent.com/JYbVl1SrdVY_BNKSpvg_PBPUY3-Q-ARdV5YWKlLY9RupX6Nt5nrMKI_TQQd996o0SgWWx43BA4QXE7HD7RWyRO1aRMU1VKFLVn_-mU9A4_2Hk8zANQZR0-YZmUSXRV8YVTT00JiumOS2F-HsRF2clTqWuQ=s2048)

## 3. Enable Plugins in UE

1. Go to Plugins and search for Live FX, if it’s not enabled, enable the plugin.

<figure><img src="https://lh7-us.googleusercontent.com/__L_E6gEZuTetx9E2P-kJBiFzWWcp6r1Hkt0ELVMPAcRZfIJN852TK_10UFlDo150EUjTD_-rjgupAVp75RiBFP7dfqUOrNR4-SdFgm0TVK784DhYRZr-4pLwbpsMDWvtLjJ_tYWynuSue9uL05rrlQF3g=s2048" alt=""><figcaption></figcaption></figure>

2. Go to Plugins and search for **Texture Share**, enable the plugin (built-in).

<figure><img src="https://lh7-us.googleusercontent.com/Ocq84zDMNk-caK26Jmr63y7UYEqQDWkkSdBPV5ZLLOtP1jvfCQ1lnATgfzSjiAAYg3uSoGWWbCza1ij7HXL3Ym8o012hJ2FFJaj7UPrflfTvYG3TmJ8DYcyIILNMX-W5htuKmPAxnYtfNFcGnWrKwHrvqg=s2048" alt=""><figcaption></figcaption></figure>

3. You can enable **Web Remote Control** now if you know you are going to use it later (optional).

<figure><img src="https://lh7-us.googleusercontent.com/1tql0oM9BY-OobbmdU-k6Zd7nZh1BLNuNSjpY_dTCKBKmrE-z8O3YKjun-G9Lycgzjec7F4VlplQjQ5e_SPMqqi0NH2UvBc86pjwh4yfytpxWFacZuq-jyywsFzmEvjmamTl1OOsiGvCPI1ahEcEVXunjw=s2048" alt=""><figcaption></figcaption></figure>

4. After enabling your plugins, **restart Unreal Engine**.

## 4. Enable Live Link

1. Go to **`Window>Virtual Production`** and open the Live Link window.

You can also click on Window and just start searching for Live Link.

<figure><img src="https://lh7-us.googleusercontent.com/uKZPrCliRqQiwhA3E_OSEpOe8KZ70cblKWJgaV9SzfZ4qZVLGKIxMWi15I0BEsh47R7goPlu1G6gDnFZD06oAx6cTnhBvtAmz5-uaanHbCL4OIV16Nb30vFQ5bxTj4ugUowCUNW0GIU0d0XF-_c1xsNapA=s2048" alt="" width="375"><figcaption></figcaption></figure>

2.  In the Live Link Window, Click on Source, and go down to **LiveFX LiveLink.**  
    You can leave the settings by default if using the same computer and press Ok.

    <figure><img src="https://lh7-us.googleusercontent.com/OiUh1gp0ctOGx7CsyUP2ymSre0ulkTIxa8zk4bN0M-UNb5VMHVt4bDbIfyBh3MQGLJ4blTArwRQ9hi2go477pPVgXzFAcPniUn3GgYdEvB8G3YKEIQASlv22tNeE7J6mYfG6rFqiHz0WU_j0DYMQTSoLtw=s2048" alt=""><figcaption></figcaption></figure>

    :bulb:If you want to be able to trigger Take Recorder from Unreal, make sure to select Auto Record here. Otherwise, you can leave it unchecked.  
      
    If you haven’t set up Live FX properly yet, then you will likely see a yellow dot, and you may see the message “Can’t Evaluate frame for Live FX”. <br>

    This can be because either Assimilate is not on, or it’s not set up correctly.

      
    If you have set up Live FX, make sure that in the Camera tab, the camera is set to “Active”.



    <figure><img src="https://lh7-us.googleusercontent.com/9_dcL1sRaUcTvyLzLn1DPGZoLtnPRS3VbphYxjdx08hX0k81Nta0Nv4G-zcFvTTjuCZAh3EN6njk4HT5kfFsbson9fxLDXeYdixpgpKfKrSmA9Z20tDL-vXIukfcej4FE85RDVEXlMQWhPq4gNAAzaWO5A=s2048" alt=""><figcaption><p>Notice the Yellow Dot, which indicates it's not set up correctly yet.</p></figcaption></figure>



## 5. Save Live Link as Preset (Optional)

It’s good practice to save your Preset.

1. Click on Presets.
2. Click on Save As Preset, and give it a name.

<figure><img src="https://lh7-us.googleusercontent.com/0W3T7QevLWzCdjFvdZyUftKjG7wtC5aWroaKvQqWflGsbny4a3RPXstQJG7MLu0R-eC4dnkPrSnY3-q7Ek2DY1AMnLZd0yRH-29B5JZ82B1lxTUB-yawPwsajZcjJl3xIzta7bynoa3RVhHPTrrjSXTTUQ=s2048" alt=""><figcaption></figcaption></figure>

3. Then in **`Edit>Project Settings`**

Search for Live Link Preset, select the “Default Live Link Preset”, and select the newly created preset.<br>

<figure><img src="https://lh7-us.googleusercontent.com/FxZS3OaFMgud1SDmzhSFWDT4LXqScrdhZ1gVjFRY6ouVxThen7ObAN37C0zseeXEiPc4n83alMJaeKRjAtIkUoGlNqaoM-_TuLyl0myun-V40pelNxefHeNEH79Mptgh3K7xMexxsE2cKiboZL28qNJ-Iw=s2048" alt=""><figcaption></figcaption></figure>

## 6. Add Camera in Unreal Engine

Now let's set up the Camera in Unreal Engine.

1. Go to the Add Menu <img src="../../assets/image (254).png" alt="" data-size="line">
2. Add a **`Basic>Actor`**
3. Rename this actor to something like  
   “00\_CamOffset”.

!!! info

    We will attach a camera with camera tracking, and this empty actor will allow us to move the camera without affecting tracking.


<figure><img src="https://lh7-us.googleusercontent.com/jZ18zHi06nWPIKLtHx1jwhwO7NJ6NtMkmJr6bFFyZpL_VrSoW4FFR1mRDkLmAwlCdLnSs7a7kygFAtjDKFz6eb_wrjtOaxdgfZ6wfbTmX28WX-2ghHttwY0DQes0FmhtVXRdflrXyLozpRCfWuTS7aiYCg=s2048" alt=""><figcaption></figcaption></figure>

4. Go to the Add Menu <img src="../../assets/image (255).png" alt="" data-size="line">
5. Add a **`Cinematic>Cine Camera Actor`**.
6. Give it a name, like “00\_LiveFXCam”

!!! info

    I use the prefix 00\_ so that it **shows up at the top**.


7.  In the Outliner, **Click and drag the Cine camera onto the Empty Actor**, so that the **actor becomes the parent.**   
    The camera should be **indented** and look like this if done correctly:<br>

    <figure><img src="https://lh7-us.googleusercontent.com/9doo67bOIwDEcEUgTRMrv75LfiDCoNA6d9HLD-T3xWz1wly_aHBBmvsRQ5bPjQyI4Ia0zSpiqPkQPb1O0hoMlSO8X_xAF4DjnIXvoSNxT9d3WjpLZCANwD_b7dYDg5i92RhURlC3_zGCx62m1LsOPT9jhg=s2048" alt="" width="375"><figcaption><p>Make sure the Camera is indented under the Actor</p></figcaption></figure>
8.  With the LiveFXCam selected, click on the **“Add Component”** button.  
    Search for “Live FX” and attach the **“Live FX Runtime Camera”**.<br>

    <figure><img src="https://lh7-us.googleusercontent.com/_T1D8qiUkSReNy8hj7O6xl-tZizekUt4ICFBcbdVnzPqIuMLOzb9cBvegLuCPid1CxJbWthoVaR-awBMFsSCfwaLgycnghJsQrx9G-Y3w4ybWY3VfVboZPkUN-f15wpBnxJD_-9L3PTtZHCSmy5GsViTEg=s2048" alt=""><figcaption><p>Add the <strong>Live FX Runtime Camera</strong> component to the Camera</p></figcaption></figure>
9.  With the LiveFXCam selected, click on the **“Add Component”** button.

    Search for “Live Link” and attach the **“Live Link Controller”** component.



    <figure><img src="https://lh7-us.googleusercontent.com/6BYqC8r9FUxrfGlCXtv2uYB6kRTN0r6bK62ttzUGl0lWUkNmLuVldmD5rJ3SiZbGHo2DDJ_seVUXW-f_ZvW_2mp0jkJ4q7azU_zm4c0hL-i4-r7KPOrrI9rGp0P4MR27woWzUBQQVGqU3f3qc67iuzPzKA=s2048" alt=""><figcaption><p>Add the <strong>Live Link Controller</strong> component to the Camera</p></figcaption></figure>
10. With the **Live Link ComponentController selected,**

    Click on the dropdown for the Subject Representation, and select the **LiveFX - Camera**.



    <figure><img src="https://lh7-us.googleusercontent.com/wgoTY1Bp86GVb-mBUvCRLlB106XOouaG72i2t4NXeQtPIglYXBYB8RSt68MOQ19PFa13QtNKZGEIZ2uANZUBY3oJWJal-2FuGtjpmYxAnLhygZuqXMRH5pSz5gaOYHLZCk7jQjsW9sSkwHQK1jhtHiW2yg=s2048" alt=""><figcaption></figcaption></figure>



!!! info

    When you press play if the selected camera is not playing in the viewport, you may want to set up manually.


Optionally, instead of adding the "LiveFX\_RuntimeCamera as a component to the camera, you can add it in the level blueprint, and by doing so, also allow for things like switching cameras dynamically.

You would set your blueprint up like this, drag your camera from the outliner into the level blueprint to get a reference of it, and replace the "0\_Zeiss\_CineCameraActor" reference with your camera:<br>

<figure><img src="../../assets/image (81).png" alt=""><figcaption></figcaption></figure>

A copy of this blueprint is provided here:

[https://blueprintue.com/blueprint/dhaupwq4/](https://blueprintue.com/blueprint/dhaupwq4/)

## 7. Set up Texture Share in Live FX

There are a few ways to work with the **Texture Share** image that comes from Unreal Engine.

If you are using a Camera Projection method with an **Inner Frustum**, you can choose the **Projection Setup** and then under Project Media, choose **`Live Capture > Unreal Texture Share,`** then you can follow your normal workflow.

<figure><img src="../../assets/image (246).png" alt=""><figcaption></figcaption></figure>

For small walls, sometimes this is not necessary and it's preferred to not have an inner frustum at all. Here is one method to achieve that. 

1.  **Create a new project** and set the resolution as needed, in my case I just use 1920x1080.

    In the construct, go to the **Filler dropdown** and add black or whichever you want.<br>

    <figure><img src="../../assets/image (247).png" alt=""><figcaption></figcaption></figure>
2.  With the new Layer selected, on the bottom left, go to **“Plug-Ins”.**<br>



    <figure><img src="../../assets/image (248).png" alt=""><figcaption></figcaption></figure>


3.  Select **“Unreal Texture Share”** and **Apply on Layer.**<br>

    <figure><img src="https://lh7-us.googleusercontent.com/gwfzsj_EQbq2L_h1Z7w7RffTaF3NOB47EKFU-4Kt2gA9goL69zRPepwvp8UCByAqhXbpOREdp9wu_lOPIBdNlCHFEr2h2Pf-vUD4a2uOU42i0KY-lkA9x-nLT2_4QJfXai_yE6AsUrgd7QzIYL6CMuSkXw=s2048" alt=""><figcaption></figcaption></figure>

## 8. Unreal Engine Live Link in Live FX

1.  Click on the **Live FX** menu, then click on the **Live Links** Menu.<br>

    <figure><img src="../../assets/image (249).png" alt=""><figcaption></figcaption></figure>


2.  Click on **Unreal Live Link.**  
    **Press On.**

    (Optional) Click Broadcast.

    **Click Connect.**<br>

    <figure><img src="../../assets/image (250).png" alt=""><figcaption></figcaption></figure>

    \*IP can be 127.0.0.1 if using the local machine

    \*\*If you see numbers moving at the bottom, this is set up correctly.
3.  If using **camera tracking**, make sure your tracking is set up correctly and that you **press “Apply”** so that it applies to your camera.<br>

    <figure><img src="../../assets/image (251).png" alt=""><figcaption></figcaption></figure>


4.  If **not** using camera tracking, go to the **Camera tab and press “Active”**

    You can manually move the camera in UE, by changing the values.<br>

    <figure><img src="../../assets/image (252).png" alt=""><figcaption></figcaption></figure>

## 9. Press Play in Unreal Engine

1. Go back to Unreal.   
   Next to the Play button, click the hamburger button and select **“New Editor Window (PIE)”**,
2.  **Maximize** this new window so it takes up the entire screen.  
      
    :information\_source: The size of the New Editor Window will be the resolution in Live FX, so if it is not maximized, it will be smaller than your monitor. For example, if you resize the window so that it is the left half of your 1920x1080 screen, the resolution would be 960x1080 (960=1920/2). <br>

    <figure><img src="../../assets/image (253).png" alt=""><figcaption></figcaption></figure>


3.  Go back to Live FX (The keyboard shortcut is **Alt+Tab**).   
    If all is set up, you should see the image!<br>

    If you see stretching pixels on the side, that means your comp is higher resolution than the Window you opened. <br>

    Try going to full screen with the UE scene and Alt+Tab to go back and check Assimilate.  
      
    You can also [change your composition resolution](../getting-started/the-basics/change-shot-framerate-and-resolution.md) to be smaller to match your window size. <br>

    <figure><img src="https://lh7-us.googleusercontent.com/XtdPgu-X3SsWwuhhwUJHL2L4vHdHso3tXctGvM3Ykas2f3NI8Onzqnl1Z5RP9wfwhavjh4j57kTDAIpXyRmgncncAvFUldvn996weCef_opjyzOQvwGRAWIqB2odEY8_iBvlZp8AqolhppyN5reqM1P59Q=s2048" alt=""><figcaption><p>Notice the pixel stretching. This is when the window is not in full screen mode.</p></figcaption></figure>


4.  If you are using camera tracking, try physically **moving your camera**.<br>

    If you don't have camera tracking set up, try changing the pan from the **camera menu.**  
      
    If all is set up correctly, you should see the scene moving in Unreal Engine.  
    

    <figure><img src="https://lh7-us.googleusercontent.com/EMpT1w02peSF2c6PP9Ic7K8QdZADJEQva-R6XDBZ7oCAVJrKfvC5SvbYmKbEEj9pZ30ep5QhHGAehDqD82tRKqAcd53U379W71uORKdoC7jBPFxqJ7ZZ606lRAiQGvvs0rfplu6KuOvtAGiOAgeb4WBEaQ=s2048" alt=""><figcaption><p>Our scene looks and behaves as expected with Camera Tracking. </p></figcaption></figure>
