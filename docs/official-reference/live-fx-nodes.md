# Live FX Nodes


<p>Live FX contains all the available file-reader and effect plug-in nodes in the Assimilate Product Suite. There are however a number of nodes only for available in Live FX. These nodes are discussed in the part of the manual. Also, some nodes that are available in the regular Product Suite but do have extra meaning in a live context are included here .</p>
<h3 id="video-capture-node">Video Capture Node</h3>
<p>At the heart of Live FX is the Video Capture node which captures a live feed through the Video IO interface. The Video IO interface supports SDI, NDI, certain USB cameras and Spout/Syphon GPU sharing with other applications. For the Video Capture node to be able to use any of these interfaces, you need to first enable and configure the interface through the Video IO Configuration panel which can be opened from the startup screen or from within the Player - Settings menu.</p>
<p>In the Video IO panel is explained in detail in the generic part of the manual but in general:</p>
<ul>
    <li>Select the <strong>Device </strong>you want to use from the dropdown at the top of the panel and make sure you explicitly <strong>Enable </strong>the device.</li>
    <li>At the Video IO Channels section of the panel, Enable one or more <strong>Input Channels</strong>. Depending of the type of device you can also select a specific source:
    <ul>
        <li>For <span class="Highlight">NDI inputs</span>, use the dropdown to the right of the channel row. This shows a list of all active NDI streams on the local network. You can also enter one or more Ip addresses in the textbox next to the refresh button to search for streams outside the local network.</li>
        <li>In the case of <span class="Highlight">Spout/Syphon GPU sharing</span>, the source list will show all currently available textures that are shared by other applications. Alternatively to selecting a specific source, you can select &lt;auto&gt; as source which means that input channel 1 will link to the first available texture, channel 2 to the second and so on.</li>
    </ul>
    </li>
</ul>
<p><img alt="" src="../../assets/official-reference/live-fx-user-guide/LFX_Plugin_Capture_v02.png" /></p>
<p>On Video Capture node, you can select the feed form the list of active <strong>Devices</strong> and from the list of active input <strong>Channels </strong>with that device. If the input is an SDI channel and the input is coming from a camera in the <strong>Camera</strong> dropdown list, then select that camera so the node can properly interpret the metadata that is send with the SDI stream.</p>
<p>The <strong>Auto TC Sync</strong> option allows you to synchronize multiple captured feeds based on their timecodes by buffering frames until all feeds produced the frame with the same timecode. Note that the setting is linked to the selected capture channel, not to the capture node (you can have multiple capture nodes that all link to the same channel). Also note that if you enable auto-sync on multiple channels and one channel fails to produce real-time frames, this will stall the other channels. If the timecodes of the various feeds differ too much, auto sync is ignored.</p>
<p>Alternatively, to the Auto-Sync you can also set a manual delay with an individual feed, in milliseconds. This is useful when you capture multiple feeds from different sources which do not have (similar) timecodes.</p>
<h4 id="full-vs-video-range">Full vs Video Range</h4>
In the Video IO panel, you set which YUV -&gt; RGB matrix to use for an SDI device: either a video- or full range matrix. Different cameras require different settings when outputting a log-signal that is captured in Live FX. For most common cameras this is the matrix that should be used:
<ul>
    <li>Video range (rec709): ARRI, Canon, RED</li>
    <li>Full range (rec709): Sony, Panasonic</li>
</ul>
<p>If you have a different camera then check the documentation with that camera to make sure what matrix to use when capturing the signal. Note that when capturing a linear signal (rec709) from a camera you should always use a video-range matrix.</p>
<h3 id="projection-node">Projection Node</h3>

<p>(Live FX Studio)</p>

