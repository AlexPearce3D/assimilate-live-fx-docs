# Live Composition and Projection Setup

<h2 id="live-composition-setup">Live Composition Setup</h2>
<div>
<p>Many of the individual compositing elements and function available in Live FX come together in the Live Composite Setup panel. This Wizard type of function is available from the Construct main menu and helps you to setup complex live (green-screen) compositions with just a few clicks.</p>
</div>
<img alt="" src="../../assets/official-reference/live-fx-user-guide/LFX_LiveCompSetup_v01.png" /><br />
<div>
<p>Start by selecting type of composition you want from the Model dropdown. The various options are self-explanatory. </p>
<p>Next, set the <strong>Name</strong> for the composition as well as the <strong>Camera-id</strong> and <strong>Scene </strong>designation. </p>
<p>Select the camera that you want to capture from the dropdown that lists all available <strong>VideoIO </strong>inputs. Note that it is possible to select a different capture channel or even add multiple live capture nodes into your composite at a later stage. </p>
<p>In the <strong>Format </strong>options you specify the resolution and framerate of your composite. The framerate should be the same as the live capture. A live composition can be <strong>Continuous</strong> (no ending) or have a specific <strong>Length</strong>. Note that even if you specify a specific duration, playback of the composite is always looped, and any recording will continue until explicitly stopped.</p>
</div>
<div>
<p>Select the background for your (green screen) live composition. There are different options:</p>
<ul>
    <li>The background can be an existing clip. Use the Browse option to load it directly from file or drag-drop the clip from the Construct into the proxy area. </li>
    <li>Alternatively, the background can in itself be a live capture coming from another camera or a live capture coming from other software.</li>
    <li>If the background image is an equirectangular image, then make sure it is marked as such if not already by default.</li>
    <li>If you do not require a background at this point but one was selection in a previous session, use the <strong>R</strong>eset button to clear it.</li>
</ul>
<p>Any green-screen with background composition, involves a key /qualifier. Enable the Light Wrap option to automatically include a Matte Wrap node to create the light wrap effect.</p>
<p>A live composition is likely to use a <strong>Camera Tracker</strong>. The dropdown lists all supported trackers (live links), whether they are already active or not. If a tracker live link is not yet active is be activated automatically. The first available tracker in the selected category is used to live link to the virtual shot camera. If the background clip is an equirectangular clip, then a Eq-&gt;2D Transformer node is included in the composition which links to the main shot camera.</p>
<p>For most live compositions to work correct, a calibrated (virtual) camera is needed. Make sure you create a camera profile after a calibration. Selecting an existing <strong>Camera Profile</strong> with the live composition setup will speed things up enormously.</p>
<p>Once you hit <strong>Create</strong>, a composition node is created, which is placed in the first empty slot in the construct and then opened for playback and further setup in the Live FX Tab. As mentioned, all options that have been set in the <strong>Create Live Composition</strong> panel can be modified in the Player. </p>
<p>For some compositions additional steps are required. E.g. when using an Unreal Engine background, you need to make sure Unreal is running the correct project and the project contains the Live Link plug-in so the Live FX can sync the images of unreal with the live camera images that are being captured. Various tutorial videos are available from the Live FX support website that show the possible workflows.</p>
</div>
</div>
<div>
<p></p>
</div>
<div>
<p></p>
</div>
<div>
<p></p>
</div>
<div>
<h2 id="live-projection-setup">Live Projection Setup</h2>
<div>
<p>Similar to the Live Composition panel there is also Live Projection Setup panel to help you setup relatively complex projection composition shots with just a few clicks. This function is also available from the Construct main menu bar.</p>
</div>
<div><img alt="" src="../../assets/official-reference/live-fx-user-guide/LFX_LiveProjectionSetup_v01.png" /></div>
<h3 id="steps">Steps</h3>
<div>
<p>The first step in creating a projection setup is select a stage-configuration from the Stage Manager. If there are not stages available yet, then you can open the Stage Manager to create one. The selected stage-configuration will automatically become, if not already, the active one. Note that you can create a projection setup without the Stage Manager but then you will have to manually enter all LED wall specifications in the projection node.</p>
</div>
<div>
<p>Next, set the <strong>Name </strong>for the composition as well as the <strong>Camera-id</strong> and <strong>Scene </strong>designation. </p>
</div>
<div>
<p>The clip that is to be projected on the LED wall can be:</p>
</div>
<ul>
    <li>A pre-recorded plate of any of the supported file formats, any resolution and framerate. Use the Browse option to select a file from disk or drag/drop an already loaded clip in the proxy area.</li>
    <li>A Live captured image from other software such as a game render engine like Unreal or Unity. Select the desired from the VideoIO capture list. </li>
    <li>A 3D scene rendered by a USD of Notch block node. Use the Browse or drag/drop option.</li>
    <li>If the image that is to be projected is an equirectangular image, then make sure it is marked as such if not already by default.</li>
