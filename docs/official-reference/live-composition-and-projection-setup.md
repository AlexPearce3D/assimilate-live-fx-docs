# Live Composition and Projection Setup

## Live Composition Setup <a href="#live-composition-setup" id="live-composition-setup"></a>

Many of the individual compositing elements and function available in Live FX come together in the Live Composite Setup panel. This Wizard type of function is available from the Construct main menu and helps you to setup complex live (green-screen) compositions with just a few clicks.

<br>

Start by selecting type of composition you want from the Model dropdown. The various options are self-explanatory.

Next, set the **Name** for the composition as well as the **Camera-id** and **Scene** designation.

Select the camera that you want to capture from the dropdown that lists all available **VideoIO** inputs. Note that it is possible to select a different capture channel or even add multiple live capture nodes into your composite at a later stage.

In the **Format** options you specify the resolution and framerate of your composite. The framerate should be the same as the live capture. A live composition can be **Continuous** (no ending) or have a specific **Length**. Note that even if you specify a specific duration, playback of the composite is always looped, and any recording will continue until explicitly stopped.

Select the background for your (green screen) live composition. There are different options:

* The background can be an existing clip. Use the Browse option to load it directly from file or drag-drop the clip from the Construct into the proxy area.
* Alternatively, the background can in itself be a live capture coming from another camera or a live capture coming from other software.
* If the background image is an equirectangular image, then make sure it is marked as such if not already by default.
* If you do not require a background at this point but one was selection in a previous session, use the **R**eset button to clear it.

Any green-screen with background composition, involves a key /qualifier. Enable the Light Wrap option to automatically include a Matte Wrap node to create the light wrap effect.

A live composition is likely to use a **Camera Tracker**. The dropdown lists all supported trackers (live links), whether they are already active or not. If a tracker live link is not yet active is be activated automatically. The first available tracker in the selected category is used to live link to the virtual shot camera. If the background clip is an equirectangular clip, then a Eq->2D Transformer node is included in the composition which links to the main shot camera.

For most live compositions to work correct, a calibrated (virtual) camera is needed. Make sure you create a camera profile after a calibration. Selecting an existing **Camera Profile** with the live composition setup will speed things up enormously.

Once you hit **Create**, a composition node is created, which is placed in the first empty slot in the construct and then opened for playback and further setup in the Live FX Tab. As mentioned, all options that have been set in the **Create Live Composition** panel can be modified in the Player.

For some compositions additional steps are required. E.g. when using an Unreal Engine background, you need to make sure Unreal is running the correct project and the project contains the Live Link plug-in so the Live FX can sync the images of unreal with the live camera images that are being captured. Various tutorial videos are available from the Live FX support website that show the possible workflows.

## Live Projection Setup <a href="#live-projection-setup" id="live-projection-setup"></a>

Similar to the Live Composition panel there is also Live Projection Setup panel to help you setup relatively complex projection composition shots with just a few clicks. This function is also available from the Construct main menu bar.



### Steps <a href="#steps" id="steps"></a>

The first step in creating a projection setup is select a stage-configuration from the Stage Manager. If there are not stages available yet, then you can open the Stage Manager to create one. The selected stage-configuration will automatically become, if not already, the active one. Note that you can create a projection setup without the Stage Manager but then you will have to manually enter all LED wall specifications in the projection node.

Next, set the **Name** for the composition as well as the **Camera-id** and **Scene** designation.

The clip that is to be projected on the LED wall can be:

* A pre-recorded plate of any of the supported file formats, any resolution and framerate. Use the Browse option to select a file from disk or drag/drop an already loaded clip in the proxy area.
* A Live captured image from other software such as a game render engine like Unreal or Unity. Select the desired from the VideoIO capture list.
* A 3D scene rendered by a USD of Notch block node. Use the Browse or drag/drop option.
* If the image that is to be projected is an equirectangular image, then make sure it is marked as such if not already by default.

It is recommended to do a camera calibration and store a **Camera Profile** for the camera that is used to record the projection. Select the profile from the dropdown rather than having to enter all data after creating a projection setup, will save a lot of time.

The **Camera Tracker** dropdown lists all supported trackers (live links), whether they are already active or not. If a tracker live link is not yet active is be activated automatically. The first available tracker in the selected category is used to live link to the virtual shot camera.

When enabling the **Frustum Highlight** toggle, the active camera frustum will be displayed in the projection. This is done by slightly dimming the outer frustum. The display of the main image in the inner frustum is not adjusted.

When projecting an 360 image (pre-recorded plate), you have the option to us **Spherical** or **Dome** projection (see for more information the description of the Projection node).