<p>A Projection node creates a projection image from its media input based LED Wall shape and position coming from the Stage Manager and the camera position. There are two types of projection nodes: 2D-&gt;wall and Eq-&gt;Wall. As the name already suggests each, depending on the type of media (2D or Equirectangular 360 media) that you want to project onto a LED wall, use one or the other.</p>
<h4 id="2d-wall">2D-&gt;Wall</h4>
<p> <img alt="" src="../../assets/official-reference/live-fx-user-guide/LFX_Node2D2wall_v01.png" /></p>
<h5 id="camera-wall">Camera/Wall</h5>
<p>The 2D-&gt;Wall can function without the <strong>Link to Stage Manager</strong> or without <strong>Link to Shot Camera</strong> (tracker). If you disable the link options you can set all the properties specific for this node, including loading an .obj file with the shape of the LED wall. However, it makes more sense to have all that data stored in the Stage Manager once. In that case you only select which wall from the active stage configuration to use from the dropdown. Note that if you change the active stage or when you change the labels of the wall in the active stage in the Stage Manager, you might have to select the correct wall from the dropdown again.</p>
<p>There are several things you can control besides the Stage Manager and Shot camera. The <strong>FoV factor</strong> allows you to extend the field of view that is used from the shot camera. This is useful for frustum highlighting. By extending the FoV you create a bit of slack between the projected frustum and the actual frustum of the physical camera and as such prevent that the camera records part of the frustum highlight (or rather outside frustum dimming).</p>
<p>Besides using the 2D-&gt;wall node for projecting an 2D image, you can also use it to generate an alpha matte of the camera frustum. You can then use this on a layer of an Eq-&gt;Wall projection to grade the frustum. Use the Invert Alpha option to grade inside or outside the frustum.</p>
<h5 id="background">Background</h5>
<p>If the camera frustum does not extend the full wall, the 2D-&gt;Wall node can extend its projection to cover the full wall in different ways. You can select a way from the Background tab of the plug-in controls.</p>
<ul>
    <li><strong>Extend Foreground</strong>. Enabling this option will extend the color of the border of the frustum over the rest of the wall.</li>
    <li>By default, the image of the inner frustum is taken and repeated, using the <strong>Fit</strong> option, to extend it on the full wall. Alternatively, you can use the Scale and Offset controls to adjust the display. You can also add a different shot to the Background input of the projection node (through the Inputs menu) to be used to fit or scaled on the outer frustum display.</li>
    <li>If the shot that is added to the Background input of the projection node is an equirectangular shot and is flagged as such, then you can use the equirectangular (<strong>Pan</strong>, <strong>Tilt</strong>, <strong>Roll</strong>) controls to display the correct part of the shot.</li>
</ul>
<p>Use the Gain control to dim (or if needed to brighten) the outer frustum from the inner frustum display.</p>
<h4 id="eq-wall">Eq-&gt;Wall</h4>
<p><img alt="" src="../../assets/official-reference/live-fx-user-guide/LFX_NodeEq2wall_v01.png" /></p>
<p>The Eq-&gt;Wall projection plug-in is similar to the 2D-&gt;Wall plug-in, except it takes in an equirectangular image to project. As such, it does not do any frustum highlighting. It does however have the option to do a Sphere- or a Dome projection, using the settings on the second tab of the plug-in controls.</p>
<p><img alt="" src="../../assets/official-reference/live-fx-user-guide/LFX_SphereDome_v01.png" /></p>
<ul>
    <li>Camera Sphere (left). The (center of the) equirectangular sphere moves with the (physical) camera (tracker).&nbsp;The projection is always made from the center of the sphere. </li>
    <li>Dome (right). The (center) position of the half-sphere (dome) is fixed and the projection camera moves with the physical camera (tracker) inside a dome. From that position, the projection is calculated for the LED walls.</li>
