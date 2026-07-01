# Projection Mapping with Cuebric Files

You can use the .2p5d files directly in Live FX.

Here are some files to download and follow along:  
[https://www.dropbox.com/scl/fo/dcromk5m6i0vbg1ts1do6/h?rlkey=b5uou9q0c8bvq4e9ip2dhe0uz\&dl=0](https://www.dropbox.com/scl/fo/dcromk5m6i0vbg1ts1do6/h?rlkey=b5uou9q0c8bvq4e9ip2dhe0uz\&dl=0)

These include two .2p5d files, as well as those same files, unzipped.

## Using the Projection Setup

1. Open the Projection Setup menu
2. For Project Media, browse to the .2p5d file.
3. Under Media Type, choose 2.5d
4.  For projection, we recommend the Planar Projection.<br>

    <figure><img src="../../assets/image (463).png" alt=""><figcaption></figcaption></figure>


5.  Make sure that the resolution of your shot is the same as the resolution of your Wall. For example, in my case, it's 4000x1600, but I had accidentally set my timeline to be 1920x1080, so I checked when I entered my shot, and then went back to Single Shot so that it would enter the shot at the correct resolution. <br>

    <figure><img src="../../assets/image (464).png" alt=""><figcaption></figcaption></figure>



## Working with Projection Mapping

It helps to see what is happening by going to the Live FX menu, Stage Manager. Here you can see the position of the camera, the position of the LED wall, and the position of each layer in Z space.

Projection mapping 2.5d workflows work similarly to non-projection mapping, but in the viewport, it will look the opposite of what you would imagine should be happening; the closest layers will move less than the further layers.

!!! info

    You should look at your physical wall or through the stage manager to check if the parallax looks correct and if everything is working properly. Looking at the image in the editor can be deceiving because it's based on what the camera would be seeing through the projection.


<figure><img src="../../assets/image (465).png" alt=""><figcaption><p>The Yellow planes here are the various layers set to different depths. </p></figcaption></figure>

When you enter your shot, you will need to adjust a few things. You might notice that it's black or that it doesn't fill your entire wall, for example. There are two main ways of adjusting the size and depth of your individual layers. These are the Camera position and Plane->Wall Projection Settings for each layer.

<figure><img src="../../assets/image (466).png" alt=""><figcaption><p>How my shot looked when i first entered. The content should fill all the way to the white thin border.</p></figcaption></figure>

Move your camera to your filming position. I moved my camera back, and already it's closer to what i need it to be, notice in the screenshot below that as I moved my Z position back, it started filling the frame better.

<figure><img src="../../assets/image (467).png" alt=""><figcaption></figcaption></figure>

With your camera in the correct position, it's time to adjust the individual layers to work better for us. First, I will rename my images, so I know what they are.

Image\_5 was just a cloud image for the ceiling, which I don't have so I'll just delete it.

Select the sky layer, and open the Plane->Wall menu on the bottom left.

The two main things we will need to adjust throughout this process are the **Trans Z** and the **Width/Height** (linked).

**Trans Z** pushes the layer further away from the camera the lower the number goes, or closer to the camera the higher the number goes.

!!! info

    If you do not see the image, you may be actually behind your camera, adjust your layers back or move the Z position of your camera back to line it up.


**Width/Height** scales the image up or down.

Go through each layer and change the Width/Height, Trans Z, and position them in X,Y space where you want them.

<figure><img src="../../assets/image (468).png" alt=""><figcaption></figcaption></figure>
