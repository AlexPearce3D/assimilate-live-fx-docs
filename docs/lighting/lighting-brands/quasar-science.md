# Quasar Science

## How to set up Quasar Science lights in Live FX

!!! danger

    **Make sure you have the** [**latest firmware**](https://www.quasarscience.com/pages/firmware-updates) **before getting set up, if your firmware is too old, the following steps will not work.**


Watch the tutorial here:

> Video/resource: [https://youtu.be/DTVNb0to3YE](https://youtu.be/DTVNb0to3YE)


In the video above, I show you how to set up your [Quasar Science](https://www.linkedin.com/company/quasarscience/) fixtures with [ASSIMILATE](https://www.linkedin.com/company/assimilate/) Live FX to do image-based lighting (through pixel mapping).

Once it's set up, it's very easy to sample any area of your canvas and to control the brightness/intensity for each array.

In this article, I will cut straight to the information you need to program your lights on the fixture, and in the software, watch the video for more step-by-step instructions.

<figure><img src="https://media.licdn.com/dms/image/D5612AQElCjv8X9OGug/article-inline_image-shrink_1000_1488/0/1698676119806?e=1710979200&#x26;v=beta&#x26;t=mdJI_bz0ywqduHWu60GO2JfxHxTicAnVJlyD5ieJPVw" alt=""><figcaption><p>Live FX. Notice the area we are sampling is being pixel mapped correctly to the array of 47 Quasar Science fixtures!</p></figcaption></figure>

## Quasar Science Fixture settings <a href="#ember3390" id="ember3390"></a>

You'll want to make sure you use the following settings on your Quasar Science fixtures:

* Number of Pixels - Max (48 for 8' Rainbow, 20 for 2' Double Rainbow, etc.)
* Profile - 64
* Wired Mode - sACN
* DMX Channel - 1
* Multicast - Enabled
* Universe - Set your array appropriately. For example, if you have an array of 47, make the top fixture universe 1, the second fixture 2, all the way through your last fixture, universe 47.
* Wireless Mode - Off
* Lead/Follow - Off

<figure><img src="https://media.licdn.com/dms/image/D5612AQFrJmHb3TTveA/article-inline_image-shrink_1000_1488/0/1698675850600?e=1710979200&#x26;v=beta&#x26;t=z7aaEbSOja5M5M7NU3PSIRc6C-jaV8UaecOR8r3TJjg" alt=""><figcaption><p>Make sure you set your Profile to 64, sACN is on, your pixel count is the highest and that you know which universe is the start universe.</p></figcaption></figure>

## Mapping Quasar Fixtures in Live FX <a href="#ember3401" id="ember3401"></a>

There are a few things to get set up in Live FX.

1. Let's start with **Protocols, sACN**.
2. Make sure Output (multicast) is turned on, and the correct Ethernet adapter where the Light or network switch is plugged in.
3. You may need to restart Live FX if you don't see your adapter and it was plugged in after you started Live FX.

!!! info

    Make sure your start and end universe covers your range.


<figure><img src="https://media.licdn.com/dms/image/D5612AQHimRoIH5-WwA/article-inline_image-shrink_1500_2232/0/1698676945516?e=1710979200&#x26;v=beta&#x26;t=ff1UtcVF5SboLauWkr-PnxBTvD6JseXGhuClwh9jmk4" alt=""><figcaption><p>sACN settings</p></figcaption></figure>

4. Now under the **Fixture Patching** Tab, let's add a new fixture and use the following settings:

* Universe - 1 (or whatever your starting universe is)
* Channel - 1
* Channels - 12
* Globals - 6
* Repeat in Universe - 48\* (This is the number of pixels in your lighting fixture)
* Repeat the Universe - 47\* (This is the number of fixtures in your array)

!!! warning

    For Double Rainbow, you need to double the number of Segments. For example, if you have 6 fixtures, you would have Repeat the Universe as 6 and Segments as 12.  
    May need to do Repeat the Universe as 12 and Segments as 12.


<div data-full-width="true"><figure><img src="https://media.licdn.com/dms/image/D5612AQF8MCzykCtXdQ/article-inline_image-shrink_1500_2232/0/1698678063026?e=1710979200&#x26;v=beta&#x26;t=tsdopeVtgYOAubYuUgD0s8-AsuG_0ITNXrVK-qUUOQo" alt="" width="375"><figcaption></figcaption></figure></div>

5. Also on the Fixture Patching tab, let's set the channels.

**Channels**

<table><thead><tr><th width="135">Channel #</th><th width="173">Channel Type</th><th width="123">Value </th><th>Description</th></tr></thead><tbody><tr><td>1</td><td>Sample: Red</td><td></td><td></td></tr><tr><td>2</td><td>Fine</td><td></td><td></td></tr><tr><td>3</td><td>Sample: Green</td><td></td><td></td></tr><tr><td>4</td><td>Fine</td><td></td><td></td></tr><tr><td>5</td><td>Sample: Blue</td><td></td><td></td></tr><tr><td>6</td><td>Fine</td><td></td><td></td></tr></tbody></table>

**Global Channels** (Make sure to write a description)

!!! info

    Global Channels will not show up until you change the "**Repeat in Universe**" to a number higher than 1.


<table><thead><tr><th width="135">Channel #</th><th width="139">Channel Type</th><th width="73">Value</th><th>Description</th></tr></thead><tbody><tr><td>7G</td><td>DMX Value</td><td>147</td><td>CCT</td></tr><tr><td>8G</td><td>DMX Value</td><td>0</td><td>+- Green</td></tr><tr><td>9G</td><td>DMX Value</td><td>255</td><td>Spectrum</td></tr><tr><td>10G</td><td>DMX Value</td><td>0</td><td>Color Space</td></tr><tr><td>11G</td><td>DMX Value</td><td>0</td><td>Output</td></tr><tr><td>12G</td><td>DMX Value</td><td>0</td><td>Reserved</td></tr></tbody></table>

<figure><img src="https://media.licdn.com/dms/image/D5612AQGPnRX2v3AN4A/article-inline_image-shrink_1500_2232/0/1698678164708?e=1710979200&#x26;v=beta&#x26;t=DlWoBuZLEakFQM0uvnHW2BaFgVoCBcVaB4AdSJzGmn0" alt=""><figcaption><p>The channel assignments in Live FX</p></figcaption></figure>

6. On the **Color Sampling tab**, change the Sample grid to Distribute and the segments should be the number of fixtures in your array, in my case, 47.

<figure><img src="../../../assets/image (342).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../assets/image (341).png" alt=""><figcaption><p>Don't forget to change the Sample Grid to Distribute and put as many segments as you have fixtures in your array!</p></figcaption></figure>

Once you've set up your fixture, you can duplicate this fixture (see top left of photo below) or you can export your entire setup using the export button (see bottom left of picture below).

I use the export feature to save my entire stage layout, over 150 fixtures!

<figure><img src="../../../assets/image (343).png" alt=""><figcaption></figcaption></figure>

  
Tags:

[Quasar Science](https://www.linkedin.com/company/quasarscience/) - Lighting

[ASSIMILATE](https://www.linkedin.com/company/assimilate/) - Live FX

[Light Sail VR](https://www.linkedin.com/company/light-sail-vr/) - Content

[Planar](https://www.linkedin.com/company/planar-systems/) - LED Wall

[Silverdraft](https://www.linkedin.com/company/silverdraft/) - Computer

[OptiTrack](https://www.linkedin.com/company/optitrackmocap/) - Camera Tracking