</ul>
<p>
For the <strong>Dome </strong>projection there are additional settings to consider. Use the <strong>XYZ </strong>controls to set the position of the center to the dome. The <strong>Radius </strong>sets the size of the dome. This size is an estimate of the actual size of the image scene. The radius is used to determine what a meter position change of the camera means inside the dome. Use the <strong>Floor </strong>setting to adjust the position where the sphere is split. </p>
<p>
The <strong>Pan</strong>, <strong>Tilt </strong>and <strong>Roll </strong>controls are used to rotate the full scene. Note that these parameters can also be controlled from the (parent) <strong>Switcher </strong>node (if present), which then controls all underlying projection nodes for each wall in the stage.</p>
<h3 id="switcher-node">Switcher Node
</h3>


<p>The Switcher node comes in two flavors. A basic Switcher node that can have multiple has multiple inputs and can play those back simultaneous to different displays and/or create a video wall of the inputs and play that back on any one of the display. The Projection Switcher node is a derivative of that, which in addition has a series of controls to manage underlying Projection nodes: e.g. to rotate the view of an equirectangular clip at once so that you do not have to go through each of the Projection nodes separately to update the settings.</p>
<p>From the Switcher node controls you can start the Channel Controller panel. From that panel Switcher node configuration is done. The configuration applies to all Switcher nodes, not just the active one.</p>
<p><img alt="" src="../../assets/official-reference/live-fx-user-guide/LFX_ChannelController_V01.png" />&nbsp;</p>
<p>The Channel Controller has 3 tabs. In the first tab you select the <strong>Active Channel</strong> of the Switcher node and toggle the grade target. <strong>Master-mode</strong> means that the grading controls apply to the Switcher node and as such will affect all its inputs. <strong>Channel-mode</strong> means that the grading controls apply to the active channel. </p>
<p>In the <strong>Display-tab</strong> you set what each display should show of the Switcher node: only the active channel, a specific channel, a videowall of all channels or a stage mosaic. That last option is tied in with the Mosaic that you defined in the <span class="Highlight">Stage Manager</span>.</p>
<p>The <strong>Settings-tab</strong> contains various settings. The border of the active channel in a video wall, text overlays in a video wall, the transition when switching active channels and the display label for channels on the first tab: numbers or the reel-ids of the channel node.</p>
<h5 id="projection-switcher-node">Projection Switcher Node</h5>
<p><img alt="" src="../../assets/official-reference/live-fx-user-guide/LFX_SwitcherProjection_v01.png" /></p>
<p>When you use the Create Projection Setup panel (discussed later) and you have multiple LED walls in your stage - a projection node&nbsp; is created per wall and all of those nodes are combined in a Projection Switcher node. To make it easier to control the settings of multiple Projection nodes, the projection settings are also available from the Switcher node. Adjusting the controls will affect all underlying Projection nodes. Note that you can still adjust the Projection nodes individually if needed.</p>
<h3 id="stage-matte">Stage Matte</h3>

<p>(Live FX Studio)</p>


<p>The Stage Matte node uses the active stage in the Stage Manager and the (virtual) camera position to generate an alpha-matte. Since the node knows if an LED wall is (partly) within view of the camera, the resulting alpha-matte can be used for creating a set-extension: extend the image on the LED wall where the LED wall stop using the live camera capture.</p>
<p><img alt="" src="../../assets/official-reference/live-fx-user-guide/LFX_NodeStageMatte_v01.png" /></p>
<p>You can enhance this matte with the <strong>Expand</strong>, <strong>Feather </strong>and <strong>Blend </strong>controls to get the desired edges. The node can take in two inputs and then uses the matte to combine the images: in case of a set-extension the inputs are the live camera capture and the clip that is projected on the LED walls.&nbsp;</p>

<h3 id="matte-wrap">Matte Wrap</h3>

<p>The Matte Wrap node can be used in combination with a keyer to create a Light Wrap effect. </p>

<img alt="" src="../../assets/official-reference/live-fx-user-guide/LFX_NodeMatteWrap_v01.png" />
<br />


