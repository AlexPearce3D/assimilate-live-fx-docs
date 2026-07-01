# Non-Projection Mapping with Cuebric

Here is a workflow if you are using Green Screen or perhaps just have a flat wall and want to skip projection mapping for one reason or another.

You can use .2p5d files directly in Live FX.

Here are some files to download and follow along:  
[https://www.dropbox.com/scl/fo/dcromk5m6i0vbg1ts1do6/h?rlkey=b5uou9q0c8bvq4e9ip2dhe0uz\&dl=0](https://www.dropbox.com/scl/fo/dcromk5m6i0vbg1ts1do6/h?rlkey=b5uou9q0c8bvq4e9ip2dhe0uz\&dl=0)

These include two .2p5d files, as well as those same files, unzipped.

## Set up the .2p5d shot

1. Create a new timeline, and set your timeline resolution to whatever you want your final resolution to be, in this example, I'll use 1920x1080.
2.  From the Construct, click on the Import Clips button in the middle of the screen and navigate to the .2p5d file.<br>

    <figure><img src="../../assets/image (469).png" alt=""><figcaption></figcaption></figure>


3.  Click on the Reload Project at the bottom left of the construct. **If you don't do this, your media may not load correctly and when you enter your shot, it may just be black.** <br>

    <figure><img src="../../assets/image (470).png" alt=""><figcaption></figcaption></figure>
4. Enter the shot by double-clicking the shot. [Change the Shot Length](../getting-started/the-basics/change-the-shot-length.md) if you want to.

## Rename the layers

Let's [rename the layers](../getting-started/the-basics/working-with-layers.md#rename-layers) so that instead of Image\_5, we know what we are working with.

## Working with the layers

It helps to visualize what is happening with the layers, to do that we can enter Dual View \[Shortcut D] and one of the views to be Perspective View \[Shortcut P]. You can toggle between these views by using the shortcuts.

I like to Unlink the views by clicking on Link on the right side so that it is grey. Now i can fit the image on the right side, and zoom out to see what is happening in our scene on the left.

Notice that Image\_1 is selected and the orange line corresponds to where that is in 3d space. If I were to move it in Trans Z we'd see it update here.

<figure><img src="../../assets/image (471).png" alt=""><figcaption></figcaption></figure>

The main ways to increase/decrease the parallax effect are by moving the images closer/further away from the camera in Z space and by moving the camera.

To move the individual layers, click on a layer, then click on the **Canvas Menu.**

As we change the Trans X, Y, Z, or Scale, we will see it updated in the Perspective view.

<figure><img src="../../assets/image (472).png" alt=""><figcaption></figcaption></figure>

If we move our camera on the X-axis right now, we can see the bottom of the Dome layer is floating, and the far background (Sky, Water, and Mountains) is moving way too much.

<figure><img src="../../assets/image (473).png" alt=""><figcaption></figcaption></figure>

If we think about real-life parallax, the sky and water are so far away we wouldn't notice any parallax by moving a few feet one way or the other and the mountains would just barely be noticeable, so let's try to create that effect.

1.  We need to change the camera Far clipping plane, otherwise, we'll move our layer back behind the clipping plane and it will just turn black. To do that, go to the Camera Tab, click on the Config tab, and change the Far distance to something very far, I'll set it to 10,000 for now. <br>

    <figure><img src="../../assets/image (474).png" alt=""><figcaption></figcaption></figure>
2.  Now let's move our Sky layer and Water layer very far back, I'll set -5000 on the Trans Z. Make sure Fit is enabled and/or scale it to fit the screen. <br>

    <figure><img src="../../assets/image (475).png" alt=""><figcaption></figcaption></figure>
3.  For the Mountains layer, move it back in Trans Z, check the camera, and repeat that until you are happy with the results. In my case, I found that -250 on Trans Z looks natural.<br>

    <figure><img src="../../assets/image (476).png" alt=""><figcaption></figcaption></figure>
4.  For the Dome layer, the parallax looks good, but the layer itself is floating above, so click on the layer and move it, or use the canvas menu Trans X and Trans Y to move it into a position that works.   
      
    **Tip** - With the layer selected, you can move your cursor right over one of the edges of the layer, hold Shift, and click and drag to scale the layer uniformly.<br>

    <figure><img src="../../assets/image (477).png" alt=""><figcaption></figcaption></figure>


5. Lastly, [defocus](README.md#defocus-and-color-grade-layers) and color each layer as needed and you are ready to shoot!

<figure><img src="../../assets/image (478).png" alt=""><figcaption></figcaption></figure>
