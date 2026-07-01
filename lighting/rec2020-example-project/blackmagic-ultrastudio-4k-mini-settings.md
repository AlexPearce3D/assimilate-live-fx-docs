# Blackmagic UltraStudio 4k Mini Settings

{% hint style="danger" %}
We have seen a bug with the UltraStudio 4k mini, that would cause color shifting in the Kino Flo Mimik. \
\
We were able to fix it by cycling from "Keep default color gamut", to "Convert to Rec. 2020" and then back to what it should be; "Keep default color gamut".&#x20;
{% endhint %}

The settings are in the screenshots below, here are the main ones to keep in mind.&#x20;

#### Video Output

Default Video Standard: 1080 24p (or whatever you need)

During Capture: Video output displays input video

During playback: Keep Default color gamut

<figure><img src="../../.gitbook/assets/image (48).png" alt=""><figcaption></figcaption></figure>

### SDI Output

Color Space: Video is converted to Y, Cb, Cr, 4:2:2

1080p HD and 2k: 1080p progressive video

SDI Connector: Single Link

<figure><img src="../../.gitbook/assets/image (49).png" alt=""><figcaption><p>Should actually be Single Link</p></figcaption></figure>

### HDMI Output

Frame Packing

<figure><img src="../../.gitbook/assets/image (51).png" alt=""><figcaption></figcaption></figure>