<p>The Matte Wrap plug-in detects the edges of the (keyer) alpha can expand it (outward or inward with a negative Size) as well as adjusting the intensity of it by using the Gain. In the example below, the first image shows the alpha from the keyer, the second image shows the alpha that the Matte Wrap generates from that, and the this image show the combined alpha.</p>
<p><img alt="" src="../../assets/official-reference/live-fx-user-guide/LFX_MatteWrap_Example_v1.png" /></p>
<p>You use the Matte Warp in a separate layer after the keyer and (obviously) in the Matte of the layer. You can use the Fill of that layer to explicitly load the background image again, which then can have its own grading to even more accentuate the light wrap effect. </p>

<h3 id="live-tracker">Live Tracker</h3>
<p>The Live Tracker plug-in node can track a specific objects/sections in an image and make the tracker data available as live link, which in turn can be used elsewhere in your composition shot such as positioning another layer. </p>
<p><img alt="" src="../../assets/official-reference/live-fx-user-guide/LFX_LiveTracker_v01.png" /><img alt="" src="../../assets/official-reference/live-fx-user-guide/LFX_LiveTracker_Overlay_v01.png" /></p>
<p>It allows you to create any number of point trackers to track a specific object in the image. The XY coordinates of each of the trackers are available as live links in your composite. The data of multiple point trackers is combined to calculate scaling and rotational data, which is then also exposed as live link.</p>
<h5 id="add-point-tracker">Add Point Tracker</h5>
<p>
Add a new point tracker – the overlay of the tracker becomes visible in the image. Drag the tracker to the object that you want to track. The outer box of the tracker represents the search area. The inner box represents the object to search for. You can adjust the sizes of the boxes by dragging the outer borders. Note that the smaller the boxes the more efficient the tracker works, but the chance of the tracker ‘losing’ the object increases.
</p>
<h5 id="remove-point-tracker">Remove Point Tracker</h5>
<p>
Remove the current selected tracker. Select a tracker by clicking the overlay of the tracker. The overlay tracker number highlights in red for the selected tracker.</p>
<h5 id="use-relative-position">Use Relative Position</h5>
<p>
With this option enabled, the node will pass the relative position to the live link – meaning the offset from the origin position. The origin position is either set when dragging the tracker to a new position, or by clicking the Set Origin button. If the Relative Position is disabled then the node passes the absolute XY coordinates in the image as live links.
</p>
<h5 id="smooth-2">Smooth</h5>
<p>
This applies a smoothing filter over the results of a tracker to filter out any jitter.
</p>
<h5 id="set-origin-2">Set Origin</h5>
<p>
Takes the current position of all trackers and sets them as origin. If the Relative Position is enabled then the position of the trackers relative to this origin position is passed as live link.
</p>
<h5 id="track-yaw-pitch-roll">Track Yaw Pitch Roll</h5>
<p>
If more than 4 trackers are active, this option tries to calculate a 3 dimension rotation from the tracker results. This option presumes that the trackers all track an object that have the same relative distance from the camera. This distance is entered as Z Value (meters) in the corresponding control.
</p>
<h5 id="aruco-roll">ArUco Roll
</h5>
<p>
With this option enabled you indicate that the tracked region contains a so called ArUco marker. In that case, the Live Tracker will not just track the xy position of the search region within the image but also try and calculate the angle of the marker. Although theoretically it can determine the rotation of the marker over 3 different axis, currently only the roll-angle of the marker is passed as live link.
</p>
<h3 id="lens-un-distort-node">Lens (Un)distort Node</h3>
<p>The Lens (Un)distort plug-in node can be used to distort or undistort an image based on lens distortion parameters or by using a UV-map. </p>
<p><img alt="" src="../../assets/official-reference/live-fx-user-guide/LFX_NodeLensDistort_v02.png" /></p>
<p>Use the top dropdown to switch between <strong>Distort </strong>and <strong>Undistort</strong>. The various <strong>Distortion parameters</strong> (P1, P2, ..) can be obtained from:</p>
<ul>
    <li>a camera calibration and storing / applying the data from a camera profile, </li>
    <li>from some of the supported live link camera trackers,</li>
    <li>from other software by simply entering the values manually.</li>
