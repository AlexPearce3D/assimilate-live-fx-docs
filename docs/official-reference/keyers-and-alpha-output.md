# Keyers and Alpha Output

### Keyer Pre- and Post-Options <a href="#keyer-pre-and-post-options" id="keyer-pre-and-post-options"></a>

To be able to create a key in a live context without having to create multiple layers and/or use additional plug-ins, the Qualifier menu has been split in a separate color selection tab and a pre- / post-options tab with a set of new functions.

The new functions are:

* Denoise pre-option, to remove noise in the source image to create a cleaner key.
* Clip Black / White post-options, which basically works as a lift-function on the alpha channel from the key, clipping the alpha at a certain level with minimal effect to the existing edges.

(all other qualifier functions are described in the main manual)

### Alpha output over SDI / Dual head <a href="#alpha-output-over-sdi-dual-head" id="alpha-output-over-sdi-dual-head"></a>

Live FX offers the option to output the alpha channel of a (live capture) shot as a black and white image through an SDI output or through the dual head GPU output. This offers an opportunity to use the qualifier / keyer function of Live FX – including all layering and garbage mask functions, plug-ins and compositing options – for other systems downstream in the pipeline. The SDI output can be gen-locked and contains the active timecode of the shot / live captured input. To output the black/white matte just select the option with the Display settings in the Player – Settings – Monitors menu.
