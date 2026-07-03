# Live FX Nodes

Live FX contains all the available file-reader and effect plug-in nodes in the Assimilate Product Suite. There are however a number of nodes only for available in Live FX. These nodes are discussed in the part of the manual. Also, some nodes that are available in the regular Product Suite but do have extra meaning in a live context are included here .

### Video Capture Node <a href="#video-capture-node" id="video-capture-node"></a>

At the heart of Live FX is the Video Capture node which captures a live feed through the Video IO interface. The Video IO interface supports SDI, NDI, certain USB cameras and Spout/Syphon GPU sharing with other applications. For the Video Capture node to be able to use any of these interfaces, you need to first enable and configure the interface through the Video IO Configuration panel which can be opened from the startup screen or from within the Player - Settings menu.

In the Video IO panel is explained in detail in the generic part of the manual but in general:

* Select the **Device** you want to use from the dropdown at the top of the panel and make sure you explicitly **Enable** the device.
* At the Video IO Channels section of the panel, Enable one or more **Input Channels**. Depending of the type of device you can also select a specific source:
  * For NDI inputs, use the dropdown to the right of the channel row. This shows a list of all active NDI streams on the local network. You can also enter one or more Ip addresses in the textbox next to the refresh button to search for streams outside the local network.
  * In the case of Spout/Syphon GPU sharing, the source list will show all currently available textures that are shared by other applications. Alternatively to selecting a specific source, you can select \<auto> as source which means that input channel 1 will link to the first available texture, channel 2 to the second and so on.

On Video Capture node, you can select the feed form the list of active **Devices** and from the list of active input **Channels** with that device. If the input is an SDI channel and the input is coming from a camera in the **Camera** dropdown list, then select that camera so the node can properly interpret the metadata that is send with the SDI stream.

The **Auto TC Sync** option allows you to synchronize multiple captured feeds based on their timecodes by buffering frames until all feeds produced the frame with the same timecode. Note that the setting is linked to the selected capture channel, not to the capture node (you can have multiple capture nodes that all link to the same channel). Also note that if you enable auto-sync on multiple channels and one channel fails to produce real-time frames, this will stall the other channels. If the timecodes of the various feeds differ too much, auto sync is ignored.

Alternatively, to the Auto-Sync you can also set a manual delay with an individual feed, in milliseconds. This is useful when you capture multiple feeds from different sources which do not have (similar) timecodes.

#### Full vs Video Range <a href="#full-vs-video-range" id="full-vs-video-range"></a>

In the Video IO panel, you set which YUV -> RGB matrix to use for an SDI device: either a video- or full range matrix. Different cameras require different settings when outputting a log-signal that is captured in Live FX. For most common cameras this is the matrix that should be used:

* Video range (rec709): ARRI, Canon, RED
* Full range (rec709): Sony, Panasonic

If you have a different camera then check the documentation with that camera to make sure what matrix to use when capturing the signal. Note that when capturing a linear signal (rec709) from a camera you should always use a video-range matrix.

### Projection Node <a href="#projection-node" id="projection-node"></a>

(Live FX Studio)

A Projection node creates a projection image from its media input based LED Wall shape and position coming from the Stage Manager and the camera position. There are two types of projection nodes: 2D->wall and Eq->Wall. As the name already suggests each, depending on the type of media (2D or Equirectangular 360 media) that you want to project onto a LED wall, use one or the other.

#### 2D->Wall <a href="#id-2d-wall" id="id-2d-wall"></a>

**Camera/Wall**

The 2D->Wall can function without the **Link to Stage Manager** or without **Link to Shot Camera** (tracker). If you disable the link options you can set all the properties specific for this node, including loading an .obj file with the shape of the LED wall. However, it makes more sense to have all that data stored in the Stage Manager once. In that case you only select which wall from the active stage configuration to use from the dropdown. Note that if you change the active stage or when you change the labels of the wall in the active stage in the Stage Manager, you might have to select the correct wall from the dropdown again.

There are several things you can control besides the Stage Manager and Shot camera. The **FoV factor** allows you to extend the field of view that is used from the shot camera. This is useful for frustum highlighting. By extending the FoV you create a bit of slack between the projected frustum and the actual frustum of the physical camera and as such prevent that the camera records part of the frustum highlight (or rather outside frustum dimming).

