# Mark Roberts Motion Control (MRMC)

[Camera Tracking](../camera-tracking/) is supported via [Free D ](../camera-tracking/camera-trackers/free-d.md)protocol with [MRMC Robots ](https://www.mrmoco.com/motion-control/)through [Flair](https://www.mrmoco.com/motion-control/flair/).&#x20;

Supported MRMC Robots; [Bolt X](https://www.mrmoco.com/motion-control/bolt-x/), [Bolt,](https://www.mrmoco.com/motion-control/bolt/) [Bolt Jr+](https://www.mrmoco.com/motion-control/bolt-jr-plus/)

Flair sends tracking data out at 50Hz. If your productions frame-rate is not 50fps (24, 23.98, 25, 29.97, 30, 48, 59.94 or 60fps) you will need to interpolate the data before Live FX receives the data. If you do not interpolate the tracking data to your productions frame-rate, the tracking will jitter. Contact MRMC the best interpolation settings, as each robot is different. Additionally, we recommend using the MRMC Flair Virtual Production Synch Box to simply the workflow.

Flair Setup

Once Flair is open, navigate to:

Setups / External Devices

<figure><img src="../.gitbook/assets/Screenshot 2024-08-29 at 5.37.38 PM.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/Screenshot 2024-08-29 at 5.36.00 PM.png" alt=""><figcaption></figcaption></figure>

External Devices Setup

Set Data Output to [Free D](../camera-tracking/camera-trackers/free-d.md), UDP and set a Static IP address. Set the Port Number to **4000**. Click apply and Save.

In Live FX, navigate to the Live Links menu.

<figure><img src="../.gitbook/assets/Screenshot 2024-08-29 at 7.16.09 PM.png" alt=""><figcaption></figcaption></figure>

Activate Free D.&#x20;

Select the correct network interface. Set your port to 4000.&#x20;

Click apply.&#x20;

Your tracking is now applied and will be visible in the Live Links menu.
