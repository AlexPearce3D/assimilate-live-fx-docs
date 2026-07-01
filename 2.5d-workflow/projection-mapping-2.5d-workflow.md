# Projection Mapping 2.5d Workflow

You can manually set up a 2.5d shot with projection mapping by adding in layers and putting them in various Z-depth spaces, or project them on planes a varying depths. &#x20;

1. [Set your shot resolution](../getting-started/the-basics/change-shot-framerate-and-resolution.md) to the same resolution as your LED wall, or your preferred output resolution if Green Screen.&#x20;
2.  Add a Filler to the timeline and enter the shot.<br>

    <figure><img src="../.gitbook/assets/image (118).png" alt=""><figcaption></figcaption></figure>
3.  If you want to increase the shot duration, go to the Live FX Menu and change the out number to something longer, like 1000 frames. <br>

    <figure><img src="../.gitbook/assets/image (119).png" alt=""><figcaption></figcaption></figure>


4.  Right-click and import your files one at a time, you may want to click on "Still Frame" if you are importing images.<br>

    <figure><img src="../.gitbook/assets/image (120).png" alt=""><figcaption></figcaption></figure>


5.  After you add all your images, you can Shift+select them and Press Group. The order should go further back layer on top and closest layer on the bottom. Then with the Group selected, you may need to go to the Canvas menu and scale to fit.<br>

    <figure><img src="../.gitbook/assets/image (121).png" alt=""><figcaption></figcaption></figure>


6. Go to the camera menu and [activate the camera](../getting-started/the-basics/general-tips.md#activate-the-camera).
7. Connect your tracker and make sure to Apply the tracking information.
8.  Go to the Camera menu, Config Tab and change the Far Clipping to something very far, like 10000<br>

    <figure><img src="../.gitbook/assets/image (482).png" alt=""><figcaption></figcaption></figure>
9.  For each layer, we need to do the following. \
    1\. **Select the Layer** \
    2\. Go to the **Plugins Menu** \
    3\. Add the **Plane->Wall plugin.**\
    **4.** Make sure to **Add to Layer**<br>

    <figure><img src="../.gitbook/assets/image (485).png" alt=""><figcaption></figcaption></figure>


10. Now for each layer we need to Go to the Plane->Wall Menu, and Link to Stage Manager. Select the wall you want to use. <br>

    <figure><img src="../.gitbook/assets/image (486).png" alt=""><figcaption></figcaption></figure>


11. For each layer we also need to Go to the **Plane->Wall Menu**, click on the **Projection tab**, and enable **Link to Shot Camera.**

    <figure><img src="../.gitbook/assets/image (487).png" alt=""><figcaption></figcaption></figure>


12. Open Stage Manager so we can visualize the next steps.<br>

    <figure><img src="../.gitbook/assets/image (488).png" alt=""><figcaption></figcaption></figure>


13. Now select one layer at at time and move the Trans Z back in Z space, with the furthest layer the furthest negative, and the closest layer closer to 0. Use the Width/Height to scale it up and down and use X,Y to move it as needed. <br>

    <figure><img src="../.gitbook/assets/image (489).png" alt=""><figcaption></figcaption></figure>



{% hint style="info" %}
Look through the camera or through Stage Manager to see if it looks correct, the viewport will look the opposite of what you would expect. For example, you would expect the background layers would not move and the foreground layers would move as you move the camera along the X axis, but with Projection Mapping, this is backward in the Viewport.
{% endhint %}
