# Baking Light

Light baking is an excellent way to improve performance, but it is somewhat of a balancing act to make everything work correctly. Here are a few tips up front:

* Use GPU Lightmass Plugin
* If you have moveable objects in your scene, set them to movable and lighting to stationary (not static)

## GPU Lightmass

### Project settings

1.  Go to Edit>Plugins. Search for GPU Lightmass and Enable<br>

    <figure><img src="../../../assets/image (97).png" alt=""><figcaption></figcaption></figure>


2.  Go to Edit>Project Settings. Search Hardware Raytracing and Enable **Use Hardware Ray Tracing when available** and **Support Hardware Ray Tracing**.<br>

    <figure><img src="../../../assets/image (98).png" alt=""><figcaption></figcaption></figure>


3.  Also in Project Settings, search Virtual Texture and check **Enable Virtual Texture Support.**   
      
    **MAKE SURE TO ENABLE VIRTUAL TEXTURE LIGHTMAPS AS WELL.** <br>

    <figure><img src="../../../assets/image (99).png" alt=""><figcaption></figcaption></figure>


4.  Also in Project Settings, search Global Illumination and change to None.<br>

    <figure><img src="../../../assets/image (101).png" alt=""><figcaption></figcaption></figure>
5.  Probably not needed, but you can also go to your post-process volume and change your Global Illumination to None and Reflections to None.<br>

    <figure><img src="../../../assets/image (100).png" alt=""><figcaption></figcaption></figure>


6. Restart your project.

### Set up your lights

You will want to go through all of your lights and environment lighting and determine if you want them to be static or stationary. If unsure, just use Stationary.<br>

<figure><img src="../../../assets/image (102).png" alt=""><figcaption></figcaption></figure>

You may want to set your Skylight to Real Time Capture.<br>

<figure><img src="../../../assets/image (103).png" alt=""><figcaption></figcaption></figure>

I will change these point lights to Stationary as well.

<figure><img src="../../../assets/image (104).png" alt=""><figcaption></figcaption></figure>

### Set up your Objects

You need to determine which objects in your scene need to be set to Static, Stationary, or Moveable. <br>

<table><thead><tr><th width="197"></th><th width="353"></th><th>Examples</th></tr></thead><tbody><tr><td>Static Objects</td><td>Will not move at runtime at all. </td><td>Buildings</td></tr><tr><td>Stationary Objects</td><td>Objects might need to move but are not always moving.</td><td>Props that may be moved at runtime</td></tr><tr><td>Movable Objects</td><td>Objects need to move constantly.</td><td>Animated Cars</td></tr></tbody></table>



### Baking

Go to Build>GPU Lightmass to open the window.<br>

<figure><img src="../../../assets/image (105).png" alt=""><figcaption></figcaption></figure>

In the GPU Lightmass tab, uncheck "Viewport Realtime is OFF".

<figure><img src="../../../assets/image (106).png" alt=""><figcaption></figcaption></figure>

!!! info

    If you cannot turn of Viewport Realtime is off from this menu, go to the Viewport Options at the top left of the viewport and there will be something that says "Disable Realtime Override".  
    ![](<../../assets/image (108).png>)<br>


Click on Build Lighting at the top left of the GPU Lightmass window.<br>

<figure><img src="../../../assets/image (109).png" alt=""><figcaption></figcaption></figure>

### Tips and Troubleshooting

You can change your Lighting Quality by going to Build>Lighting Quality

<figure><img src="../../../assets/image (111).png" alt=""><figcaption></figcaption></figure>

You should check your Lightmap Density and Resolution Adjustment by going to Build>Lighting Info

<figure><img src="../../../assets/image (112).png" alt=""><figcaption></figcaption></figure>

With static lighting, especially where you have very large objects, like the ground, you may need to click on the object, search for "Lightmaps", and override the Light Map Res to be much much larger.

<figure><img src="../../../assets/image (110).png" alt=""><figcaption></figcaption></figure>

## References

Here are a few video references that have been helpful for us:

Baked RTX Lighting in Unreal Engine 5  
[https://youtu.be/2VY-ZBWM5-M?si=HYBETr4aIFUh5lUV](https://youtu.be/2VY-ZBWM5-M?si=HYBETr4aIFUh5lUV)

UE5 Can we still Bake Light?  
[https://www.youtube.com/watch?v=Tx-PNbKmLPU](https://www.youtube.com/watch?v=Tx-PNbKmLPU)
