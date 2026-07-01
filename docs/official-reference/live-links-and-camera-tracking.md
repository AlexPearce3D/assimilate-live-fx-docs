# Live Links and Camera Tracking

<h2 id="live-links-2">Live Links</h2>
<p>Live Links are at the heart of compositing in Live FX. They are a source of dynamic metadata that can be used as parameters for composite elements. Live link metadata can also be stored alongside the recording so that it can be used for creating animations in a post-production context.</p>
<p>There are 3 types of Live Links:</p>
<ul>
    <li>Global sources. Global live links are tied to an external to the software source. This can be a specific camera tracking system or a data coming from other software through the Open sound Control (OSC) protocol. These types of Live Links need to be explicitly activated but are then available in any composite node and at any level.  Global Live Links are managed from the Live Links panel that is opened from the Live FX menu or the Tools dropdown in the top menu bar.</li>
    <li>Outgoing. Some Live Links send out metadata for other applications to use. E.g. The Unreal Engine (UE) Live Link sends out the current (virtual) camera metadata over the network to an Live FX Unreal plug-in that controls the camera inside the UE scene it is used in. That way you can generate (and potentially capture) as if it was made with the Live FX virtual camera.</li>
    <li>Sources linked to a specific node. Examples are metadata produced by a Live Tracker plug-in node that is placed on a (live capture) clip to track a specific element, or the Focal Length dynamic metadata that comes with a live SDI capture of a camera. In these cases, the live link data is only available in the composite, at every (sub) node that is on the same level or downstream from the live link source.</li>