</ul>
<div>
<p>It is recommended to do a camera calibration and store a <strong>Camera Profile</strong> for the camera that is used to record the projection. Select the profile from the dropdown rather than having to enter all data after creating a projection setup, will save a lot of time.</p>
<p>The <strong>Camera Tracker</strong> dropdown lists all supported trackers (live links), whether they are already active or not. If a tracker live link is not yet active is be activated automatically. The first available tracker in the selected category is used to live link to the virtual shot camera. </p>
<p>
</p>
</div>
<div>
<p>
</p>
<p>
</p>
</div>
<div>
<p>
</p>
<p>
</p>
</div>
<div>
<p>When enabling the <strong>Frustum Highlight</strong> toggle, the active camera frustum will be displayed in the projection. This is done by slightly dimming the outer frustum. The display of the main image in the inner frustum is not adjusted.</p>
<p>When projecting an 360 image (pre-recorded plate), you have the option to us <strong>Spherical</strong> or <strong>Dome </strong>projection (see for more information the description of the Projection node).</p>
<p>
</p>
<h3 id="capture-scene">Capture scene</h3>
<p>
To live review the result of the scene, you can capture the image of the physical camera. Select the correct channel from the <strong>Live Capture</strong> dropdown list. This will create an additional channel in the resulting Projection Switcher node. Potentially you can also use this for recording. Note though that you do not want to get in the way of regular playback in case the resources of the system are limited and the media + grades become extensive and complex.</p>
<p></p>
<p>Enable the <strong>Set-extension</strong> option to add a Stage-matte node with the live capture so the projected image is (virtually) extended if the camera frustum does not fully overlap the LED wall. Note that usually a camera capture introduces a few frames delay. That means that the set-extension clip should take this into account. Set the <strong>Frame-delay</strong> so that the correct back plate frame is combined with the correct captured frame. You can adjust this at any point in the player – in the Fill/Matte menu of the Set-extension layer.
</p>
<h3 id="projection-composition">Projection Composition</h3>
<p>
Click the Create button to create the projection setup. This composition is placed in the first empty slot on the construct and the nod is opened in the player. The exact layout of the Projection composition depends on your LED wall configuration in the Stage Manager and the if you added a live capture / set-extension. </p>
<p></p>
<p><img alt="" src="../../assets/official-reference/live-fx-user-guide/LFX_ProjectionCompTree_v01.png" /></p>
<p>The Projection composition node will likely contain the following elements:</p>
<ul>
    <li>Switcher node at the root, with for each LED wall output a channel + optionally a channel for live capture. The Switcher node is tied to the camera tracking.</li>
    <li>Each channel has a Projection node, which in turn has the source clip as input. The projection node uses the Stage Manager and is tied to a specific wall. The Projection node uses the virtual camera settings of the Switcher node.</li>
    <li>In case of frustum highlighting. The Projection node has a layer with a 2D-&gt;Wall matte plug-in that dims the outside of the camera frustum.</li>
    <li>In case of a Live capture, an extra input/channel is added to the Switcher node. If no set-extension is used, the capture node is used as the channel input. For a set-extension, the Stage-Matte is used as input, which in turn takes the live capture node and the source clip as input. It uses the Stage Manager and Switcher node camera settings to render its output.</li>
