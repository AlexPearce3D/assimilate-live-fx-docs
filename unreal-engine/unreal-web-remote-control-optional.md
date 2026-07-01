# Unreal Web Remote Control (Optional)

## Overview

**Web Remote Control** is an excellent way to control many parameters of Unreal Engine **through a web browser.**&#x20;

This way you can give an **iPad** to a Gaffer and allow them to make changes to the Sun and Skylight, for example.&#x20;

Web Control goes a lot deeper and there are many things to learn, this training will only talk about setting up **Web Remote Control for use with Live FX**, it will not teach you how to use Web Remote Control in depth.

{% hint style="info" %}
This plugin makes it easy to control UE through a web browser, and is helpful for Virtual Production in general, but is not required for Live FX to work properly.
{% endhint %}

{% hint style="info" %}
Not all parameters work when you package your project, even if they work in the editor. And not all parameters work when you use the -RenderOffscreen option.&#x20;

Custom Blueprints with Construction scripts that control variables don't seem to work when packaging games.&#x20;
{% endhint %}

For more information on Web Remote Control, visit the documentation:\
[https://docs.unrealengine.com/5.3/en-US/remote-control-web-application-for-unreal-engine/](https://docs.unrealengine.com/5.3/en-US/remote-control-web-application-for-unreal-engine/)



{% hint style="danger" %}
If WebRemote by any chance doesn't start, if UE says "Failed to build WebApp" error, this is what steps you need to do:<br>

Navigate to WebApp folder in (your local installation path >UE\_5.3/Engine/Plugins/VirtualProduction/RemotecontrolWebInterface/Webapp \
\
In WebApp folder, delete the Node-v16.17.0 (in my case what it was called) UE expects Node.js minimum version: 8. - maximum version: 14.15.5.

Start up UE, in your project double-click on your WebRemote Preset and UE should start building WebRemote dependencies.
{% endhint %}

## 1. Install Web Remote Control

1. **Go to Plugins** and search for Remote Control. &#x20;
2. Enable the plugin, **Remote Control API** (built-in).
3. Enable the plugin, **Remote Control Web Interface** (built-in).&#x20;
4. **Restart** Unreal Engine.

{% hint style="danger" %}
You must enable both plugins for it to work properly!
{% endhint %}

<figure><img src="https://lh7-us.googleusercontent.com/FMsTbKFmhFuEfU-fGReFW9qEz5Lh9merWGPdf3tAjVtfowypIra_EfgVVN9NE7TsyVXERbmqtLZDziDvEwivtsDUHkLGR6VozgLr_8N9oMm7lnF6qUE5oC96AOqu6S6UwqfSJFTkz4j1QRoAnkT8yApSQA=s2048" alt=""><figcaption></figcaption></figure>

## 2. Set up Remote Control

1. Somewhere in your Content browser, right-click, go down to “Remote Control” and click on **“Remote Control Preset”**.

<figure><img src="https://lh7-us.googleusercontent.com/UvTG5P7bC2zYj3Rn_xcktgq_Z4C7l_1Gu8bJqppQd-8tRMqLN5seCQDssSgcoBUbj7wKFvrb8z5Sy2Gb651QKRXSKALxO-xnYOXHYbrV6BTgyyxOZeq9eGmXmc_R4PH4Pe73Io1GWWv1rLZR6fRGbxAqFw=s2048" alt=""><figcaption></figcaption></figure>

2.  **Drag** the Remote Control Preset into the level. <br>

    <figure><img src="https://lh7-us.googleusercontent.com/DPUqV3OHQYveEDs_LLFFAzqx56mBX121H_2RBI6qgSMMmNx0ypnlczUg4QmeTEojnYxyg8yCXiEmSSpyhKfOO5GB_DowRekNn6rmphI8QkeJU_CgFntihT5XatIs7z3y5uTkgCfFWQbBfwF0vlsNR61_bQ=s2048" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
This is important if you want to package your project later.
{% endhint %}

3. Double-click on the newly created **Remote Control Preset**. \
   This **opens a new window** and now, an eyeball icon<img src="../.gitbook/assets/image (256).png" alt="" data-size="line"> shows up next to any items that you can remotely control in the outliner.\
   \
   :information\_source: A closed eyeball icon <img src="../.gitbook/assets/image (241).png" alt="" data-size="line"> means that this parameter is not exposed in your Web Remote Control.  An open eyeball icon <img src="../.gitbook/assets/image (256).png" alt="" data-size="line"> means that this parameter is exposed, and you can control it.

<figure><img src="https://lh7-us.googleusercontent.com/v_D8b6UZVujzZFBBbfCRoY6RsOjLNyiiNjeR4jQOpqZhUbBWHVG2F9rWMuaUfp2luwQy2AJZ_yvamvGRbjQjdqkZMKW18vGlBQFsmkiXU96-L5wdmATbtcQXWW_oNevMXvg2kPyNA-ACzBbLhk7OAj07BQ=s2048" alt=""><figcaption></figcaption></figure>

4.  The Description name is what is visible, so make sure to rename this to something that will be obvious what it is like "Sun Rotation".<br>

    <figure><img src="../.gitbook/assets/image (445).png" alt=""><figcaption></figcaption></figure>
5. Click on an item you want to be able to control to **see what you can control**.\
   \
   For this example, let’s click on the **Directional Light**, and turn the Light Color and Intensity eyeballs on.

<figure><img src="https://lh7-us.googleusercontent.com/v_D8b6UZVujzZFBBbfCRoY6RsOjLNyiiNjeR4jQOpqZhUbBWHVG2F9rWMuaUfp2luwQy2AJZ_yvamvGRbjQjdqkZMKW18vGlBQFsmkiXU96-L5wdmATbtcQXWW_oNevMXvg2kPyNA-ACzBbLhk7OAj07BQ=s2048" alt=""><figcaption></figcaption></figure>

5. Now click on **“Web App”**

<figure><img src="https://lh7-us.googleusercontent.com/0KJ9E91y1KAgMw1vSFo2yycBivUErSnp2Gs4_cU4UzdCKDvyHXSUpsVHZnAODvQSRR2OPZ1e17FZw2wXnrSr597KgvVXt2BQ2ksi7D8LrqjuPYHye04Fmm102kZKgaQipcfsPCDR5814lttmv8LR73nPvg=s2048" alt=""><figcaption></figcaption></figure>

6.  Choose whichever you want, I will use **Build Your Own UI.**<br>

    <figure><img src="https://lh7-us.googleusercontent.com/_IDvoammen9KpzuuNzDOvqB3MPBNlbVh4AM_6ey_8RY_bpuPNUmD5yBR2OxysQcQI4PKnhWv9INSz7nHckICgdB8daA5XbzoMC-il-oxSPKaIQBRxIcClgh6IpYGvIK7f68epT3QPMkrD6Xa6stOkrZvJw=s2048" alt=""><figcaption></figcaption></figure>
7.  Toggle **“Control” to “Design”** and click on the **“Properties” tab.**

    <figure><img src="https://lh7-us.googleusercontent.com/IgydxGNrF3kI2NmRQMhflYonFZ1zKldjy8svzGb11CXfAQTPGRmolci6uTcsJvyIc51oVqHPuHQ72U6r_c_-BaH916gbimaz-WGlHZT3l9o3J9bLb0MZ-q1vXvuuZNQa3bmVvdvqyGalK3TC9g6ItQ_S-w=s2048" alt=""><figcaption></figcaption></figure>
8.  **Click and Drag** “Light Color” and “Intensity” to the middle of the right side of the screen to start building your UI.<br>

    <figure><img src="https://lh7-us.googleusercontent.com/GxcXYBQjbl8JbklHMYrNkkmq578h9NejnB8t6cVlrqdZkHhNu6HMhU96FLbBjI2pySVkc4w06Rwz925DfDCr50OmA5qkALMWz6AZ-rSIimXNvPiAlEL8Ycq3UiuXVv9xJ6tkOjdkpVjW5yB9_P8NnFn5mQ=s2048" alt=""><figcaption></figcaption></figure>

## 3. Control Unreal Engine through Web Remote

1. Switch back to Control.\
   \
   You can now **control the Light Color and Intensity of the Directional Light**, from your web browser!

<figure><img src="https://lh7-us.googleusercontent.com/wUF3U9-mARolp4X1RAF8zZ873hHP4H02SZ3CK7CurzHjhwBSdF6-m4J9O0tvrypDIryeMg8BZr5z_MblcnjpJgg1FBn8gQ0R5NYu-z8UT3SvSJd1z7Czm0yWPFS6sK3ioY2tww40PQgxQ6gdYazwMrHFwA=s2048" alt=""><figcaption></figcaption></figure>

2. Open a browser.\
   \
   Type in 127.0.0.1:30000\
   \
   **Control through your browser!**

<figure><img src="https://lh7-us.googleusercontent.com/SdTvCCxtQQ0p1DJ0mBdG_LFehMyL4ni_0TXBRYWQdsivAbrap-uTlrSezjg4bl_4iXN3kBU0IAHqDYDAjEaxlA7-EGjNULd6hVOifb3K0UHAOfF9O59cSz0q4H5bOSEh9dPeMYom8BJU5funCdn6z7I6KQ=s2048" alt=""><figcaption></figcaption></figure>

If you want to control from a different device on the same network, enter the host's ip address:30000 into the browser. For example, it would look something like 192.168.1.23:30000 \
\
To find your [computer's IP Address you can follow the steps here.](../general-troubleshooting/networking-tips.md#how-to-find-your-computers-ip-address)

## 4. iPad or iPhone App (Optional)

If you have a compatible iPhone or iPad and are connected to the **same network** as your Unreal Engine machine, you can use the application from the **App Store**:\
\
[https://apps.apple.com/us/app/unreal-remote-2/id1374517532](https://apps.apple.com/us/app/unreal-remote-2/id1374517532)



## 5. Copy Webapp into Executable

If you are planning on using the Remote Control with an executable, [make sure to follow these steps at this link. ](how-to-package-an-unreal-engine-project-for-live-fx/)
