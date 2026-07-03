# Live FX Interface

## General <a href="#general" id="general"></a>

Live FX offers a toolset for virtual production in its broadest sense: live on-set compositing, pre-visualization, and LED wall projection. It includes media- and version management, metadata handling and recording options and as such allows you to both easily prepare live setups in advance as well as create relevant input for post-production. It also integrates image-based lightning (IBL) through DMX allowing you full control over the look and feel of a scene. Here are some examples of supported setups and workflows:

* Basic green-screen setup with 2D or 2.5D (equirectangular) background, using camera tracker to position the background image.
* Green screen with active camera tracking and 3D backgrounds coming from Unreal, Unity, Notch, or internal USD renderer.
* LED wall projection of 2D, 2.5D or 3D media on any LED wall configuration: single wall, multiple walls, curved walls. In a colour-managed context and can graded with the full set of grading controls.
* A pure keyer solution for other applications – using all layering-, masking- and plug-in tools available and send the result as separate RGB and Alpha Video IO channels or NDI.
* Image Based Lighting (IBL) – easy setup of fixture configuration, sampling colour managed image and sending over ArtNet or sACN.
* Record live composites on-set for instant review without the need for offloading cards from the camera(s). Capture all camera tracking and other dynamic metadata in a sidecar file for post-production/VFX usage.
* Animate the virtual camera and use the Unreal or Unity plug-in to directly control the camera in the renderer, capture the rendered output directly from the GPU without delay for your composite, grade and (optionally) record the result.

Live FX exposes live camera tracking, live-links and other dynamic metadata in a way that allow compositors, VFX specialists and DITs to work with it in a familiar creative context rather than in a programming style environment.

Live FX is an application within the Assimilate Product Suite installer and can be combined with other Assimilate product licenses.

This part of the user guide covers the Live FX specific functions and tools. General functions of the Assimilate Product Suite, such as creating a new project, playback-features or grading tools are covered in the generic section / chapters of the product suite user guide. It is recommended to also read that manual or view the various available tutorial videos.

Note that Live FX comes in two flavours: Live FX Studio and Live FX. Certain functions are only available in Live FX studio. In that case the manual will state ‘FX Studio’ only.

## Live FX tabs <a href="#live-fx-tabs" id="live-fx-tabs"></a>

When you open a project in Live FX, you will find 2 tabs at the bottom of the screen that represent the main modules in Live FX.

* **Construct:** manage media and preparation of live compositions.
* **Live FX:** play-back, projection, grading and composition tools.

Left of the tabs is the Toolset dropdown. Depending on your license you will various other toolsets there. To be able to follow this manual, ensure that the Live FX toolset is selected.

### Construct tab <a href="#construct-tab" id="construct-tab"></a>

Most of the functions and workings of the Construct module are described in the generic user guide. On the main toolbar, there are three important options.

* **Import Clips**. Load a single shot or a range of clips at once from disk. The options for this are fully documented in the Product Suite guide.
* **Live Setup**. Quick and easy create a live composite with foreground, background, camera tracker, keyer and more. This function is explained later in this manual, after some basic elements and tools for live compositing have been explained.
* **Projection Setup**. Quick and easy create a composition shot for projection on LED Wall(s), optionally included with a camera capture and Set extension display. This function is explained later in this manual, after some basic elements and tools for projection have been explained.

In the Construct bottom menu, there are several Live FX specific options.

**Switcher node**. When you select one or more clip items in the construct you can wrap them together in a so called Switcher node. A Switcher node can playback multiple nodes to different outputs at the same time. The details of the Switcher node are explained in more detail later in the manual.

**Calibration**. This will start a calibration session for your LED wall to generate a display LUT based to compensate for any color shifts of the recording camera. This function is still a work in progress and not available on all versions yet.

**Online Composition**. This function allows you to easily switch from a live composition with live input, to an offline composition with recorded proxy media to an online composition that uses the high-resolution camera recordings. This function has its own section later in this manual.

