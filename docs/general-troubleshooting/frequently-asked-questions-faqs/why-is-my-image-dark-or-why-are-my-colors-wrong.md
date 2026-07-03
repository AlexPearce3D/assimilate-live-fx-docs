# Why is my image dark (or why are my colors wrong)?

Sometimes when you import an image or movie file, the colors or brightness appear different than what you are expecting to see. In many cases, the color space or EOTF may need to be changed for it to be displayed properly.

In this example, an HDRI was used, which is scene linear/sRGB.

Here are two ways you can change Scene Linear to match your monitor.

1. Add a new layer and simply change the Gamma Master to 2.2 (or whatever your monitor is closest to).<br>
2.  Another way to do this is to add a new layer and go down to the Plug-Ins menu. Go to Effects>Color Space Converter and apply on layer.

    Change the input to:\
    Color:sRBG/EOTF: Scene Linear

    Change the output to:\
    Color: sRGB/EOTF: Gamma 2.2<br>
