# 🕙 Dealing with Delay

## Overview

Delay happens for many different reasons, and you have many different types of delay, from Camera Tracking delay to Unreal Engine delay. Sometimes you need to add a delay in order for everything to sync up.  
  
Let's look a a few examples of **when and how to add delay**.

!!! info

    When possible, you should use Timecode Sync and Genlock.


## 1. Delay Unreal Engine Content (Inner Frustum)

If you move your camera and the inner frustum moves first and the content inside your frustum moves later, you need to dial in the delay to match.

1. Click the animate tab. 
2. Select x, y, z, Pan, Tilt, Roll, and then set the delay of the first one to 4 (as a starting point).   
     
   All the rest should automatically be delayed by the same amount.

[This is also covered in the Camera Tracking section of this guide.](../camera-tracking/how-to-delay-the-inner-frustum.md)

<figure><img src="https://lh7-us.googleusercontent.com/HY4WUbQrx-Orrz9BGDWXokQH2pNKKrPh8LJ1P3ukNwZ_hi_MwCOjOYIYebGh8fb9DowO_y_p4y4G9BFDg64ZFQK53vdkLjwbFnXqIEKmizK6TrD7M7FrLirQQqSt3J3b0E07o3_oOdpn8qAC__HAPH0" alt=""><figcaption></figcaption></figure>

## 2. Delay Camera Feed for Greenscreen

One reason you may need to delay your camera feed is if you are using a Green Screen workflow and your **camera feed is faster than the Unreal Engine scene** that is behind your talent.

1.  Click on your primaries layer at the top left of your screen so that it is the active layer (Orange).<br>

    <figure><img src="../assets/image (238).png" alt=""><figcaption></figcaption></figure>


2.  Under the "**Video Capture**" Menu, you will find the **Delay** as well as the Auto TC Sync button.<br>

    <figure><img src="../assets/image (239).png" alt=""><figcaption></figcaption></figure>


3. **Adjust the Delay** as needed. It can be helpful to **whip pan** your camera quickly to see how much to delay your camera.

## 3. Delay Camera Tracking

There may be times when you need to delay your camera tracking.

1. Go to **`Live FX Menu>Live Links`**
2. Click on the active camera tracker, in this example, Ncam.
3.  Increase the delay as needed. <br>

    <figure><img src="../assets/image (240).png" alt=""><figcaption></figcaption></figure>



## 4. Delay sACN for Lighting

Oftentimes, lighting data through the sACN protocol will travel faster than the content from the LED wall and you may need to delay the sACN signal.

1. Go to the Stage Lights workspace at the bottom.
2. Click on Protocols.
3. Click on the sACN tab.
4.  Add Signal Delay (in milliseconds).

    <figure><img src="../assets/image (356).png" alt=""><figcaption></figcaption></figure>

