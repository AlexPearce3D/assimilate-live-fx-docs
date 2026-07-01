# Mimik 120

## Overview

Here is a great video Tutorial for setting up the Kino Flo Mimik in Live FX:

[Image-Based Lighting - Video Fixtures](https://youtu.be/kiXWHEGBUJE?si=iobk7B9s8CWmcFag)<br>

MIMIK 120 is an image-based video lighting tile that mirrors video content while applying a higher tonal and color rendering range. MIMIK delivers extended spectral bandwidth and cinematic color fidelity when lighting talent and set elements in virtual production environments.

Patented Kino Flo technology translates an incoming RGB video signal into five individual emitters (warm white, cool white, red, green, and blue), generating synchronized foreground lighting that creates the utmost realism on virtual sets.

Embodied in a lightweight carbon fiber frame, MIMIK adapts to on-set configurations with easy mobility. Controlled by the Megapixel VR HELIOS LED processor, MIMIK expands real-time and post-production options, delivering 10,000 NITS, along with the ability to shoot as high as 900 frames per second and offer as many as 30 Alpha channels at 30 frames per second.

This revolutionary full spectrum LED image-based lighting solution enables latency-free synchronization to an LED volume along with the versatility of optional control from a lighting desk.

To learn information about it, visit [https://kinoflo.com/mimik-120/](https://kinoflo.com/mimik-120/)



## Getting started with the Mimik 120



The Mimik is between an LED tile and a Lighting Fixture, and Assimilate Live FX has a unique workflow for the Mimik in the Stage Lights tab, instead of a normal fixture, they are called "Video Fixtures".

## Color Management for Kino Flo Mimik

For regular lighting fixtures, you can use the Color Transform tab to take the incoming signal and transform to the correct color space, but this is NOT how Video Fixtures work.

<figure><img src="../../../../assets/image (526).png" alt=""><figcaption><p>Notice the Color Transform Controls are greyed out when using Video Fixtures</p></figcaption></figure>

Instead, to do Color Space Transforms on Video Fixtures, we use the Settings>Monitor settings.

Whatever the source is for your incoming signal, ensure it is set up properly in the Live FX menu, under Media.

If someone else is giving you a feed, you may need to confirm with them what the source should be.

<figure><img src="../../../../assets/image (528).png" alt=""><figcaption><p>In this case we are using an HDRi and it is sRGB Scene Linear. </p></figcaption></figure>

If the source is different than the output to the LED processor, you set it correctly in the Settings>Monitors menu.

For example, if your HELIOS processor is set to Rec2020, PQ, then you would go into the Settings>Monitors menu and set the feed that you sending the Mimik on to Rec2020, PQ.

<figure><img src="../../../../assets/image (527).png" alt=""><figcaption></figcaption></figure>

You should also check Settings>Video IO and ensure the video signal is set up properly.

<figure><img src="../../../../assets/image (529).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../../assets/image (530).png" alt=""><figcaption><p>Ensure you are sending the correct levels</p></figcaption></figure>