</ul>
<h3 id="live-links-manager">Live Links Manager</h3>
<p><img alt="" src="../../assets/official-reference/live-fx-user-guide/LFX_LiveLinks_v03.png" /></p>
<p>The left of the Live Links panel lists all available live links and their state: active / inactive. To activate or to deactivate a Live Link, select it in the list and click the <strong>On/Off</strong> button with the Live Link.</p>
<p>All incoming Live Link data is tied to a timecode. Normally that is the timecode of the current (composition) shot that is playing. But just like you could set an alternative <strong>Timecode Provider</strong> for a composition shot (see earlier in the manual), you can also set an alternative timecode source for live link data. In some case you might use a shot that uses more than one live capture, but you need camera tracking data be tied to a specific capture. Note that this is a global setting. If you set a timecode provider then this is also used by default with any next composition that you open. Of course, you can change the setting at any time.</p>
<h3 id="live-links-camera-trackers">Live Links – Camera Trackers</h3>
<p>Live FX comes with a range of supported camera tracker that you can use. All trackers are presented and controlled in a similar way and have a number of common functions. </p>
<h4 id="tracker-common">Tracker Common </h4>
<h5 id="apply">Apply</h5>
<p>When a tracker live link is selected, the Apply button at the top of the Live Link panel is available. The Apply function ties the current selected tracker to the virtual camera of the current shot. Depending on the capabilities of the tracker, the translation and rotation parameters are linked to the animation controls of the virtual camera in the Camera menu. This is a shortcut for automatically linking the virtual camera to camera. See for more information about (manually) linking shot parameters to live link data later in this manual.</p>
<h5 id="delay">Delay</h5>
<p>The camera tracker data and image data usually travel different paths. The tracker data is usually sent over an Ip network, while the camera live image comes in through SDI. This also means that that the data travels at different speeds. If you combine the data again in a live composition you need to compensate for this. Since the tracker data is in general faster than the image data, there is a delay setting with each tracker. This delay is specified in milliseconds and represents the timeframe between the arrival of the tracker data and the arrival / capture of the corresponding camera image though a VideoIO channel.</p>
<p>There is no automated way to determine the delay. This is done by trial and error. A possible way is to add a virtual ground layer through the camera calibrate panel. This layer sticks to the scene origin while the physical and virtual camera moves. When the delay value is incorrect the layer will appear to move before or after the camera image moves. Adjust the value up / down till the layer sticks to the camera image. Note that the value might have to be adjusted from one session to the next as the image capture cadence might slightly vary.</p>
<h5 id="smooth">Smooth</h5>
<p>The Smooth option applies a filter to the tracker data to get rid of any jitter. Note that the stronger the filter, any movement changes might come over as somewhat delayed. This is inherent to filtering real time data.</p>
<h5 id="threshold">Threshold</h5>
<p>This is another way of filtering out potential noise in the tracker data: changes in the tracker data smaller than the threshold are ignored. Note that setting the threshold too high can make an actual camera move appear as a little jump.</p>
<h5 id="mount-offset">Mount Offset</h5>
<p>A rotation of the camera might also result in a slight xyz offset of the camera tracker mounted on top of a camera. A tracker might also have been mounted on a slight angle on the camera. To compensate for this, you can enter mounts offsets. From the perspective of the camera operator (behind the camera): the Z offset represents the distance the tracker is mounted behind (positive) the focal point, the y offset how far the tracker is mounted above (positive) the focal point and the x offset how far to the right (positive) of the focal point. All in millimetres. Note that some trackers already include the mount offset and all values can be left to 0. Also note that the calibration functions that are discussed later, can possibly be used to determine the mount offset values. </p>
<h5 id="reset">Reset</h5>
<p>This resets the tracker camera position matrix that has been set through the camera position calibration. In that calibration step the absolute position of the camera from the scene origin is determined by scanning an Aruco marker at that scene origin. From that scan a camera pose is calculated to adjust the tracker data. This button resets this camera pose matrix and will show the tracker raw values.</p>
<h5 id="overlay">Overlay</h5>
<p>Enable this option to get a display of the current selected tracker and the motion path.</p>
<h4 id="trackers">Tracker Specific</h4>
<p>The various supported camera tracker systems also each have their own specifics regarding:  </p>
<ul>
    <li>All trackers give rotation data but not all trackers provide (XYZ) translation data.</li>
    <li>Not all trackers provide lens data such as focal length and zoom (which can be live linked to the virtual camera of a shot).</li>
    <li>Some trackers provide lens distortion (dist) data, which can be live linked to the Lens (un)distort plug-in to undistort the camera image in real-time. If the tracker does not provide this data then you can consider determining the distortion yourself by using the camera calibration tools, discussed later in this manual.</li>
    <li>Some trackers require you to do an origin calibration to set the scene origin (see more about this in section about (virtual) camera calibration), whereas other trackers do this in the source system.</li>
    <li>Some trackers do not already include the mount-offset from the camera nodal point. If they do not, you need to enter these yourself. You can use the nodal point calibration for this, which is discussed later in this manual. The mount offset covers both the xyz distance offset between tracker point and the camera nodal point as well as the xyz rotational offset that might exist.</li>
    <li>Some tracker are automatically detect on the network whereas other you need to specify them (IP/Port) to connect.</li>
    <li>Some trackers are only available with a Live FX Studio license.</li>
