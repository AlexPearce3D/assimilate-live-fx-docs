# Video-IO Settings

The iron rule of thumb is that all YUV (or YCbCr) signals shall be legal range (and vice versa, RGB signals shall be full range ;-). So selecting a YUV output signal, but then choosing an RGB matrix cannot possibly work. selecting a YUV matrix gets you there halfway, but as you will find out, will clip certain parts of the signal at top and bottom (the green bars & green patch).

<figure><img src="../.gitbook/assets/Screenshot 2024-06-18 at 12.17.37 PM.png" alt=""><figcaption><p>Video-IO menu: The format an default YUV Matrix are chosen in the upper right corner of the menu. In the lower half, the Matrix can be overridden for any of the input / output channels.</p></figcaption></figure>

To elaborate a bit more: Live FX internally works in full range RGB (as any respectable finishing tool / live compositor would). So when setting your output to YUV, Live FX has to apply a matrix to go from RGB to YUV. And that matrix also contains a conversion from full to video range. This is what you select in the second dropdown (below the "Format" one in the upper right corner of the menu). And obviously, if you chose to output a YUV signal, you should then choose the corresponding YUV matrix (and in video range, please) along with it. In your case, that would be Rec2020 Video.

The alternative is to select RGB as the output and choose the RGB full matrix along with it. While the RGB signal is technically cleaner (no chroma subsampling, no matrix conversions), I doubt it will make any difference of significance for IBL. So feel free to choose whatever you think works best.

Now for the lower half of the video-io dialog: There you can override the RGB to YUV Matrix for every output channel. As long as the dropdown there says , it will refer to what you set as the matrix in the upper right corner. But you can override that setting, by selecting a different matrix for any of the output channels.

For input channels, it works similarly. Of course, Live FX can't "define" what arrives in any given input channel. But you can help "interpret" the incoming signal, by setting the corresponding dropdown for that channel to the correct matrix. That being said, whatever you set the matrix to for an input channel, it will not prevent any clipping, as that would already occur on the "sender's" side, when making an SDI signal from it.



### The unwritten rule of video signal distribution:

YUV / YCbCr signals are to be encoded, decoded and interpreted as video range.\
RGB signals are to be encoded, decoded and interpreted as full range.

As long as you don't deviate from this rule, you will live a happy life.
