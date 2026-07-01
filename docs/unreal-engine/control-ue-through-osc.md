# Control UE through OSC

## Overview

You can use OSC to do many things. We are going to create a layer in Live FX and use it to drive our Sun in Unreal Engine.



Live FX currently has one way of using OSC that uses the first layer's Canvas transform controls, to control custom properties in Unreal Engine via a blueprint the user can set up.

There are a total of 8 float values that can be used in Unreal Engine, they correspond to the following properties in the Canvas menu (of the top dummy layer).

The numbers here correspond to the Index numbers in the **Get OSC Message Float At Index** node in Unreal Engine:

<figure><img src="../../assets/image (87).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../assets/image (86).png" alt=""><figcaption></figcaption></figure>

You can set these numbers to control many different areas of your Unreal Engine Scene, but for us, the default settings we will use will be to reserve 0 for Sky Light Intensity and we'll reserve 5,6,7 for Intensity and location in the sky:  


0: Sky Light Intensity   
5: Directional Light Intensity  
6: Directional Light Pitch  
7: Directional Light Roll

<figure><img src="../../assets/image (522).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../assets/image (523).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../assets/image (525).png" alt=""><figcaption></figcaption></figure>

## Set up Live FX

1. Go to Live FX Menu>Live Links
2. Turn on OSC Sender
3. Turn On, enable Animation and press connect.
4.  For your ip, if it's the local machine, you can use 127.0.0.1. For port, you can use 9003 or whatever port, but you'll need to remember this for later. <br>

    <figure><img src="../../assets/image (491).png" alt=""><figcaption></figcaption></figure>


5.  Create a new layer, and make sure it is the very top layer. This will be a "dummy" layer, do not add color grading or anything else to it. <br>

    <figure><img src="../../assets/image (492).png" alt=""><figcaption></figcaption></figure>



## Set up Unreal Engine

You can find the whole blueprint here, copy and paste it into your Level Blueprint, and then connect the Event Begin Play to the Create OSC Server Exec pin. It may have some errors, but you should be able to fix them by following the instructions below.

[https://blueprintue.com/blueprint/m6-a4t3l/](https://blueprintue.com/blueprint/m6-a4t3l/)

  
Here is another pastebin with a few more things added, that will serve as a template of sorts, for OSC.

[https://blueprintue.com/blueprint/hpe6xzd2/](https://blueprintue.com/blueprint/hpe6xzd2/)<br>

Manual Instructions for creating the Blueprint.

1.  In your Level Blueprint (or you could create a new one), from **Event Begin Play**, add the node **Create OSCServer.**   
      
    1\. For the IP Address you can use 0.0.0.0.   
    2\. For the Port use 9003 or whatever you set in Live FX  
    3\. Check Start Listening  
    4\. Write the same Server Name you added in Live FX for the Server Name. <br>

    <figure><img src="../../assets/image (493).png" alt=""><figcaption></figcaption></figure>


2.  Drag off of the Return Value pin and Promote to Variable and (optionally) rename the variable to OSCServer.<br>

    <figure><img src="../../assets/image (494).png" alt=""><figcaption></figcaption></figure>

    <figure><img src="../../assets/image (495).png" alt=""><figcaption></figcaption></figure>


3.  Then add **Unbind All Events from On Osc Bundle Received** and then add **Bind Event to On Osc Message Received**.<br>

    <figure><img src="../../assets/image (496).png" alt=""><figcaption></figcaption></figure>


4.  Drag off the Event socket, type **Create Event.**   
    Then in the dropdown select **Create a matching event.**  
    <br>

    <figure><img src="../../assets/image (498).png" alt=""><figcaption></figcaption></figure>
5.  **Rename** the event to **OSCMessageReceived** and press **Compile Blueprint.**<br>

    <figure><img src="../../assets/image (500).png" alt=""><figcaption></figcaption></figure>


6.  Drag off the Message pin and promote to a variable. The default name will be Message, we'll keep it the same for now. <br>

    <figure><img src="../../assets/image (501).png" alt=""><figcaption></figcaption></figure>


7.  Drag off that node and Get OSC Message Float at Index, do this three times.   
    For the Index, we'll use 5,6 and 7.

    <figure><img src="../../assets/image (502).png" alt=""><figcaption></figcaption></figure>

    :bulb:Remember, the numbers that correspond in Live FX are the following from the top dummy layer:

    <figure><img src="../../assets/image (88).png" alt=""><figcaption></figcaption></figure>
8.  From the left-side, drag over the Message Variable and select Get Message. <br>

    <figure><img src="../../assets/image (503).png" alt=""><figcaption></figcaption></figure>


9.  From that variable, connect it to the three Get OSC Message Float At Index. <br>

    <figure><img src="../../assets/image (504).png" alt=""><figcaption><p><br></p></figcaption></figure>


10. Draf off the execution pin of the last node, **Uncheck Context Sensitive** and search for **Set Relative Rotation**. Choose the **Transformation>Set Relative Rotation.**<br>

    <figure><img src="../../assets/image (505).png" alt=""><figcaption></figcaption></figure>


11. Right-click on New Rotation and select **Split Struct Pin**.<br>

    <figure><img src="../../assets/image (506).png" alt=""><figcaption></figcaption></figure>


12. Drag the Value from **5 to the Z**, **6 to the Y**, and **7 to the X**. <br>

    <figure><img src="../../assets/image (507).png" alt=""><figcaption></figcaption></figure>


13. Drag your Directional Light from your scene into the blueprint. Then from the Blue output pin, connect that to the Target of the Set Relative Rotation. This will automatically create a node in between. <br>

    <figure><img src="../../assets/image (508).png" alt=""><figcaption></figcaption></figure>

    <figure><img src="../../assets/image (509).png" alt=""><figcaption></figcaption></figure>



## Control in Live FX

Back in Live FX, to control the X, Y, and Z, you click on the top layer, select the Canvas menu at the bottom left, and then you can use the Rotate X, Y, and Z to control the Sun in Unreal Engine (must be in play mode). <br>

<figure><img src="../../assets/image (511).png" alt=""><figcaption></figcaption></figure>

## Custom Blueprints

You can create a blueprint and add many components to it, then you can go to the construction script and do some custom things to have one variable effect multiple components in different ways, in this example, multiplying the intensity variable so that it would be 10x the number that goes to

<figure><img src="../../assets/image (510).png" alt=""><figcaption></figcaption></figure>

Here is another example. For headlights in a city scene, we used a blueprint called "00\_BP\_Headlights",  which is a simple actor blueprint with a single Spot Light component.

Inside of each vehicle blueprint, we brought in this blueprint twice, these two act like the headlights.

In the Level blueprint, we Get OSC Message Float At Index, then Get All Actors Of Class. We select the class 00\_BP\_Headlights, then add a For Each Loop, and set the intensity to the Value set in the OSC message.

<figure><img src="../../assets/image (521).png" alt=""><figcaption></figcaption></figure>