</ul>
<div>
<table style="width: 75%;" class="BorderTable">
    <thead>
    </thead>
    <tbody>
        <tr>
            <td style="width: 30%;">
            <p><strong>Tracker</strong></p>
            </td>
            <td style="width: 10%;" align="center">
            <p><strong>XYZ </strong></p>
            </td>
            <td style="width: 10%;" align="center">
            <p><strong>Lens</strong></p>
            </td>
            <td style="width: 10%;" align="center">
            <p><strong>Dist</strong></p>
            </td>
            <td style="width: 10%;" align="center">
            <p><strong>Origin</strong></p>
            </td>
            <td style="width: 10%;" align="center">
            <p><strong>Mount</strong></p>
            </td>
            <td style="width: 10%;" align="center">
            <p><strong>Auto </strong></p>
            </td>
            <td style="width: 10%;" align="center">
            <p>&nbsp;<strong>Lic</strong></p>
            </td>
        </tr>
        <tr>
            <td>
            <p>Antilatency<br />
            <a href="http://" target="_blank" class="ApplyClass">https://antilatency.com</a></p>
            </td>
            <td align="center">
            <p>Y </p>
            </td>
            <td align="center">
            <p>N </p>
            </td>
            <td align="center">
            <p>N </p>
            </td>
            <td align="center">
            <p>N </p>
            </td>
            <td align="center">
            <p>N </p>
            </td>
            <td align="center">
            <p>Y </p>
            </td>
            <td align="center">
            <p> S</p>
            </td>
        </tr>
        <tr>
            <td>
            <p>FreeD</p>
            </td>
            <td align="center">
            <p>y/n </p>
            </td>
            <td align="center">
            <p>y/n </p>
            </td>
            <td align="center">
            <p>N </p>
            </td>
            <td align="center">
            <p>y/n </p>
            </td>
            <td align="center">
            <p>y/n </p>
            </td>
            <td align="center">
            <p>Y </p>
            </td>
            <td align="center">&nbsp;</td>
        </tr>
        <tr>
            <td>
            <p>Mo-Sys<br />
            <a href="http://" target="_blank">https://www.mo-sys.com</a></p>
            </td>
            <td align="center">
            <p>Y </p>
            </td>
            <td align="center">
            <p>Y </p>
            </td>
            <td align="center">
            <p>Y </p>
            </td>
            <td align="center">
            <p>Y </p>
            </td>
            <td align="center">
            <p>Y </p>
            </td>
            <td align="center">
            <p>Y </p>
            </td>
            <td align="center">
            <p>&nbsp;S</p>
            </td>
        </tr>
        <tr>
            <td>
            <p>NCam<br />
            <a href="http://">https://www.ncam-tech.com</a></p>
            </td>
            <td align="center">
            <p>&nbsp;Y</p>
            </td>
            <td align="center">
            <p>Y </p>
            </td>
            <td align="center">
            <p>Y </p>
            </td>
            <td align="center">
            <p>Y </p>
            </td>
            <td align="center">
            <p>Y </p>
            </td>
            <td align="center">
            <p>Y </p>
            </td>
            <td align="center">
            <p>&nbsp;S</p>
            </td>
        </tr>
        <tr>
            <td>
            <p>OSC Apps - Oschook (Android)	 </p>
            </td>
            <td align="center">
            <p>N</p>
            </td>
            <td align="center">
            <p>N </p>
            </td>
            <td align="center">
            <p>N </p>
            </td>
            <td align="center">
            <p>N </p>
            </td>
            <td align="center">
            <p>N </p>
            </td>
            <td align="center">
            <p>N </p>
            </td>
            <td align="center">&nbsp;</td>
        </tr>
        <tr>
            <td>
            <p>OSC Apps - GyrOsc (iOS)</p>
            </td>
            <td align="center">
            <p>&nbsp;N</p>
            </td>
            <td align="center">
            <p>N </p>
            </td>
            <td align="center">
            <p>N </p>
            </td>
            <td align="center">
            <p>N </p>
            </td>
            <td align="center">
            <p>N </p>
            </td>
            <td align="center">
            <p>N </p>
            </td>
            <td align="center">&nbsp;</td>
        </tr>
        <tr>
            <td>
            <p>OSC Apps - Sigsim Pro (iOS)</p>
            </td>
            <td align="center">
            <p>&nbsp;Y</p>
            </td>
            <td align="center">
            <p>N </p>
            </td>
            <td align="center">
            <p>N </p>
            </td>
            <td align="center">
            <p>N </p>
            </td>
            <td align="center">
            <p>N </p>
            </td>
            <td align="center">
            <p>N </p>
            </td>
            <td align="center">&nbsp;</td>
        </tr>
        <tr>
            <td>
            <p>OpenVR</p>
            </td>
            <td align="center">
            <p>&nbsp;Y</p>
            </td>
            <td align="center">
            <p>N </p>
            </td>
            <td align="center">
            <p>N </p>
            </td>
            <td align="center">
            <p>N </p>
            </td>
            <td align="center">
            <p>N </p>
            </td>
            <td align="center">
            <p>Y </p>
            </td>
            <td align="center">&nbsp;</td>
        </tr>
        <tr>
            <td>
            <p>Realsense (Intel) (discontinued)</p>
            </td>
            <td align="center">
            <p>&nbsp;Y</p>
            </td>
            <td align="center">
            <p>N </p>
            </td>
            <td align="center">
            <p>N </p>
            </td>
            <td align="center">
            <p>N </p>
            </td>
            <td align="center">
            <p>N </p>
            </td>
            <td align="center">
            <p>Y </p>
            </td>
            <td align="center">&nbsp;</td>
        </tr>
        <tr>
            <td>
            <p>ZED<br />
            <a href="http://" target="_blank">https://www.stereolabs.com</a></p>
            </td>
            <td align="center">
            <p>Y </p>
            </td>
            <td align="center">
            <p>N </p>
            </td>
            <td align="center">
            <p>N </p>
            </td>
            <td align="center">
            <p>N </p>
            </td>
            <td align="center">
            <p>N </p>
            </td>
            <td align="center">
            <p>Y </p>
            </td>
            <td align="center">&nbsp;</td>
        </tr>
    </tbody>