Besides using the 2D->wall node for projecting an 2D image, you can also use it to generate an alpha matte of the camera frustum. You can then use this on a layer of an Eq->Wall projection to grade the frustum. Use the Invert Alpha option to grade inside or outside the frustum.

**Background**

If the camera frustum does not extend the full wall, the 2D->Wall node can extend its projection to cover the full wall in different ways. You can select a way from the Background tab of the plug-in controls.

* **Extend Foreground**. Enabling this option will extend the color of the border of the frustum over the rest of the wall.
* By default, the image of the inner frustum is taken and repeated, using the **Fit** option, to extend it on the full wall. Alternatively, you can use the Scale and Offset controls to adjust the display. You can also add a different shot to the Background input of the projection node (through the Inputs menu) to be used to fit or scaled on the outer frustum display.
* If the shot that is added to the Background input of the projection node is an equirectangular shot and is flagged as such, then you can use the equirectangular (**Pan**, **Tilt**, **Roll**) controls to display the correct part of the shot.

Use the Gain control to dim (or if needed to brighten) the outer frustum from the inner frustum display.

#### Eq->Wall <a href="#eq-wall" id="eq-wall"></a>

The Eq->Wall projection plug-in is similar to the 2D->Wall plug-in, except it takes in an equirectangular image to project. As such, it does not do any frustum highlighting. It does however have the option to do a Sphere- or a Dome projection, using the settings on the second tab of the plug-in controls.

* Camera Sphere (left). The (center of the) equirectangular sphere moves with the (physical) camera (tracker). The projection is always made from the center of the sphere.
* Dome (right). The (center) position of the half-sphere (dome) is fixed and the projection camera moves with the physical camera (tracker) inside a dome. From that position, the projection is calculated for the LED walls.

For the **Dome** projection there are additional settings to consider. Use the **XYZ** controls to set the position of the center to the dome. The **Radius** sets the size of the dome. This size is an estimate of the actual size of the image scene. The radius is used to determine what a meter position change of the camera means inside the dome. Use the **Floor** setting to adjust the position where the sphere is split.

The **Pan**, **Tilt** and **Roll** controls are used to rotate the full scene. Note that these parameters can also be controlled from the (parent) **Switcher** node (if present), which then controls all underlying projection nodes for each wall in the stage.

### Switcher Node <a href="#switcher-node" id="switcher-node"></a>

The Switcher node comes in two flavors. A basic Switcher node that can have multiple has multiple inputs and can play those back simultaneous to different displays and/or create a video wall of the inputs and play that back on any one of the display. The Projection Switcher node is a derivative of that, which in addition has a series of controls to manage underlying Projection nodes: e.g. to rotate the view of an equirectangular clip at once so that you do not have to go through each of the Projection nodes separately to update the settings.

From the Switcher node controls you can start the Channel Controller panel. From that panel Switcher node configuration is done. The configuration applies to all Switcher nodes, not just the active one.

The Channel Controller has 3 tabs. In the first tab you select the **Active Channel** of the Switcher node and toggle the grade target. **Master-mode** means that the grading controls apply to the Switcher node and as such will affect all its inputs. **Channel-mode** means that the grading controls apply to the active channel.

In the **Display-tab** you set what each display should show of the Switcher node: only the active channel, a specific channel, a videowall of all channels or a stage mosaic. That last option is tied in with the Mosaic that you defined in the Stage Manager.

The **Settings-tab** contains various settings. The border of the active channel in a video wall, text overlays in a video wall, the transition when switching active channels and the display label for channels on the first tab: numbers or the reel-ids of the channel node.

**Projection Switcher Node**

When you use the Create Projection Setup panel (discussed later) and you have multiple LED walls in your stage - a projection node  is created per wall and all of those nodes are combined in a Projection Switcher node. To make it easier to control the settings of multiple Projection nodes, the projection settings are also available from the Switcher node. Adjusting the controls will affect all underlying Projection nodes. Note that you can still adjust the Projection nodes individually if needed.

### Stage Matte <a href="#stage-matte" id="stage-matte"></a>

(Live FX Studio)

The Stage Matte node uses the active stage in the Stage Manager and the (virtual) camera position to generate an alpha-matte. Since the node knows if an LED wall is (partly) within view of the camera, the resulting alpha-matte can be used for creating a set-extension: extend the image on the LED wall where the LED wall stop using the live camera capture.