### Capture scene <a href="#capture-scene" id="capture-scene"></a>

To live review the result of the scene, you can capture the image of the physical camera. Select the correct channel from the **Live Capture** dropdown list. This will create an additional channel in the resulting Projection Switcher node. Potentially you can also use this for recording. Note though that you do not want to get in the way of regular playback in case the resources of the system are limited and the media + grades become extensive and complex.

Enable the **Set-extension** option to add a Stage-matte node with the live capture so the projected image is (virtually) extended if the camera frustum does not fully overlap the LED wall. Note that usually a camera capture introduces a few frames delay. That means that the set-extension clip should take this into account. Set the **Frame-delay** so that the correct back plate frame is combined with the correct captured frame. You can adjust this at any point in the player – in the Fill/Matte menu of the Set-extension layer.

### Projection Composition <a href="#projection-composition" id="projection-composition"></a>

Click the Create button to create the projection setup. This composition is placed in the first empty slot on the construct and the nod is opened in the player. The exact layout of the Projection composition depends on your LED wall configuration in the Stage Manager and the if you added a live capture / set-extension.

The Projection composition node will likely contain the following elements:

* Switcher node at the root, with for each LED wall output a channel + optionally a channel for live capture. The Switcher node is tied to the camera tracking.
* Each channel has a Projection node, which in turn has the source clip as input. The projection node uses the Stage Manager and is tied to a specific wall. The Projection node uses the virtual camera settings of the Switcher node.
* In case of frustum highlighting. The Projection node has a layer with a 2D->Wall matte plug-in that dims the outside of the camera frustum.
* In case of a Live capture, an extra input/channel is added to the Switcher node. If no set-extension is used, the capture node is used as the channel input. For a set-extension, the Stage-Matte is used as input, which in turn takes the live capture node and the source clip as input. It uses the Stage Manager and Switcher node camera settings to render its output.

When only dealing with a single LED wall and no live capture then the composition the Switcher node is not included, and the channel projection node becomes the root.

## Composition Assemble <a href="#composition-assemble" id="composition-assemble"></a>

(Live FX Studio)

In the paragraph about the recording options in the Live FX menu in the Player, the option to record the clean sources (rather than the full graded composition) was briefly discussed. In this paragraph the workflow to start with a live composition, create and tweak an offline composition and ultimately create the final online composition is discussed. The workflow is displayed in the diagram below.

With the Record: Source Capture option, the Auto Load Clip and the Write Metadata Sidecar options enabled in the Live FX menu, every recording of a live composition shot is automatically transformed into an offline composition shot, where:

* A full copy of the original (composition) shot is made.
* Any live capture node inside the composition shot is replaced with the recorded source.
* Any live link animation is replaced with data from the side car file and put in an animation curve for the specific parameter.
* The shot is tagged as an offline composite.

An Offline Composition can be worked on as any normal composition: e.g. smooth animations or adjust grades. Once the high resolution camera media has been offloaded from the camera and loaded into your project, you can create the Online Composition. To transform an Offline Composition into an Online Composition (or directly a Live Composition into the Online Composition), you use the Online Composition Assembler which is available from the Online Compositions button in the Construct menu.

The panel lists all Live and Offline composition shots in the current timeline. If a shot is selected int he timeline it is enabled in the list, otherwise it is disabled. This way you can quickly transform just a single node. Click the button in the first column in the list or use the **Select** option below the list to alter the selection. The next step is to point the Assemble function where to look for the Online media: either select a specific group of timeline in the project or use the **Media** drop down to select a specific folder on disk. Then make sure that you point the Assemble function to the correct folder with the sidecar files with (animation) metadata. The function will match the correct files with the correct composition.

After pointing the function to the correct locations for media and metadata, start the matching function and tell it where to put the results by using the Target drop down. The Assemble button will start the actual creation of the Online Composition:

* Copy the Live or Offline composition.
* Replace live capture nodes or offline recordings with the online high resolution camera media.
* In case of a live source, replace the live links with the animation data from the sidecar file.
* Place the new Online Compositions in either a new timeline, as versions in the same slot as the Live / Offline compositions or attached to the pen from where you can drop them anywhere you want.

Note that you can use **Create All Takes** in one go when going directly from a Live Composition to an Online Composition. However, you do need to make sure that the Online media has to correct cam-id and scene-number metadata to match with the Live Compositions as a timecode match will not work.

In the right part of the Composition Assembler you can see the matched Online shots that were found with the Live or Offline Composition. If for some reason you find there is a wrong match then either use the **Remove** button to remove the individual shot or use the **Clear Matches** button to clear all matches with all nodes in the list to start a clean new match round.
