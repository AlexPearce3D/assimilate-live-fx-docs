# Why is my image dark (or why are my colors wrong)?

Sometimes when you import an image or movie file, the colors or brightness appear different than what you are expecting to see. In many cases, the color space or EOTF may need to be changed for it to be displayed properly.

In this example, an HDRI was used, which is scene linear/sRGB.

<figure><img src="../../../assets/image (272).png" alt="" width="375"><figcaption><p>Scene Linear does not look correct without an adjusment</p></figcaption></figure>

Here are two ways you can change Scene Linear to match your monitor.

1.  Add a new layer and simply change the Gamma Master to 2.2 (or whatever your monitor is closest to). <br>

    <figure><img src="../../../assets/image (271).png" alt=""><figcaption><p>Master Gamma changed to 2.2</p></figcaption></figure>
2.  Another way to do this is to add a new layer and go down to the Plug-Ins menu. Go to Effects>Color Space Converter and apply on layer.   
      
    Change the input to:   
    Color:sRBG/EOTF: Scene Linear  
      
    Change the output to:  
    Color: sRGB/EOTF: Gamma 2.2<br>

    <figure><img src="../../../assets/image (273).png" alt=""><figcaption></figcaption></figure>
