# Simple Video Playback

## Overview

In this example, we will add some simple 2d video plates to play on an LED wall with a Logo overlaid on top.

We will not worry about camera tracking or projection mapping.

We will assume your system is already connected and mapped to the LED wall.

You can also just use an external monitor to follow along.

<figure><img src="../../assets/image (388).png" alt=""><figcaption></figcaption></figure>

## 1. Download and Import Footage

You can use your own footage, but here is a link to download some sample footage for you to download to follow along:  
  
[**Download ProRes (10 Gb)**](https://www.dropbox.com/scl/fo/i643swgfabbftprczuix2/h?rlkey=a372vlhva2j68qc9wlfuy3v9k\&dl=0)  
[**Download H265 (237 Mb)**](https://www.dropbox.com/scl/fo/vk1tz67gmirqjn212ztj7/h?rlkey=b3bspoysjg1h1b9o0tp7uks1g\&dl=0)

## 2. Create a new project

Let's create a new project.

<figure><img src="../../assets/image (361).png" alt=""><figcaption></figcaption></figure>

For the resolution and frame rate, let's use the LED wall (or computer Monitor's) resolution. For example, if our footage is 3840x1260, but our LED wall is 1920x1080, we'll use 1920x1080.

<figure><img src="../../assets/image (362).png" alt=""><figcaption></figcaption></figure>

You can always [change your project settings later](../getting-started/the-basics/project-settings.md). You can also change your timeline settings inside the project.

## 3. Import Media and Enter Shot

1.  Click on Import Clips.

    <figure><img src="../../assets/image (365).png" alt=""><figcaption></figcaption></figure>


2.  Navigate to where you downloaded the demo files, click on the first file, then **hold down shift and click to the last file to select them all.** <br>

    <figure><img src="../../assets/image (366).png" alt=""><figcaption></figcaption></figure>


3.  Don't change the format.  
    If your source footage is different in resolution, frame rate, or aspect ratio than your timeline, Live FX will prompt you to see if you want to change the timeline to match your source footage. In our case, we want our timeline to stay what we specified, the resolution of our LED wall, so let's click **No**.<br>

    <figure><img src="../../assets/image (367).png" alt=""><figcaption></figcaption></figure>


4. Drop the clips on the timeline.   
     
   The clips will stick to your mouse pointer to allow you to position the clips where you want them. Hover over Slot 0 and left-click to drop them on there. <br>
5.  Choose Timeline Player Mode.  
      
    There are two major Player Modes in Live FX: **Single Shot and Timeline**.  
    **Single Shot** plays one clip on the timeline, and **Timeline** plays all of the clips on the timeline.  
      
    One of the big limitations of Single Shot mode, is that you cannot change the resolution or the shot.   
      
    So in our example, even though our wall is 1920x1080, if we enter one of our shots in Single Shot mode, the resolution will be 3840x2160, which is not what we want.   
      
    So let's go to the Player Mode and switch to **Timeline**, near the bottom left of the Construct screen. <br>

    <figure><img src="../../assets/image (368).png" alt=""><figcaption></figcaption></figure>


6.  Enter the first shot on the timeline.   
      
    You can either double-click on the shot, or you can click on the Live FX tab at the bottom middle of the screen.<br>

    <figure><img src="../../assets/image (369).png" alt=""><figcaption></figcaption></figure>



## 4. Scale the Shot

**We're going to make many adjustments on the first shot**, and then copy and paste those to all the others, so make sure you stop playback (shortcut is Enter), and make sure your play head is somewhere in the first shot.

1.  Scale the shot.  
      
    Go to the Framing Menu from the bottom left, then either scale down manually or use **Fit Width.** In this example, the scaling is exactly 50%.   
      
    If you have a different aspect ratio from your footage, you may need to manually scale your image so that there are no black bars on either side.  
    <br>

    <figure><img src="../../assets/image (374).png" alt=""><figcaption></figcaption></figure>

    <figure><img src="../../assets/image (375).png" alt=""><figcaption></figcaption></figure>



## 5. Add a LUT

Now that our shot is the correct scale, **add a LUT**.   
  
1\. Create a new layer and re-name it LUT.  
  
2\. With the LUT layer selected, navigate to the LUT menu at the bottom left.   
  
3\. Press Load and navigate to the file in your downloads "**AppleLogToRec709-v1.0.cube**"<br>

<figure><img src="../../assets/image (371).png" alt=""><figcaption></figcaption></figure>

## 6. Add a Logo

Let's add a logo on top of the footage.

Inside the folder you downloaded, there is a file called "**LSVR Logo**".

1. Right-click in the shot and click on **Import Clip**, then navigate to the Logo.
2. It comes in very big, and there are many ways to resize it, but in this case, let's **hold down the shift key and drag** one of the edges to scale it down.   
     
   Holding down the shift key makes sure it scales uniformly in both the x and the y.<br>
3.  Now click and drag the Logo so that it's in the bottom left corner.  
      
    You can also go to the Canvas Menu to make additional changes or reset anything you don't want.  
    <br>

    <figure><img src="../../assets/image (376).png" alt=""><figcaption></figcaption></figure>

## 7. Copy and Paste Forward

Make any other adjustments that you might want to make globally, and when you are finished follow along with the steps, making sure to follow them exactly.<br>

1.  While in the first shot, click on the Copy button on the bottom right.   
    <br>

    <figure><img src="../../assets/image (377).png" alt=""><figcaption></figcaption></figure>


2. Go to the second clip in the timeline, and press Paste.
3.  Press Paste FWD:arrow\_right:  
    <br>

    <figure><img src="../../assets/image (379).png" alt=""><figcaption></figcaption></figure>


4.  The Paste FWD button becomes a confirmation box, **click on Yes**.<br>

    <figure><img src="../../assets/image (380).png" alt=""><figcaption></figcaption></figure>


5.  There's one more confirmation, warning that you are going to effect the entire timeline. **Click OK.**<br>

    <figure><img src="../../assets/image (381).png" alt=""><figcaption></figcaption></figure>

## 8. Arranging the Timeline

Now let's get a little familiar with the timeline.

1.  Click on Construct to get back out of the timeline. <br>

    <figure><img src="../../assets/image (382).png" alt=""><figcaption></figcaption></figure>


2.  You may have noticed that when we imported our clips, we accidentally imported the logo as a shot. Let's use the scroll bar and go to the right on our timeline, select the Logo, and press **Delete Selected.** <br>

    <figure><img src="../../assets/image (383).png" alt=""><figcaption></figcaption></figure>


3.  Let's switch our first and second shots. We can do that by clicking and dragging the first shot and dropping it above the second shot temporarily, then dragging the second shot left to the first slot.

    <figure><img src="../../assets/image (385).png" alt=""><figcaption></figcaption></figure>



## 9. Change shot duration

1. Double-click to go into the Shot IMG\_3218, which should be in the second slot now.
2. Click on Source, which will change from showing the entire timeline, to just showing the source timeline.
3. Click on the Live FX Menu
4.  Use the Timeline and the Current Frame Position to determine what your In and Out should be, then enter those numbers under the **Shot Length** section.<br>

    <figure><img src="../../assets/image (387).png" alt=""><figcaption></figcaption></figure>
