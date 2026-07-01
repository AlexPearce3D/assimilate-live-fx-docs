# Keyers and Alpha Output

<h3 id="keyer-pre-and-post-options">Keyer Pre- and Post-Options</h3>
<p>To be able to create a key in a live context without having to create multiple layers and/or use additional plug-ins, the Qualifier menu has been split in a separate color selection tab and a pre- / post-options tab with a set of new functions.</p>
<p><img alt="" src="../../assets/official-reference/live-fx-user-guide/LFX_Qualifier_Options_v01.png" /></p>
<p>The new functions are:</p>
<ul>
    <li>    Denoise pre-option, to remove noise in the source image to create a cleaner key.</li>
    <li>    Clip Black / White post-options, which basically works as a lift-function on the alpha channel from the key, clipping the alpha at a certain level with minimal effect to the existing edges.</li>
</ul>
<p>(all other qualifier functions are described in the main manual)</p>
<h3 id="alpha-output-over-sdi-dual-head">Alpha output over SDI / Dual head</h3>
<p>Live FX offers the option to output the alpha channel of a (live capture) shot as a black and white image through an SDI output or through the dual head GPU output. This offers an opportunity to use the qualifier / keyer function of Live FX – including all layering and garbage mask functions, plug-ins and compositing options – for other systems downstream in the pipeline. The SDI output can be gen-locked and contains the active timecode of the shot / live captured input. To output the black/white matte just select the option with the Display settings in the Player – Settings – Monitors menu.</p>
<p><img alt="" src="../../assets/official-reference/live-fx-user-guide/LFX_VideoIO_Keyer_v01.png" /></p>
</div>
<p></p>