You can enhance this matte with the **Expand**, **Feather** and **Blend** controls to get the desired edges. The node can take in two inputs and then uses the matte to combine the images: in case of a set-extension the inputs are the live camera capture and the clip that is projected on the LED walls.&#x20;

### Matte Wrap <a href="#matte-wrap" id="matte-wrap"></a>

The Matte Wrap node can be used in combination with a keyer to create a Light Wrap effect.

<br>

The Matte Wrap plug-in detects the edges of the (keyer) alpha can expand it (outward or inward with a negative Size) as well as adjusting the intensity of it by using the Gain. In the example below, the first image shows the alpha from the keyer, the second image shows the alpha that the Matte Wrap generates from that, and the this image show the combined alpha.

You use the Matte Warp in a separate layer after the keyer and (obviously) in the Matte of the layer. You can use the Fill of that layer to explicitly load the background image again, which then can have its own grading to even more accentuate the light wrap effect.

### Live Tracker <a href="#live-tracker" id="live-tracker"></a>

The Live Tracker plug-in node can track a specific objects/sections in an image and make the tracker data available as live link, which in turn can be used elsewhere in your composition shot such as positioning another layer.

It allows you to create any number of point trackers to track a specific object in the image. The XY coordinates of each of the trackers are available as live links in your composite. The data of multiple point trackers is combined to calculate scaling and rotational data, which is then also exposed as live link.

**Add Point Tracker**

Add a new point tracker – the overlay of the tracker becomes visible in the image. Drag the tracker to the object that you want to track. The outer box of the tracker represents the search area. The inner box represents the object to search for. You can adjust the sizes of the boxes by dragging the outer borders. Note that the smaller the boxes the more efficient the tracker works, but the chance of the tracker ‘losing’ the object increases.

**Remove Point Tracker**

Remove the current selected tracker. Select a tracker by clicking the overlay of the tracker. The overlay tracker number highlights in red for the selected tracker.

**Use Relative Position**

With this option enabled, the node will pass the relative position to the live link – meaning the offset from the origin position. The origin position is either set when dragging the tracker to a new position, or by clicking the Set Origin button. If the Relative Position is disabled then the node passes the absolute XY coordinates in the image as live links.

**Smooth**

This applies a smoothing filter over the results of a tracker to filter out any jitter.

**Set Origin**

Takes the current position of all trackers and sets them as origin. If the Relative Position is enabled then the position of the trackers relative to this origin position is passed as live link.

**Track Yaw Pitch Roll**

If more than 4 trackers are active, this option tries to calculate a 3 dimension rotation from the tracker results. This option presumes that the trackers all track an object that have the same relative distance from the camera. This distance is entered as Z Value (meters) in the corresponding control.

**ArUco Roll**

With this option enabled you indicate that the tracked region contains a so called ArUco marker. In that case, the Live Tracker will not just track the xy position of the search region within the image but also try and calculate the angle of the marker. Although theoretically it can determine the rotation of the marker over 3 different axis, currently only the roll-angle of the marker is passed as live link.

### Lens (Un)distort Node <a href="#lens-un-distort-node" id="lens-un-distort-node"></a>

The Lens (Un)distort plug-in node can be used to distort or undistort an image based on lens distortion parameters or by using a UV-map.

Use the top dropdown to switch between **Distort** and **Undistort**. The various **Distortion parameters** (P1, P2, ..) can be obtained from:

* a camera calibration and storing / applying the data from a camera profile,
* from some of the supported live link camera trackers,
* from other software by simply entering the values manually.

Use the **Crop** option to scale the image to remove any black borders that are created by the (un)distort. The **Crop** only works with the distortion parameters, not with an external UV or ST map.

The **Save XML** and **Load XML** buttons store or load the distortion parameters to / from an external file on disk.

Alternatively to using the distortion parameters, you can also use a **UV map** or an **ST map**. Use either the **Load** option to select a map image from disk or drag drop an already loaded map shot to the input of the Lens (Un)distort node in the Inputs menu.

If you loaded a Map through the **Load** button, you can clear it by using the **Remove** button.

### Spout/Syphon GPU Share & Sender <a href="#spout-syphon-gpu-share-and-sender" id="spout-syphon-gpu-share-and-sender"></a>