</table>
<br />
</div>
<h5 id="antilatency">Antilatency</h5>
<p>Select one of the available placements – which determines the sensor layout that is being used. Please, see the Antilatency documentation for information on creating a placement.</p>
<h5 id="freed">FreeD</h5>
<p>FreeD is a generic protocol for tracker data exchange. There are different tracker systems available that use this protocol. Although the FreeD protocol includes Zoom and Focus parameters, not all these trackers might also actually include this. Also, the values that are included might not follow a standard. You need to select the appropriate Encoder option with a tracker to get correct data. Possibly the encoder is not yet available in Live FX.</p>
<h5 id="mo-sys-ncam">Mo-Sys, NCam</h5>
<p>Both these trackers have the option to Use Encoder zoom. By default this is off, which means that the focal length live link that is available from the tracker is based on the effective Field of View that the tracker uses internally and passes. This FoV is recalculated into a Focal Length based on the generic/default (virtual) camera sensor size and aspect. When you link this tracker data to the focal length parameter of a virtual camera of a shot, then you should leave the sensor settings of that virtual camera to Generic. </p>
<p>If you enable the Use Encoder option, then the tracker focal length is the data that is passed from the (mechanical) encoder on the physical camera.</p>
<p>Note that to add an NCam tracker, you need to provide the Ip and port number of that system.</p>
<p>Note that the Mo-Sys tracker always sends 1 track frame per video frame. As such, Live FX never interpolates between tracker frames when using tracker data for a specific frame.</p>
<h5 id="osc-app-trackers">OSC App trackers</h5>
<p>The various mobile phone tracker systems each have their own way it can be mounted on a camera: flat / portrait / landscape. You need to set the mount type for each tracker to work correctly.</p>
<h5 id="openvr">OpenVR</h5>
<p>The OpenVR tracker uses the HTC Vive headset and hardware trackers. Please note though that HTC also has the HTC Vive-Mars tracker system. That specific tracker system is supported through the FreeD protocol.</p>
<h4 id="live-links-unreal">Live Links – Unreal</h4>
<p>The Unreal Live Link forms a bridge from Live FX to the Epic Unreal render engine. The UE Live Link sends the (virtual) camera positional and lens data as well as scene/take and record state metadata of the current shot that is playing to an Unreal Plug-in. This plug-in is in its turn a Live Link inside Unreal and can control a virtual camera inside an Unreal scene. So, in case when using a camera tracker system, this is a way of forwarding the tracker data to Unreal. Next, the rendered image can e.g. be used to project on an LED wall or captured for a green-screen setup.</p>
<p>To connect with an Unreal system, enter the Port number to communicate over and either enter the specific IP address of the Unreal system or enable the Broadcast option. The latter will broadcast the data over the network and makes it available to any system in the network to pick it up. When Unreal is running on the same system as Live FX, you can also use ‘local’ as IP address. Click Connect to start sending data.</p>
<p>Use the Offset controls to add an offset to the translation and rotation that is passed to Unreal. This can be useful to quickly select a different part of the Unreal scene without having to adjust anything in the Unreal scene itself. The Scale options can be used in case the Unreal dimensions are not in meters (by default they are in centimeters) or to get a slightly wider field of view than the specified to create some slack when e.g. projecting a camera frustum.</p>
<h5 id="unreal-plug-in">Unreal Plug-in</h5>
<p>To use the Live FX Unreal plug-in in your UE project, first download the plug-in for the version of Unreal Engine that you are using:</p>
<ul>
    <li>    Live FX for Unreal Engine 4.26 - Plugin v07</li>
    <li>    Live FX for Unreal Engine 4.27 - Plugin v07</li>
    <li>    Live FX for Unreal Engine 5.0 - Plugin v07</li>
    <li>    Live FX for Unreal Engine 5.1 - Plugin v11</li>
    <li>Live FX for Unreal Engine 5.2 - Plugin v12</li>