</ul>
<p>Use the <strong>Crop</strong> option to scale the image to remove any black borders that are created by the (un)distort. The <strong>Crop </strong>only works with the distortion parameters, not with an external UV or ST map.</p>
<p>The <strong>Save XML</strong> and <strong>Load XML</strong> buttons store or load the distortion parameters to / from an external file on disk.</p>


<p>Alternatively to using the distortion parameters, you can also use a <strong>UV map</strong> or an <strong>ST map</strong>. Use either the <strong>Load </strong>option to select a map image from disk or drag drop an already loaded map shot to the input of the Lens (Un)distort node in the Inputs menu. </p>


<p>If you loaded a Map through the <strong>Load </strong>button, you can clear it by using the <strong>Remove </strong>button.</p>
<h3 id="spout-syphon-gpu-share-and-sender">Spout/Syphon GPU Share &amp; Sender</h3>
<p>Spout (windows) and Syphon (mac) are protocols to share GPU textures (images) between applications. Sharing images directly on the GPU limits latency to its minimum. Do note however that Spout/Syphon do not have any sync mechanism: an application always just takes the 'latest' image shared. An receiver application might already have advanced to a next frame, while the sender application has not - or vice verse. In general, when both application both run in real time (and at the same frame rate) the latency should be a maximum of 1 frame.</p>
<p>There are two versions of the Spout/Syphon plug-in: The <strong>GPU Share</strong> plug-in and the <strong>Sender </strong>plug-in. In the GPU Share plug-in you select one of the available textures from the <strong>Server </strong>dropdown. If the texture of an application is not listed, try using the <strong>Reload </strong>button to refresh the list. Once the texture is loaded, you can size the plug-in node to the texture size by enabling the <strong>Auto-resize</strong> option. Use the <strong>Invert-image</strong> option to flip the image in case the sending application has a different orientation for its textures. In the bottom label the <strong>format / bit depth</strong> of the shared texture is displayed.</p>
<p>Note that Spout/Syphon GPU texture share is also available through the VideoIO framework. The advantage of using it through the VideoIO framework is that you can also record any stream coming in through Spout/Syphon. The plug-in version is sometimes more convenient in an ad-hoc setup as it takes less configuration on forehand.</p>
<p>The Spout/Syphon Sender version of the plug-in is currently not available through VideoIO. You can instantiate the plug-in anywhere in your composition to share the image with another application. After instantiating the plug-in, enter a label for the shared image to be easily recognizable in the other application.</p>
<h3 id="realsense-depth-deprecated">RealSense Depth (deprecated)</h3>
<p>The Intel RealSense depth camera uses Lidar to generate a depth image. The RealSense depth plug-in captures this image and can generate a matte from it, which can be combined with an RGB camera image. </p>
<p>Note that the RealSense depth camera is only available for Windows. Further note this node was implemented as an experiment but that in the end the resolution of the camera, as well as the accuracy of the depth information and in dealing with the reflection of certain surfaces proved to be limited. Nevertheless – the plug-in offers a way to start using new technology in a creative way. The aim of the implementation was to use it as an overlay on the actual camera image and as such to create a dynamic mask based on the depth information which potentially could replace green screen keying. Without newer and better versions of the depth camera, further development was stopped.</p>
<p><img alt="" src="../../assets/official-reference/live-fx-user-guide/LFX_Plugin_Realsense_depth_v01.png" /></p>
<h5 id="mode">Mode</h5>
<ul>
    <li>    Alpha Mask. Use the Threshold distance to generate a matte with everything further away than the threshold being fully opaque.</li>
    <li>    Depth as Alpha. Put all depth information in the alpha channel of the image. Use the input shot of the plug-in for the RGB part.</li>
    <li>    Depth as RGB. Generate RGB image based on the depth information.</li>