**Render**. Live FX does not have an elaborate render pipeline like the some of the other toolsets have, as it is focussed on Live capture and projection, for which is has recording capabilities. Sometimes it might be useful though to render a composition node to a single file. The Render panel allows you to render a single clip or a selection of clips to ProRes, H264 or HECV.

### Live FX - tab <a href="#live-fx-tab" id="live-fx-tab"></a>

If you are familiar with any of the other Assimilate Product Suite applications, you will recognize the generic Player layout in the Live FX tab, including the color grading and composite tools. The Live FX toolset has a series of additional functions as well as changes the behavior of the Player in several aspects.

* Playback is always started automatically and in loop mode.
* No timeline playback, by default only single (live) shot playback. If you require timeline playback, then enable the 'Live FX Timeline' option in the User Preferences panel (use the gear-icon in bottom right corner).
* More prominent display of playback / pause (highlight in yellow) to warn that the image showing is not live.
* When entering the Player with a live composite, the Record options are available.
* When adding a fill/matte on a layer, the playback mode is automatically set to loop (rather than once).

Most of the Live FX specific functions in the Player are in or can be accessed from the Live FX menu.

#### Live FX Menu - Setup <a href="#live-fx-menu-setup" id="live-fx-menu-setup"></a>

**Live Links**

Live Links opens the live links panel to manage Live Link sources that captures and sends out camera tracking and other dynamic metadata, which can be used in your composition setup. Live Links are discussed in more detail later.

**Stage Manager**

Open the Stage Manager panel where you manage the LED wall setup. The Stage Manager is discussed in more detail later.

**Calibration**

Open the Camera Calibration panel. This panel can also be opened from the Camera menu and in discussed in more detail in the section about the (virtual) camera.

**Scene-Take**

Open the Scene-Take panel to adjust the scene / take metadata for the current shot. The scene / take metadata is included with any recording you make.

**DMX**

The DMX button opens the DMX Light Control panel for on-set image based light control (IBL). These functions are discussed later in this guide.

**Performance Monitor**

Toggle the Performance Monitor displayed centre-top in the View Port on/off to check the playback performance and real time abilities of the system. The Performance display is explained in more detail in the generic part of the manual.

**Quick Paths**

The Quick Paths drop down is a quick way to add specific functions to your composite. A quick path automatically adds layers, plug-ins, and live link animations to create the desired function. A Quick Path can be undone with a single undo.

**Active Components**

This section shows you how many Video IO streams are currently active and being used in the current composite, how many Video IO outputs are active, and the number of Live Links are active in the system. This can give you an indication how resources are being used on the system and give possible suggestions what to adjust if playback is no longer real-time. Every input and output stream requires system resources - even if an input stream is not used in the current composite shot that is playing.

**Auto Sync**

This is a shortcut to toggle the auto-sync option with each input channel on/off rather than having to navigate to each live capture node and toggle the setting on/off one by one. The Auto-Sync option with input channels allows you to automatically synchronize incoming frames from different feeds based on the associated timecode. See for a more elaborate description of this mechanism in the section about capture nodes.

Note that if the current composite contains (multiple) capture nodes with the Auto Sync option enabled while at the same time there are active input feeds with the option enabled but that are not used in the composite - a warning exclamation character is shown. Since all feeds will sync with each other even if not used - the not-used feed might influence the timing of the active shot. It is then better to toggle the Auto Sync option off and back on again. When switching the Auto Sync on from this menu - only the channels that are being used in the active composite shot are in fact enabled.

**Shot Length**

In most cases the length of a live composite is of less interest as it will playback in a loop and as such always provides a continuous live image. If you however combine the live composite with pre-recorded media or add fixed time animations then the length of the composite – and as such the repeat time – is of importance. When enabling the Continuous option, the mini-timeline for scrubbing the play position is no longer visible. You can only set the continuous mode for live capture nodes. For media nodes, you can adjust the in- and out-point of the clip.

**Timecode Provider**