</ul>
<p></p>
<p>When only dealing with a single LED wall and no live capture then the composition the Switcher node is not included, and the channel projection node becomes the root.</p>
</div>
<div>
<h2 id="composition-assemble">Composition Assemble</h2>
<p>(Live FX Studio)</p>
<p>In the paragraph about the recording options in the Live FX menu in the Player, the option to record the clean sources (rather than the full graded composition) was briefly discussed. In this paragraph the workflow to start with a live composition, create and tweak an offline composition and ultimately create the final online composition is discussed. The workflow is displayed in the diagram below.</p>
<p><img alt="" src="../../assets/official-reference/live-fx-user-guide/LFX_Assemble_Diagram_v01.png" /></p>
<p>With the <span class="Highlight">Record: Source Capture </span>option,  the <span class="Highlight">Auto Load Clip</span> and the <span class="Highlight">Write Metadata Sidecar</span> options enabled in the Live FX menu, every recording of a live composition shot is automatically transformed into an offline composition shot, where:</p>
<ul>
    <li>A full copy of the original (composition) shot is made.</li>
    <li>    Any live capture node inside the composition shot is replaced with the recorded source.</li>
    <li>    Any live link animation is replaced with data from the side car file and put in an animation curve for the specific parameter.</li>
    <li>    The shot is tagged as an offline composite.</li>
</ul>
<p>An Offline Composition can be worked on as any normal composition: e.g. smooth animations or adjust grades. Once the high resolution camera media has been offloaded from the camera and loaded into your project, you can create the Online Composition. To transform an Offline Composition into an Online Composition (or directly a Live Composition into the Online Composition), you use the Online Composition Assembler which is available from the Online Compositions button in the Construct menu.</p>
<p><img alt="" src="../../assets/official-reference/live-fx-user-guide/LFX_Assemble_Panel_v01.png" /></p>
<p>The panel lists all Live and Offline composition shots in the current timeline. If a shot is selected int he timeline it is enabled in the list, otherwise it is disabled. This way you can quickly transform just a single node. Click the button in the first column in the list or use the <strong>Select </strong>option below the list to alter the selection. The next step is to point the Assemble function where to look for the Online media: either select a specific group of timeline in the project or use the <strong>Media </strong>drop down to select a specific folder on disk. Then make sure that you point the Assemble function to the correct folder with the sidecar files with (animation) metadata. The function will match the correct files with the correct composition.</p>
<p>After pointing the function to the correct locations for media and metadata, start the matching function and tell it where to put the results by using the Target drop down. The Assemble button will start the actual creation of the Online Composition:</p>
<ul>
    <li>Copy the Live or Offline composition.</li>
    <li>    Replace live capture nodes or offline recordings with the online high resolution camera media.</li>
    <li>    In case of a live source, replace the live links with the animation data from the sidecar file.</li>
    <li>    Place the new Online Compositions in either a new timeline, as versions in the same slot as the Live / Offline compositions or attached to the pen from where you can drop them anywhere you want.</li>
</ul>
<p>Note that you can use <strong>Create All Takes</strong> in one go when going directly from a Live Composition to an Online Composition. However, you do need to make sure that the Online media has to correct cam-id and scene-number metadata to match with the Live Compositions as a timecode match will not work.</p>
<p>In the right part of the Composition Assembler you can see the matched Online shots  that were found with the Live or Offline Composition. If for some reason you find there is a wrong match then either use the <strong>Remove </strong>button to remove the individual shot or use the <strong>Clear Matches</strong> button to clear all matches with all nodes in the list to start a clean new match round.</p>
</div>
</div>
<div>
<p></p>
</div>
<div>
<p></p>
</div>
<div>
<p></p>
</div>
<div>