Spout (windows) and Syphon (mac) are protocols to share GPU textures (images) between applications. Sharing images directly on the GPU limits latency to its minimum. Do note however that Spout/Syphon do not have any sync mechanism: an application always just takes the 'latest' image shared. An receiver application might already have advanced to a next frame, while the sender application has not - or vice verse. In general, when both application both run in real time (and at the same frame rate) the latency should be a maximum of 1 frame.

There are two versions of the Spout/Syphon plug-in: The **GPU Share** plug-in and the **Sender** plug-in. In the GPU Share plug-in you select one of the available textures from the **Server** dropdown. If the texture of an application is not listed, try using the **Reload** button to refresh the list. Once the texture is loaded, you can size the plug-in node to the texture size by enabling the **Auto-resize** option. Use the **Invert-image** option to flip the image in case the sending application has a different orientation for its textures. In the bottom label the **format / bit depth** of the shared texture is displayed.

Note that Spout/Syphon GPU texture share is also available through the VideoIO framework. The advantage of using it through the VideoIO framework is that you can also record any stream coming in through Spout/Syphon. The plug-in version is sometimes more convenient in an ad-hoc setup as it takes less configuration on forehand.

The Spout/Syphon Sender version of the plug-in is currently not available through VideoIO. You can instantiate the plug-in anywhere in your composition to share the image with another application. After instantiating the plug-in, enter a label for the shared image to be easily recognizable in the other application.

### RealSense Depth (deprecated) <a href="#realsense-depth-deprecated" id="realsense-depth-deprecated"></a>

The Intel RealSense depth camera uses Lidar to generate a depth image. The RealSense depth plug-in captures this image and can generate a matte from it, which can be combined with an RGB camera image.

Note that the RealSense depth camera is only available for Windows. Further note this node was implemented as an experiment but that in the end the resolution of the camera, as well as the accuracy of the depth information and in dealing with the reflection of certain surfaces proved to be limited. Nevertheless – the plug-in offers a way to start using new technology in a creative way. The aim of the implementation was to use it as an overlay on the actual camera image and as such to create a dynamic mask based on the depth information which potentially could replace green screen keying. Without newer and better versions of the depth camera, further development was stopped.

**Mode**

* Alpha Mask. Use the Threshold distance to generate a matte with everything further away than the threshold being fully opaque.
* Depth as Alpha. Put all depth information in the alpha channel of the image. Use the input shot of the plug-in for the RGB part.
* Depth as RGB. Generate RGB image based on the depth information.

**Max Distance**

The max distance is used to better reflect the depth range in the alpha or RGB shades.

**Threshold**

Used with the Alpha Mask mode to generate a matte from all that is closer or further away than the threshold distance. Used to mimic a green-screen setup, without the green-screen.

**Invert Mask**

Inverts the alpha values / mask related to the distance.

**Smooth Radius**

Smooth the alpha values to get rid of jitter along the edges of objects.

**Calibrate**

Enable this setting to get an RGB representation of the depth info so it is easier to align the depth image with the actual camera image.

**Scale & Offset**

Scale and offset the depth image to match the actual camera image.

### Eq->2D Transformer <a href="#eq-2d-transformer" id="eq-2d-transformer"></a>

The Eq->2D Transformer node takes in an equirectangular image and outputs a 2D image based on a camera rotation and field of view that you set.

The camera rotation and field of view can also be **linked to the shot camera**, which in turn can be linked to a camera tracker. Optionally you can also move the inside the equirectangular sphere by adjusting the **XYZ position**. Note though that since this is primarily used with pre-recorded plates, adjusting in xyz too much might lead to a distorted image.

To also link the XYZ position to the shot camera, enable the **Incl. Position** option. Since inside a sphere the standard radius is 1, you can adjust the Scale to use a more proper range for XYZ adjustments in meters.

### USD Nodes <a href="#usd-nodes" id="usd-nodes"></a>

(Live FX Studio)

USD (Universal Scene Description) is a format for 3D elements and scenes. The USD node load these elements / scene and uses the Pixar Hydra rendered, that is included with the installation, to render a 2D image based on the camera and object position and a range of render and lighting options. This allows you to include 3D virtual elements into your (live) composition.

Although the USD node has its own camera position controls, you can also link to the active shot camera as to fully integrate it with your composition. When you add an USD node on a layer to your composition, ensure that the layer is set to **Relative**, so that it 'sticks' to the camera: the USD node makes sure that at any one time the correct perspective of the 3D item is rendered to a 2D image.

