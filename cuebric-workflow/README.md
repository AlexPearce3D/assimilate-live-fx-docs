# ©️ Cuebric Workflow

## Overview

<figure><img src="../.gitbook/assets/image (128).png" alt=""><figcaption><p>Graphic showing the basic concept of 2.5d. </p></figcaption></figure>

The 2.5d concept is pretty simple, you have several 2d layers of pictures or videos as separate layers and you put them in various depths of your scene so that as you move your camera, they create a parallax effect, such that the foreground elements appear to move faster than the background elements.&#x20;

If done well, you can make 2d elements look like 3d.&#x20;

You can even combine some 3d elements with 2d elements as well, but this section will focus on 2d elements for now.&#x20;

## Cuebric

Cuebric is an AI generation tool that has specific segmentation toolsets to help separate layers for you and help make 2.5d workflows easier.&#x20;

According to their website, "[_Cuebric_](https://cuebric.com/) is the Generative _AI_ tool that is revolutionizing preproduction and production by allowing filmmakers to go From Concept To Camera™ in minutes."

Cuebric has its own file format, .2p5d (get it, it's sounding out **T**wo **P**oint **F**ive **D**). The format is not complex, it's essentially a zipped folder with images, depth maps and a JSON file to specify what the depths are supposed to be.

Here are some files to download and follow along:\
[https://www.dropbox.com/scl/fo/dcromk5m6i0vbg1ts1do6/h?rlkey=b5uou9q0c8bvq4e9ip2dhe0uz\&dl=0](https://www.dropbox.com/scl/fo/dcromk5m6i0vbg1ts1do6/h?rlkey=b5uou9q0c8bvq4e9ip2dhe0uz\&dl=0)

These include two .2p5d files, as well as those same files, unzipped.&#x20;

## Defocus and Color Grade Layers

One benefit to having separate layers for the foreground, middle ground, and background is that you can color grade and defocus the layers individually. You can defocus the far background and extreme foreground and get a more realistic-looking image. This is useful no matter which workflow you are using.

To defocus layers, select the layer you want to affect, go to the **Numeric tab,** and under Aperture, change the Defocus. I'll defocus the Sky, Water, Mountains and Rocks layers.

<figure><img src="../.gitbook/assets/image (142).png" alt=""><figcaption></figcaption></figure>

You could also use the Lens Blur plug-in to get more extreme results.&#x20;

Go to Plug-ins->Effects->Lens Blur and add on layer.

<figure><img src="../.gitbook/assets/image (143).png" alt=""><figcaption></figcaption></figure>

Make any adjustments you want here, and make sure to Blur Alpha.

<figure><img src="../.gitbook/assets/image (144).png" alt=""><figcaption></figcaption></figure>

## Manually set up 2.5d layers

You can manually set up a 2.5d shot by adding in layers and putting them in various Z-depth spaces, or project them on planes a varying depths. &#x20;

1. [Set your shot resolution](../getting-started/the-basics/change-shot-framerate-and-resolution.md) to the same resolution as your LED wall, or your preferred output resolution if Green Screen.&#x20;
2.  Add a Filler to the timeline and enter the shot.

    <figure><img src="../.gitbook/assets/image (449).png" alt=""><figcaption></figcaption></figure>


3.  If you want to increase the shot duration, go to the Live FX Menu and change the out number to something longer, like 1000 frames. <br>

    <figure><img src="../.gitbook/assets/image (452).png" alt=""><figcaption></figcaption></figure>
4.  Right-click and import your files one at a time, you may want to click on "Still Frame" if you are importing images.

    <figure><img src="../.gitbook/assets/image (450).png" alt=""><figcaption></figcaption></figure>


5.  After you add all your images, you can Shift+select them and Press Group. The order should go further back layer on top and closest layer on the bottom. Then with the Group selected, you may need to go to the Canvas menu and scale to fit.<br>

    <figure><img src="../.gitbook/assets/image (451).png" alt=""><figcaption></figcaption></figure>



For non-projection mapping workflows, you can now just [follow the instructions above.](./#greenscreen-non-projection-mapping)

For Projection Mapping workflows.&#x20;
