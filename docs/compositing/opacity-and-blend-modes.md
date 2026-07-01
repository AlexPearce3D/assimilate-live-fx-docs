# Opacity and Blend Modes

To change how much opacity a layer has, go to the fill tab on the top-left menu, and on the left, you can change the opacity from 100 (default) to something less to blend the images together.

<figure><img src="../assets/image (531).png" alt=""><figcaption></figcaption></figure>

You can use any of the common blend styles as needed for your project. In this case I have the lighting pass of the Sunlight, and I'm able to subtract that from my scene, effectively re-lighting my scene after the initial render in compositing.

<figure><img src="../assets/image (534).png" alt=""><figcaption></figcaption></figure>

### General

Each Layer has a set of controls for determining how the layer is blended with the base image and the other layers. These controls are: Opacity, Blend mode and Recursive. You can set the values for each of these properties in the Layers List in the Front (Opacity and RGB blend mode) and Matte (alpha blend mode) tabs.

**OPACITY**

The Opacity parameter in the Front tab sets the level at which a Layer is mixed with the other layers. This control is linked to the Opacity control in the Canvas menu. Note that to animate the Opacity level of a Layer, you must use the control in the Canvas menu.

**BLENDING MODES**

The following modes are available for both RGB and alpha blending.

* Normal: Blend is a simple, non-pre-multiplied overlay of the image, using the value of the alpha channel to determine the opacity of each pixel.
* Over: Over is similar to Blend, except the foreground image is assumed to be pre-multiplied.
* Add: The foreground and background colors are added together. The overall value is multiplied by the alpha channel to determine the final amount that is added to the image.
* Subtract: Subtract is the inverse of Add, where the foreground color is subtracted from the background color.
* Multiply: Multiply looks at the color information in each channel and multiplies the background color by the foreground color.

For RGB / Front, the following additional modes are available:

* Screen: Screen is the opposite of Multiply, where the background is multiplied by the inverse of the foreground color.
* Overlay: Overlay combines Multiply and Screen blend modes. Light parts of the picture become lighter and dark parts become darker.
* Dodge: Dodge mode multiplies the pixel value of the lower layer by 256, then divides that by the inverse of the pixel value of the top layer. The resulting image is usually lighter, but some colors may be inverted.
* Burn: Burn mode inverts the pixel value of the lower layer, multiplies it by 256, divides that by one plus the pixel value of the upper layer, then inverts the result. It tends to make the image darker, somewhat similar to “Multiply” mode.
* Lighten: Lighten uses the lighter value between foreground and background images. Whichever value is higher is used in the resulting image. This is evaluated individually for each channel of the image.
* Darken: Darken uses the darker value between foreground and background images. Whichever value is lower is used in the resulting image. This is evaluated individually for each channel of the image.
* Negate: Produces the opposite effect to Difference. Instead of making colors darker, it makes them brighter.
* Soft light: Darkens or lightens the colors, depending on the blend color. The effect is similar to shining a diffused spotlight on the image.
* Hard light: Multiplies or screens the colors, depending on the blend color. The effect is similar to shining a harsh spotlight on the image.
* Difference: The Difference blending takes the absolute value of the subtraction of the source and layer pixel values.
* Exclusion: Creates an effect similar to Difference Mode but lower in contrast often smoother effect. Blending with white inverts the base color values. Blending with black produces no change.
* Color: The Color blending mode takes the chrominance of the layer and combines it with the luminance of the source.
* Luminosity: The Luminosity blending mode takes the luminance of the layer and combines it with the chrominance of the source

**RECURSIVE**

Each Layer also has a Recursive setting which determines whether a Layer will interact with the layers below it or if it will take the base image as its starting point. Recursion can be toggled on / off by clicking the '**R**' button that is available with each Layer in the Layer list. An empty button indicates that Recursive is off.

Tip: You can choose the default behavior of every new Layer by setting the **Recursive Layer** option in the Player User Configuration.

When Recursive is active for a Layer it will use the results of the layers below it as the starting point for any color grading. With Recursive deactivated the base image will be used.

**Recursive Activated**

<figure><img src="../assets/image (532).png" alt=""><figcaption></figcaption></figure>

**Recursive Deactivated**

<figure><img src="../assets/image (533).png" alt=""><figcaption></figcaption></figure>
