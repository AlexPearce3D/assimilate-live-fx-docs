# Part 3: Projection Mapping on multiple walls

Here is the Youtube Video for this part, if you rather watch, than read  ;-) .

{% embed url="https://www.youtube.com/watch?v=x4dT6S3MaiM" %}

In this part of the tutorial series, we discuss more complex stage setups with multiple LED walls and LED wall processors. To a certain extent this is just up-scaling of what we already covered in the first two videos of this tutorial series. However, it does also add some extra complexities of which you need to be aware.



When dealing with multiple LED walls or with multiple LED wall processors that feed into a single big wall, Live FX Studio has to send multiple images through different outputs at the same time. The one item to do this in Live FX Studio is the so-called Switcher node. This node takes in multiple inputs and generates a specific image for each display output of the system.

Let’s first have a look at this node outside of the context of projection.

Here we loaded 3 shots which we all select by holding down the control key, and next we wrap them into a switcher node, using the Switcher button in the menu below. This gives us a new Switcher node. Let’s place that on the Construct and then double click it to open it in the player.

At first glance this just plays the first shot of the three that we wrapped into it. Let’s take a close look at the node menu. From here we can open the so-called Channel Controller. Note that you can also open this panel from the Live FX Studio menu.

The channel controller has 3 tabs. Channels, where you set the active channel, that you want to work, or grade on. Displays, where you map inputs to a specific display output. And on the settings-tab you can set various display preferences.

Let’s start on the Channel tab. Here you can select the active channel from the available inputs. The active channel in this context means, the node that is displayed in the primary viewport and is active in the menu below. Although this also depends on the Grade Target setting. When set to Channel then you are grading on the selected active channel input. This way you can color grade each input separately. If however you switch to Master, then you are grading on the Switcher node itself, and the grade on this is then applied to all inputs.

To a certain extent the Switcher node is just like any other effect node. If we open the tree-view, we can see the switcher node at the top and each of the inputs below.

When looking at the Inputs menu, you can see the individual input shots that we are feeding into the switcher node. From here we can also add new inputs to the switcher by using the Fetch option, selecting a new shot and dropping it in the fourth input slot. As you can see, the Channel Controller automatically updates to reflect 4 inputs, same as the node tree.

Now, what sets the Switcher node apart from other effect nodes is that you can tie its inputs directly to a specific display output. Here on the Displays tab all outputs are listed and with each output, you can select which input is to be sent to that display.

The easiest way to see that at work in this tutorial is by opening the Split view by pressing Quick key D.

Now, we have set the Primary display to show the active channel. We can set the Split view to always show the third channel. If I now change the Active channel then you can see the change on the primary view but the split view remains the same.

Next to selecting the active channel or a specific channel, you can also select the Video Wall option, which shows all the outputs together.

The Stage Mosaic option we discuss later as that is directly related to LED wall projection.

For now, let conclude this explanation of the Switcher node by a quick look at the settings tab. Most of the settings here relate on how the video wall is displayed. Next to that you can set a Dissolve transition effect when switching the active channel.

Lastly, the Label option determines the labels on the channel buttons on the first tab. When we set this to Reel-ID and switch to the channels tab then you can see the labels changed to the reelid metadata item of each of the input shots.



Back to the main topic: LED wall projection and how to deal with multiple walls.

<figure><img src="../../.gitbook/assets/Switcher Node.png" alt=""><figcaption></figcaption></figure>

Now that we have seen the Switcher node in action, let’s create a setup with multiple LED walls. Open the Projection setup panel and from there open the Stage Manager. For this tutorial we start with a single wall that is slightly curved, which makes it easier to distinguish from a new wall that we are going to add.

Hit the Create button and let’s create a ceiling panel. Use the default size and resolution. And hit ok. Let’s then adjust the position so that it is above the backwall panel. There we go.

Now, the next thing to do is to map the wall to a specific output. For that we switch to the Mapper tab of the Stage manager. We have our main back wall, which is mapped to the dual head output, directly on the GPU. \[show] Let’s map the ceiling wall to the SDI output.

Note that when using different types of outputs, like mixing GPU and SDI outputs, the individual walls will likely have different latency levels. For demonstration purposes we’ll continue with this setup. Further into this tutorial, we will discuss other types of mappings to use.

For now, exit the stage manager and we’re back in the setup panel. Here we select the equirectangular shot that we loaded earlier which automatically gives us a Spherical projection. Let’s select our tracker, as well as enable the frustum highlighting. This gives us a similar projection as in the previous part of the tutorial, but now for two LED walls. Click Create and we are in the Player.