</ul>
<p>Next, follow these steps to use the plug-in</p>
<ul>
    <li>Unzip the LiveLink folder that is in the downloaded zip file and place it in the  “..\yourUnRealProject\Plugins” folder.</li>
    <li>(re)Start Unreal, activate the new plug-in and add a new Live Link Source. Make sure the Unreal Live Link has the same Port number set as the live link inside Live FX.</li>
    <li>Tie the Live Link to the camera in the UE scene. If you have the Unreal Take recorder active, the scene metadata can automatically be synced with Live FX.</li>
</ul>
<div><img alt="" src="../../assets/official-reference/live-fx-user-guide/LFX_UnrealPlugin_v02.png" /><br />
</div>
<p>There are many different use models for Live FX with Unreal Engine. The Unreal Live Link can forward live camera tracking data or forward an animated camera position. Live FX can capture the image output from Unreal to composite this into a live camera feed. </p>
<p></p>
<p>Live FX can capture the Unreal output through SDI or NDI. In general this will cause some latency issues as the Unreal signal takes more time than the live camera image. For that the live capture node in Live FX has a delay option. By delaying the live camera capture you can sync it perfectly with the Unreal output.</p>
<p>Alternatively, Live FX provides a so called Spout plug-in, which allows for direct image sharing between UE and Live FX on the GPU. This only works if both applications run on the same machine but since the image is shared directly on the graphics card, there is no latency. The Spout plug-in is discussed in more detail later.</p>
<p></p>
<h4 id="live-links-other">Live Links – Other</h4>
<h5 id="osc-sender">OSC Sender</h5>
<p>The OSC Sender Live Link can send metadata to other systems using the OSC protocol. Enter the IP Address and (UDP) port number of the system to send the data to. Optionally add a custom tag for the OSC message. Click Connect to start the sending of live link data.</p>
<p>Select which type of data to send by toggling the category buttons on or off.</p>
<ul>
    <li>Camera – Send the Virtual Camera XYZ, Pan/Tilt/Roll and Field of View. Note that the Virtual Camera might be linked to an external Live Link (tracker). In that case this option forwards all the data of that tracker.</li>
    <li>Player – Send the current play-head position (timecode) and player state (play/pause/record).</li>
    <li>Metadata – Send scene/take data of the current shot.</li>
    <li>Animation – Use this to send generic animation data. This option sends the xyz-translation, xy-scale and xyz-rotation data of the Canvas of the first layer in the stack. Use an empty layer to just send out data that you do not want to influence the local composite but do require on another system.</li>
