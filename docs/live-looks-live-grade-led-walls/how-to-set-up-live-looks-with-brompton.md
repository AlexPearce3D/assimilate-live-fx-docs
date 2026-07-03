# How to set up Live Looks with Brompton

First, you'll need to make sure your computer with Live FX is connected to the same network as the Brompton processor, and that [you can ping the network successfully](../general-troubleshooting/networking-tips.md#how-to-ping-a-device-on-the-network).

1. Open Assimilate and click on the **Live Looks** button on the left.
2. Enter the Setup menu on the left.
3. Go to the **LUT boxes** tab
4. Click on **Find & Setup**
5. Disable Teradek and enable **Brompton**
6. Click on **Edit**<br>
7.  This opens a text file that you can edit. Add lines with a group name and 1 or more IP address(es) of processors, separated by commas.

    For example, if you have 6 Brompton processors, could set up Live Looks to have 7 different groups, 1 master will all the processors, and then 6 groups to individually grade specific walls.

    :bulb:You may need to restart Assimilate after you set up the network correctly.<br>
8. **Save** the text file.
9. You may need to click **Re-Scan** for it to find the new config.<br>