Note that USD elements / scenes can be loaded directly from file just like any other media format.

#### General <a href="#general-3" id="general-3"></a>

**Position / Rotation**

This determines the position and rotation of the scene. As mentioned above, if the USD node is added on a layer in a composition, the layer should be set to Relative. That way the USD node origin aligns with the origin of the 3D layer composition and virtual camera model.&#x20;

**Scale**

Some USD scenes might be specified in a different dimension than in meters. Use the **Scale** to convert it into meters so it aligns with camera tracking.

**Render Quality**

The higher the quality setting the better the output image but also the higher the potential performance hit for the whole composition.

**Enable Lights**

Toggle the lights as defined in the USD on/off.

**Scene Lights**

Toggle additional lights (see last tab) on/off. The effect depends on the specific scene.

**Enable Materials**

Toggle the use of textures and reflections as defined in the USD on/off. Can be used to affect performance.

**Equirectangular**

This option renders the scene 6 times in all directions and generates an equirectangular output from it. The equirectangular output can e.g. be used for projection to multiple LED walls or to render out a scene and use the rendered output directly.

**Grid**

Toggle the display of a floor-level grid on/off.

#### Camera <a href="#camera" id="camera"></a>

**Position / Rotation**

Position the camera that is used to render the 2D image of the 3D scene.

**Auto-position**

Option to auto position the camera so that the scene is captured completely in the 2D image.

**Link to Shot camera**

This links the render camera to the shot camera, which in turn is linked to a camera tracker and controls the full composition.

**FoV Factor**

Only available when the USD render camera is linked to the shot camera and is a way to extend the camera frustum a bit to create some slack on the physical camera frustum on an LED wall projection to that the edge of the displayed frustum is never captured by the physical camera.

**Planes**

This can be used to filter out near or far away objects from the render. By using 2 versions of the same scene and adjusting the front / back planes of each you can potentially create a front and back plate that can be used with a green-screen (middle) plate.

#### Lights <a href="#lights" id="lights"></a>

The effect of the **Ambient**, **Specular**, **Shininess** color as well as the **Dome Light** toggle depend on the setup of the USD scene. Toggle the **Auto-Position** off to be able to adjust the direction of the light in the scene manually by using the **XYZ** controls.

### NOTCH Blocks <a href="#notch-blocks" id="notch-blocks"></a>

(Live FX Studio)

Notch Builder ([https://www.notch.one/](https://www.notch.one/)) allows you to create 3D elements or completes scenes which can be exported as Notch Blocks. Live FX can load such a Notch Block as part of a (live) composition shot, where the various parameters of the notch block can be set, animated or linked to a live source and as such be combined with a live camera feed.

A Notch Block can be loaded directly from disk or by first selecting a Notch Block plug-in node through the plug-in browser in the player. When loaded through the plug-in browser, you are asked to select a specific Notch Block \*.dfxdll file from disk. To be able to render the content of a Notch Block you need the Notch render engine installed as well as a Notch license. Certain Notch Blocks can take some time to load, the first time you open them. Loading a project with the Notch Blocks nodes in it, does not take that much extra time. However, the first time a Notch Block needs to render an image in the player it might take longer.

Each Notch Block has its own set of parameters / controls to. However, all Notch blocks have the same 3 general controls: Height and Width, which determine the size of the output of the Notch Block. Note that by default the size if the same as the size of the Live FX node but can be adjusted to e.g. a smaller size to speed up rendering (while you can then upscale the node to the composition resolution). The third general control with each Notch Block is the Layer selection. A Notch Block can contain one or more different layers of which only one can be selected at any one time. Note however that you could instantiate multiple Notch nodes in a single composition, each with a different layer selected.

Certain Notch Blocks can contain properties that are exposed as Live Links (similar to the output of the Live Tracker). These Live Links can in turn be used to control and steer other aspects of the composition. Check the Live Animation editor for available Notch Block parameters.

### NotchLC <a href="#notchlc" id="notchlc"></a>

Next to rendering Notch Blocks, Live FX also supports playback of (QuickTime) media encoded with the NotchLC codec. The NotchLC codec is used to ensure real-time playback due to its GPU optimized encoding model. There is also a NotchLC encoder available for SCRATCH to transcode any media into this format. Contact support on the known email address for more information