Let’s first have a look at the node tree to view the composition shot that was created. Here we see our main top node with two branches below it. Each branch looks suspiciously like the projection setup that we created in the previous part of the tutorial series. We have a projection node, with the source shot going into that. And we have a layer for frustum matte. One difference is that the layers for the inner- and outer-frustum are up one level.

And that one level up node is indeed a Switcher node. Or in this case a derivative of the Switcher node with some extra functionality for dealing with multiple projection nodes, which has two inputs: The respective Equirectangular to wall nodes for each of the two walls in our stage.

Let’s look at all the elements more closely. To do that, let’s switch to split view, and open both the Channel controller and the Stage Manager from the Live FX menu. Now, that are a lot of panels, and we need to resize the views a bit to fit all. To pan a view, hold down space bar and drag. For scaling hold down Alt and drag. You can collapse any of the panels by double clicking anywhere in the title bar of the panel.

Note that most of the time you do not need all these elements visible together all the time and can just trust the elements working as supposed to without monitoring. For this demonstration we do want to show them all though.

So, let’s start with the channel controller. Here we see the two inputs, representing the different mapped LED walls. If we switch between them, we can clearly recognize the main curved wall and the ceiling wall. Looking at the Display tab we need to ensure that each output receives the correct input. We want the dual head to output the main wall from the first channel. And we want the SDI channel to output the ceiling wall. To have a similar view, we leave the primary output to the active channel which is currently the first channel. And we set the split view to display the ceiling wall output.

Now, as we can see in the Channel controller, the grade target is currently set to Master. This means that the grading controls apply to the Switcher node and hence will affect both inputs, or walls so to speak. As you can see in the layer stack, we can see the inner and outer frustum layers that were created on the Switcher node. When we adjust the outer frustum a bit, we can clearly see the effect on both led walls.

When selecting the Channel as grade target, you can see that the layer stack no longer shows the frustum layers. We can create a new layer here, adjust the grade on that and we can see that this only affects the main led wall. Let’s return to Master mode and see the frustum layer again.

Using the Grade target in the Channel Controller is like navigating the node tree with the view lock. The lock is currently enabled and when I now select the projection node of the main wall, we can now see the layer again that we created through the channel mode. In that sense, the channel controller just offers an alternative and quick way of navigating the node tree. Back to the top node.

Next thing we want to focus on is the camera tracker. This is linked to the Switcher node as we can see in the Camera menu. From there the camera position ripples down to the individual projection nodes below it. When we select the projection node of our main wall, we can see that the camera of that shot is not active, which means that it inherits the settings of the camera of the node above it.

Now if we rotate the camera around, we can see the frustum move and when we tilt the camera up, we can also see the frustum appear on the ceiling wall. Let’s also view the stage manager to actually see the camera rotating.

So, as you can see, effectively to support multiple walls all we had to do was to create the extra wall in the stage manager and map that to an output and then ensure that the output is indeed routed correctly in the channel controller.

Now the last thing to look at is the node menu of the Switcher node. As mentioned, the switcher node used with projection is not a vanilla one, but a derivative with some extra functions.

If you remember correctly, when we discussed the spherical projection, we showed you how to rotate the sphere to get the correct orientation. We did that on the projection node. Now to prevent that you have to adjust the orientation on each of the projection nodes underlying the switcher node, the orientation controls are duplicated on the switcher node. When we adjust the pan or tilt here, then that affects both - the projection node of the main wall and the projection node of the ceiling wall. We can actually see this if we use the node tree. The values we dialed in on the switcher node are replicated on the individual projection nodes. This can save you quite a bit of time setting up your scene, as dialing in another portion of the background is a single click operation.

Now, before we move on to mapping multiple walls to a single output inside the stage manager, there are some other things to understand about this setup.

First, you need to be aware that both of the projection nodes for the different walls use the same instance of the source media. We can show that they both use the same instance of the media by selecting one of the source nodes there and then adjusting the primary grade. As you can see the image on the other wall also changes.

It is very important that the different walls use the same instance of the source node instead of a copy of the node. This saves a lot of performance on playback. Using a copy basically means playing back the same clip twice – so using an instance instead means that the system only has to decode the clip once, and also apply the grade on the source node once, instead of multiple times. To prevent using copies, always create the projection setup with the wizard panel in the construct. Creating the composition manually is doable but takes a lot of extra steps to prevent using copies.