</ul>
<p>Note that on the far right of this Live Link, the OSC message formatting is displayed. Use this to properly interpret the data on the receiving third party system.</p>
<p>Also note that the data send out over OSC can be wrapped in individual packets per value or (by default) as a single bundle. For certain receiving applications this can be important. In the Advanced System Settings, you can switch off the Use OSC Bundles option if needed.</p>
<h5 id="osc-source">OSC Source</h5>
<p>The OSC Source Live Link captures all OSC data that is send to the system over the ports specified. You can enter 3 different ports to receive data from multiple sources. The list next to the ports shows all the tags that are coming in. From that list you can select items to create actual Live Links which values can be used in your composite. Select an item from the left list and use the &gt; button to add it to the right Live Link list. Use the &lt; button to remove the Live Link item.</p>
<h5 id="wave-generator">Wave Generator</h5>
<p>The Wave Generator Live Link allows you to generate a repeating signal that can be used for various purposes in a composite, such as using the signal to position a layer or to dynamically alter a grading parameter.  With each signal (except for the Random signal) you can set the wave length in frames. The available wave forms are:</p>
<ul>
    <li>Sine wave – values between -1.0 and 1.0.</li>
    <li>Square wave – values alternating between 0.0 and 1.0.</li>
    <li>Triangle wave – values between -1.0 and 1.0.</li>
    <li>Saw tooth wave – values between -1.0 and 1.0.</li>
    <li>Random – values between 0.0 and 1.0.</li>
</ul>
<h2 id="live-animation">Live Animation</h2>
<p>Live Link metadata can be used in the grade and composite elements of shot through the Live Animation module. Live Animations are an extension to the standard animation module in the Assimilate Product Suite. In the standard animation module, you can create and apply an animation curve to a grade / composite parameter. Through the Live Animation extension, you link a Live Link to a grade / composite parameter and optionally apply a transform to the metadata to fit the parameter range. Before you can link a parameter to a Live Link you first switch on the Live-option for an animation channel.</p>
<p><img alt="" src="../../assets/official-reference/live-fx-user-guide/LFX_Anim_Live_v01.png" /></p>
<p></p>
<p>The <strong>Live</strong> option applies to all parameters in the animation channel. When the Live option is enabled, the Link option becomes available which opens the Animation Editor for the animation channels shown in the current menu.</p>
<p>The <strong>Link</strong> button opens the Animation Editor for the current selected animation channel, where you manage live links.</p>
<h3 id="live-animation-editor">Live Animation Editor</h3>
<p>The Live Animation Editor behaves similar to the standard Animation Editor, where in the tree view on the left side you select the channels, you want to edit / link.</p>
<p><img alt="" src="../../assets/official-reference/live-fx-user-guide/LFX_Anim_Editor_v02.png" /></p>
<p>In the right panel of the editor, you link the selected animation channel to a live source by selecting a Live Link from the corresponding <strong>Live Sources</strong> dropdown.</p>
<p>Optionally you can set the live link to use a <strong>Delay</strong> with retrieving the value. This is similar to setting a delay with a camera tracker, which was discussed earlier. Only in this case you would delay the data for a specific parameter, rather than delaying the entire tracker data stream. This can be useful e.g. in a case where you need to project an image onto a LED wall based on the more recent camera position but at the same time render a set-extension image from a camera input - which is delayed - and need the same tracker data but of a few frames earlier.</p>
<p>The delay with the Live Link is set in a number of frames, not in milliseconds. Also note that when you set a delay for a channel, that delay is also set for all other selected channels. That way you do not have enter the delay multiple times.</p>
<p>After selecting a live source, you determine how to interpret the live link values.</p>
<ul>
    <li><strong>Absolute</strong>. Use the Live Link value one-on-one as parameter value.</li>
    <li><strong>Invert</strong>. Multiply the Live Link value with -1 to invert the sign of the value.</li>
    <li><strong>Offset</strong>. Add or subtract (negative offset) an amount to the Live Link value and apply the result to the channel parameter.</li>
    <li><strong>Invert + Offset</strong> (combine the two above)</li>
    <li><strong>Factor</strong>. Scale the Live Link value by multiplying it with a number.</li>
    <li><strong>Normalize</strong>. Scale the Live Link value to a value between 0.0 and 1.0. Enter the minimum and maximum values that the Live Link can produce.</li>
    <li><strong>Range</strong>. Scale the Live Link value to a predefined range. Enter the minimum and maximum values that the Live Link can produce as well as the minimum and maximum range the scaling should produce.</li>
</ul>