Certain composition shots might not have a timecode of their own. E.g. when the composition starts with an empty color frame and the live camera capture is added as a layer on top of that. You can assign a timecode provider to such a shot. Note that this only applies to live composite shots (containing a live element), not to regular media clips. These you can just assign a timecode if needed.

As timecode provider you can either select the system time or you can select one of the available VideoIO input device/channels. Note that if needed, you can select a different channel that is being used in the composition shot.

#### Live FX Menu - Record options <a href="#live-fx-menu-record-options" id="live-fx-menu-record-options"></a>

When a live capture node / shot is active in the player, the main toolbar will show a record button. In the record tab inside the Live FX menu you can set the recording options: the Output folder and file naming mask as well as the format and whether to record alpha- and certain audio channels.

Live FX allows to record in one of three formats: ProRes, H264 or DNx. Depending on the selected format additional options become available like ProRes sub-codec, H264 quality or DNx bit rate control.

ProRes 4444 and 4444 XQ also allow to record the created alpha channel of the composite along with the video.

At the bottom of the menu you can enable one or more audio channels to record. In Live FX you can capture the audio with the video input or select a separate audio input through the **Audio Panel** (Capture tab), which is available from the top menu. Optionally you can delay the audio to sync with the captured video.

In addition to the recording format and audio there are several options on what should be recorded.

Full Shot versus Source Capture. The first option records a single clip with all the sources and grades baked in. The second option records each live capture node in the composition in a separate output, without any grade applied. These source shots are used to create an offline version of the live composition when loaded back into the project. In a later stage you can use these offline compositions to create the online composition with the actual camera raw media. The workflow to create offline and online composites is discussed later in this guide.

Write Dynamic Metadata to a sidecar file. All dynamic metadata and live link data, whether actively used in the composite or not, is written to a comma separated (.csv) sidecar file. The file has the same name as the recorded media file and contains the per frame timecodes so you can link any metadata to a specific recorded frame (see below on how to use the metadata from the sidecar file).

Auto Load the recorded clip. This option loads the recorded clip as version shot into the same slot as the composite shot when the recording is ended. As such, the clip is immediately available for review from the version stack in the player.

Auto Increment the Scene-Take number of the current (live) shot after recording ends.

**Metadata Sidecar**

The metadata sidecar file that can be created with a recording contains comma separated value (csv) data. You can load and use this data for your online composite with the camera raw media through the Animation editor.

If you e.g. want to use the metadata for the virtual camera of a shot, then first enable manual animation in the camera menu and then open the Animation menu. Select the channels you want to animate and then use the Import button to open the csv file. The software will automatically recognize the sidecar file and open the channel mapping dialog to link the metadata to a specific animation channel.

The Sync drop down tells the software from where to apply the animation data:

* Start at the first frame (in-point) of the shot.
* Use the current play-position as the start.
* Start the animation by syncing the shot timecode and the timecode column in the csv. This requires that the csv has a timecode column and that you selected that column from the second drop down.

Next, select with each animation channel the csv column you want to load, using the drop down in the second column. Use the options in the Start and End column to determine the shape of the animation curve at the start and end frame. The last option determines if the each of the animation point is interpreted as part of a curve or connected linearly.

## Player Controls <a href="#player-controls" id="player-controls"></a>

When a live capture node or a composition node that contains a live capture node is active in the player, then the main menu bar will contain Record controls and the Cue Up control.

#### Auto / Rec <a href="#auto-rec" id="auto-rec"></a>

The Auto option is only available in Live FX and when the software is able to recognize and read the record state of a camera from the SDI signal. When the Auto option is enabled, recording will automatically start when the camera starts recording. Alternatively, when the Auto option is off or disabled you can click the Rec button at any time to start / stop recording.

Note that you can also use the Remote-Control function keys to start/stop recording. The Remote Control is available from the Tools drop down menu in the top toolbar in the Player.

#### Cue Up <a href="#cue-up" id="cue-up"></a>

Clicking the Cue Up button will ensure that any fill shots (e.g. used as a background in a green-screen context) and/or frame animations are reset to their start position.
