# How to delay the Inner Frustum

When you pan the camera and stop suddenly, if the frame of the inner frustum stops and the content inside keeps moving, you may need to delay the camera tracking **AFTER** it's been forwarded to Unreal Engine and **BEFORE** going to the LED wall.

!!! info

    If you delay the camera tracking from the Live Links menu, it will delay the camera tracking globally, before it's sent to Unreal Engine, and you will still have the same issue.


1. Navigate to the **Animate** button and the **Live Links** tab.

<figure><img src="../assets/image (345).png" alt=""><figcaption></figcaption></figure>

2. Now select X, Y, Z, Pan, Tilt, and Roll.
3. Click on the Delay of any one of the selected parameters and enter the number of frames you want to delay by.   
     
   We recommend starting with something like 10, which will be a noticeable difference.   
     
   Then work your way back until the content inside the frame and the frame move and stop at the same time.

<figure><img src="../assets/image (346).png" alt=""><figcaption></figcaption></figure>