On the other hand, in some cases you might want to use a different shot for a ceiling or side wall, and in some cases you might even not need a projection node for that as in most cases these walls are merely used for light reflection. So for instance in our current setup, we can decide that we want a completely different sky on the ceiling panel. We select the fetch option and navigate to the construct where we loaded the sky that we want to use. Select it and this time, rather than dropping it in the Input menu, you can also directly replace the shot in the node tree by hovering over the shot that we want to replace and select the replace option. In this case we want to actually replace the projection node with the new source node, just to keep things simple. There we go, now we have our new sky

&#x20;

&#x20;

Ok, now it’s time to dive in a little deeper on alternative ways of mapping multiple led walls. As we said earlier mapping one wall to the dual head on the GPU and another through a video-io channel is not always wanted due to differences in latency. However sometimes, if the resolution of the wall is too high for a single led wall processor you need map the signal in such way that it feeds multiple processors – and with the same latency, of course. Consider the following case.



Here we have an LED wall with a resolution of 4928 by 1936, driven by 2 LED wall processors. In addition, we have smaller side panel of 1056 x 1056, which is driven by one of the 2 processors.

What we want to do is go out from the graphics card to both LED processors to keep latency to a minimum, rather than using Video-IO. And the solution to do this is two-fold. First, we are going to use Nvidia’s mosaic functionality that covers 2 physical outputs from the graphics card to the LED processors, and presents them as one big virtual display to the operating system and as such to Live FX Studio. Secondly, we are going use the Nvidia mosaic display as the dual head output of Live FX Studio and map the two walls onto that display.

(show how to create nvidia mosaic. Show link to nvidia document. Tell restrictions / important aspects. 16k x 16k limit but can split wall into sections, framerate, save / load edid).

Once the Nvidia mosaic is created, make sure to enable the dual head setting in the system settings.

In case the system has more than 2 displays attached, you can change the default selection for the primary UI and Dual Head by setting which index to use here in the advanced system settings. For now we’ll leave things at their default, exit the system settings and enter back into our project.

Our first stop is again the stage manager, which we open from the projection setup panel. In the stage manager we see our two walls, which we want to map to the dual head output – which is the nvidia mosaic view.

In the mapping tab we select the dual head display and because we want to map multiple walls onto that, we need to enable the mosaic option.

Please note that even through this button is labelled Mosaic and is often used together with an nvidia  virtual mosaic display, it is not directly related. All this option says is that you want to map multiple walls onto the single display output. This can also just be a 4K Video-IO display onto which you map multiple HD-sized walls for instance.

To actually map a wall, just select it and hit the Map option. Then, select the other wall and also click the Map option. So now both walls are mapped onto the display, however, both are mapped to the middle of the display. The next step is to offset the mapping to be in line with how each LED processor is outputting its input to the physical wall.

This part very much depends on how you mapped the tiles of your wall in the led processor. In our case, we offset the main wall a bit up but leaving it exactly in the middle and then we offset the side wall to the lower right corner of the display output.

As said, it is important that this mapping is exactly in line with the mapping of physical tiles inside the LED processors. To ensure the mapping offsets are correct you can use the Preview option. When selecting the Preview, the player is opened if you are not already in the player, and a test pattern is generated, based on the specifications of your wall, including the resolution and the number of tiles as defined with each wall.

The test pattern features a single pixel line pattern outlining the tiles, which all should be visible on the actual wall. If a line is not visible, then either the mapping offset is incorrect or the wall specifications are incorrect. Of course, if the tile-mapping inside the led processor is not correct then any setting in Live FX Studio cannot fix that.

So, all ready with our mapping. Click the R-button next to the Preview button to exit out of the player. Next, we can close the stage manager and again create a new projection composition.

Let’s use our 360 shot and spherical projection, set the camera profile and tracking, enable the frustum highlight and click create. Back into the player.

Since we have two led walls, the composition uses a switcher node as you can see here in the node-tree view. Now, the first thing we need to check is that the dual head – which is our virtual mosaic display - gets the correct output. Open the Channel Controller from the node menu and select the Display tab. Now with the Dual head, we need to make sure that the Stage Mosaic is selected. Let’s for demonstration purposes also do that for the Split view.

And if we now open the split view – hotkey “D” - you can see the mosaic that we created in the mapper tab of the stage manager, with the main wall in the center and the smaller side wall to the bottom right. This is what is being sent out to the dual head. The dual head in turn is an nvidia mosaic of two displays, meaning that each physical display gets one half of this view. That is then what the led processors get, which in turn feed their part of the image to the correct part of the main wall and to the side wall.

That concludes this part of the tutorial on using multiple led walls with Live FX Studio. Note that your setup might differ from the one we used in this demonstration. However, it should be clear that using the various mapping options – from nvidia mosaic to the stage manager and the options you will have in the led processor, you should be able to create a suitable projection setup for your environment.
