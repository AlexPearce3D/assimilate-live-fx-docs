# HDR with Windows Consumer Monitor in 9.8

Consumer TV Consumer TVs (or HDR-capable laptop displays) act differently.

To get HDR working properly on consumer monitors, you have to trick it into HDR, and a lot of the settings we will go over here, are counter intuitive (like turning HDR off in Windows).

  
1\. Go to Settings>System>Display and make sure HDR is turned on.

The shortcut to toggle HDR on and off is Windows+Shift+B.

<figure><img src="../../../assets/image (14).png" alt=""><figcaption></figcaption></figure>





2. Go to Nvidia Control Panel, and under "Change Resolution" (or in Mosaic Settings, if you are using Nvidia Mosaic), choose an output color depth of at least 10 bpc.   
     
   Although confusing, the Desktop Color Depth does not need to be set to HDR to use the HDR monitor.   
     
   \*HOWEVER, if you have true HDR content, you will need to use these settings to playback HDR properly:   
     
   **Desktop Color Settings:HDR (64-bit)**   
   **Output Color Depth: At least 10 bpc**  
   **Output Dynamic Range: Full**<br>

<figure><img src="../../../assets/image (8).png" alt=""><figcaption></figcaption></figure>

\*If you cannot change these settings, or you get weird artifacts when trying to change, your cables or HDMI adapters may not be good enough to do proper HDR 10 bit.

<figure><img src="../../../assets/IMG_3010.jpeg" alt=""><figcaption></figcaption></figure>

Notice above that the Sun disk is not visible and the highlights are blown out, this is with SDR(64-Bit)

<figure><img src="../../../assets/HDR(64bit) (2).jpeg" alt=""><figcaption></figcaption></figure>

Now with the same settings everywhere else, by changing the settings to HDR(64-Bit), we can see the Sun and make out a lot more detail in the highlights.   
  
  
3\. In Assimilate, under System settings, search for HDR and turn on "Enable Extended Dynamic Range for Dual Head". If your user interface is HDR, turn on "Enable Extended Dynamic Range for UI"<br>

<figure><img src="../../../assets/image (9).png" alt=""><figcaption></figcaption></figure>

<br>

4. Make sure your media is flagged correctly, if using an HDRi, sRGB Scene Linear for example

<figure><img src="../../../assets/image (10).png" alt=""><figcaption></figcaption></figure>



5.  Under Settings>Monitors, set the Dual Head to   
    Rec 709 (or 2020 if you're going to 2020)  
    Set to Gamma 2.4   
      
    \*(even though we know this is actually supposed to be HDR, we have to trick Windows into working with HDR, by clamping the signal).<br>

    <figure><img src="../../../assets/image (11).png" alt=""><figcaption></figcaption></figure>
6. You will likely need to bring down the gamma to around .5 for the content look correct and may need to gain up.  
     
   In this example, the background should look very close to black, not lifted purple. By adjusting the gamma by .5, this gets us back to the appropriate setting. This applies to both HDR and SDR content.   
   ![](<../../assets/image (12).png>)![](<../../assets/image (13).png>)<br>