</ul>
<h5 id="max-distance">Max Distance</h5>
<p>The max distance is used to better reflect the depth range in the alpha or RGB shades.</p>
<h5 id="threshold-2">Threshold</h5>
<p>Used with the Alpha Mask mode to generate a matte from all that is closer or further away than the threshold distance. Used to mimic a green-screen setup, without the green-screen.</p>
<h5 id="invert-mask">Invert Mask</h5>
<p>Inverts the alpha values / mask related to the distance.</p>
<h5 id="smooth-radius">Smooth Radius</h5>
<p>Smooth the alpha values to get rid of jitter along the edges of objects.</p>
<h5 id="calibrate-3">Calibrate</h5>
<p>Enable this setting to get an RGB representation of the depth info so it is easier to align the depth image with the actual camera image.</p>
<h5 id="scale-and-offset">Scale &amp; Offset</h5>
<p>Scale and offset the depth image to match the actual camera image.</p>
<h3 id="eq-2d-transformer">Eq-&gt;2D Transformer</h3>
<p>The Eq-&gt;2D Transformer node takes in an equirectangular image and outputs a 2D image based on a camera rotation and field of view that you set.</p>
<p><img alt="" src="../../assets/official-reference/live-fx-user-guide/LFX_EQ2D_v01.png" /></p>
<p>The camera rotation and field of view can also be <strong>linked to the shot camera</strong>, which in turn can be linked to a camera tracker. Optionally you can also move the inside the equirectangular sphere by adjusting the <strong>XYZ position</strong>. Note though that since this is primarily used with pre-recorded plates, adjusting in xyz too much might lead to a distorted image. </p>
<p>To also link the XYZ position to the shot camera, enable the <strong>Incl. Position</strong> option. Since inside a sphere the standard radius is 1, you can adjust the Scale to use a more proper range for XYZ adjustments in meters.</p>
<h3 id="usd-nodes">USD Nodes</h3>

<p>(Live FX Studio)</p>

<p>USD (Universal Scene Description) is a format for 3D elements and scenes. The USD node load these elements / scene and uses the Pixar Hydra rendered, that is included with the installation, to render a 2D image based on the camera and object position and a range of render and lighting options. This allows you to include 3D virtual elements into your (live) composition. </p>
<p>Although the USD node has its own camera position controls, you can also link to the active shot camera as to fully integrate it with your composition. When you add an USD node on a layer to your composition, ensure that the layer is set to <strong>Relative</strong>, so that it 'sticks' to the camera: the USD node makes sure that at any one time the correct perspective of the 3D item is rendered to a 2D image.</p>
<p>Note that USD elements / scenes can be loaded directly from file just like any other media format.</p>
<p><img alt="" src="../../assets/official-reference/live-fx-user-guide/LFX_NodeUSD_v01.png" /></p>
<h4 id="general-3">General</h4>
<h5 id="position-rotation">Position / Rotation</h5>
<p>This determines the position and rotation of the scene. As mentioned above, if the USD node is added on a layer in a composition, the layer should be set to Relative. That way the USD node origin aligns with the origin of the 3D layer composition and virtual camera model.&nbsp; </p>
<h5 id="scale">Scale</h5>
<p>Some USD scenes might be specified in a different dimension than in meters. Use the <strong>Scale</strong> to convert it into meters so it aligns with camera tracking. </p>
<h5 id="render-quality">Render Quality</h5>
<p>The higher the quality setting the better the output image but also the higher the potential performance hit for the whole composition. </p>
<h5 id="enable-lights">Enable Lights</h5>
<p>Toggle the lights as defined in the USD on/off.</p>
<h5 id="scene-lights">Scene Lights</h5>
<p>Toggle additional lights (see last tab) on/off. The effect depends on the specific scene.</p>
<h5 id="enable-materials">Enable Materials</h5>
<p>Toggle the use of textures and reflections as defined in the USD on/off. Can be used to affect performance.</p>
<h5 id="equirectangular">Equirectangular</h5>
<p>This option renders the scene 6 times in all directions and generates an equirectangular output from it. The equirectangular output can e.g. be used for projection to multiple LED walls or to render out a scene and use the rendered output directly.</p>
<h5 id="grid">Grid</h5>
<p>Toggle the display of a floor-level grid on/off.</p>
<h4 id="camera">Camera</h4>
<h5 id="position-rotation-2">Position / Rotation</h5>
<p>Position the camera that is used to render the 2D image of the 3D scene.</p>
<h5 id="auto-position">Auto-position</h5>
<p>Option to auto position the camera so that the scene is captured completely in the 2D image.</p>
<h5 id="link-to-shot-camera">Link to Shot camera</h5>
<p>This links the render camera to the shot camera, which in turn is linked to a camera tracker and controls the full composition.</p>
<h5 id="fov-factor">FoV Factor</h5>
<p>Only available when the USD render camera is linked to the shot camera and is a way to extend the camera frustum a bit to create some slack on the physical camera frustum on an LED wall projection to that the edge of the displayed frustum is never captured by the physical camera.</p>
<h5 id="planes">Planes</h5>
<p>This can be used to filter out near or far away objects from the render. By using 2 versions of the same scene and adjusting the front / back planes of each you can potentially create a front and back plate that can be used with a green-screen (middle) plate.</p>
<h4 id="lights">Lights</h4>
<p>The effect of the <strong>Ambient</strong>, <strong>Specular</strong>, <strong>Shininess </strong>color as well as the <strong>Dome Light</strong> toggle depend on the setup of the USD scene. Toggle the <strong>Auto-Position</strong> off to be able to adjust the direction of the light in the scene manually by using the <strong>XYZ</strong> controls.</p>
<h3 id="notch-blocks">NOTCH Blocks</h3>

<p>(Live FX Studio)</p>

<p>Notch Builder (<a href="https://www.notch.one/" class="ApplyClass" target="_blank">https://www.notch.one/</a>) allows you to create 3D elements or completes scenes which can be exported as Notch Blocks. Live FX can load such a Notch Block as part of a (live) composition shot, where the various parameters of the notch block can be set, animated or linked to a live source and as such be combined with a live camera feed.</p>
<p>A Notch Block can be loaded directly from disk or by first selecting a Notch Block plug-in node through the plug-in browser in the player. When loaded through the plug-in browser, you are asked to select a specific Notch Block *.dfxdll file from disk. To be able to render the content of a Notch Block you need the Notch render engine installed as well as a Notch license. Certain Notch Blocks can take some time to load, the first time you open them. Loading a project with the Notch Blocks nodes in it, does not take that much extra time. However, the first time a Notch Block needs to render an image in the player it might take longer.</p>
<p>Each Notch Block has its own set of parameters / controls to. However, all Notch blocks have the same 3 general controls: Height and Width, which determine the size of the output of the Notch Block. Note that by default the size if the same as the size of the Live FX node but can be adjusted to e.g. a smaller size to speed up rendering (while you can then upscale the node to the composition resolution). The third general control with each Notch Block is the Layer selection. A Notch Block can contain one or more different layers of which only one can be selected at any one time. Note however that you could instantiate multiple Notch nodes in a single composition, each with a different layer selected.</p>
<p>Certain Notch Blocks can contain properties that are exposed as Live Links (similar to the output of the Live Tracker). These Live Links can in turn be used to control and steer other aspects of the composition. Check the Live Animation editor for available Notch Block parameters.</p>
<h3 id="notchlc">NotchLC</h3>
<p>Next to rendering Notch Blocks, Live FX also supports playback of (QuickTime) media encoded with the <span class="Highlight">NotchLC codec</span>. The NotchLC codec is used to ensure real-time playback due to its GPU optimized encoding model. There is also a NotchLC encoder available for SCRATCH to transcode any media into this format. Contact support on the known email address for more information </p>


