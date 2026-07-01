# LED Wall Projection and Stage Manager

<h2 id="led-wall-projection">LED Wall Projection</h2>

<p>(Live FX Studio)</p>

<h3 id="overview">Overview</h3>
<p>Using an LED wall as background for recording a scene takes more than just playing back media on the wall. The media should be projected correctly where the projection considers both the position and size/resolution of the wall as well as the position/rotation of the camera that is recording the stage. If the projection does not take these aspects into account, the background in the recorded image might look distorted and wrongly scaled. </p>
<p>Live FX can be used to easily and correctly project media on LED wall(s). Live FX uses several elements for this which are displayed in the schematic below. The schematic gives an overview and briefly explained in this paragraph to introduce you to the various concepts involved. Each element has been or will be described in detail in this manual and separately as some elements also have their function in other contexts than projection. After discussing the elements in detail, setting up an actual projection is discussed. By then, it is easy to understand what is happening under the hood and how to manage the projection.</p>
<p><img alt="" src="../../assets/official-reference/live-fx-user-guide/LFX_ProjectionDiagram_v01.png" /></p>
<ul>
    <li>The Stage Manager is where you manage the configuration of the LED wall(s): shape, size, resolution, and position of a wall. This creates a model of your stage.</li>
    <li>In the Stage Manager you also map the LED wall (models) to physical output displays (dual head and/or VideoIO).</li>
    <li>A Projection node comes in two flavors: 2D-&gt;Wall and Eq-&gt;Wall. Depending on the type of media you use one or the other.</li>
    <li>A Projection node takes in:
    <ul>
        <li>Media: this can be a 2D or 2.5D pre-recorded clip, a live capture from e.g., Unreal Engine, a 3D Notch block, or a 2D render from a 3D USD scene. </li>
        <li>The configuration of one of the walls from the active stage in the Stage Manager</li>
        <li>Camera tracking data of the physical camera, coming in through a live link tracker that is tied to the virtual camera of the node.</li>
    </ul>
    </li>
    <li>The projection node adapts to the resolution of the selected wall and generates the correct image based on the shape of the wall and the position of the camera.</li>
    <li>One or more Projection nodes (in case of multiple walls) feed into a single Switcher node. A Switcher node can playback multiple streams at the same time to specific displays.</li>
    <li>The Switcher node takes in the mapping information of the Stage Manager to generate a mosaic image and/or to output each wall projection to the correct display.</li>
</ul>


<h2 id="stage-manager-2">Stage Manager</h2>

<p>(Live FX Studio)</p>


<p>At the heart of LED wall projection in Live FX is the stage manager. The Stage Manager is where you create a model of your stage with the position and shape of the LED wall(s). This information is used, together with the camera position, to determine the correct image to be send to each wall. In the Stage Manager you also determine how display outputs are mapped on each of the LED walls. The Stage Manager can be opened from the Projection Setup panel in the Construct (see below) or from the Live FX menu in the Player.</p>
<p><img alt="" src="../../assets/official-reference/live-fx-user-guide/LFX_StageManager_v01.png" /></p>
<p>The left side of the panel contains all controls to manage multiple stages and walls. The right side of the panel show the stage model. Through the Mapper tab in the right side of the panel you link the physical display outputs to the LED walls.</p>
<h3 id="stage-management">Stage Management</h3>
<p>You can maintain multiple stage configurations. Use the <strong>Add</strong> button to create a new configuration or use the <strong>Duplicate </strong>option to make a copy of the selected configuration to create a variation. The <strong>Delete </strong>option will permanently remove the configuration, there is no undo option for it. </p>
<p>The configurations are stored in the <span class="Highlight">stageconfigs.xml</span> file in the Assimilate settings folder. The configurations are available in all projects. Optionally, you can copy this file to other systems, however, keep in mind that the configurations have references to <span class="Highlight">wall-mesh (.obj) files</span>, which also need to be copied and be available in the same relative path on the other system.</p>
<p>Although you can maintain multiple stage configurations, there is only one active at any one time. The title bar of the Stage Manager panel states which stage is active. Select the <strong>Active</strong> button to make the current stage active. The button will light up green.</p>
<h3 id="wall-specifications">Wall Specifications</h3>
<p>Each stage contains one or more LED wall definitions / models. To input the shape and size of a LED Wall, you use an <span class="Highlight">.obj file</span>. You can create and save 3D models in an .obj file in a variety of other software and use the Load option in the Stage Manager to load it in. Alternatively, use the <strong>Create </strong>button to open the Led Wall Model Creator panel.</p>
<p><img alt="" src="../../assets/official-reference/live-fx-user-guide/LFX_WallCreator_v01.png" /></p>
<p>In this panel you can define the size and shape of a panel, save an .obj file to the selected output folder and add it to the stage configuration directly.</p>
<p>The specifications of the LED wall are defined by entering the number of LED tiles used and the size and resolution of an individual tile. Optionally you can set a curvature for the wall in degrees. Note that if you enter the curvature, the label at the bottom will show the ‘<span class="Highlight">depth</span>’ of the wall, which is the distance from sides of the wall to the centre-back. Use this if the curvature in degrees is not known and you are able to measure the distance. </p>
<p>There are three types of walls you can create: a standard vertical wall or a floor- or roof wall. The floor and roof walls are rotated and respond to the curvature setting by removing whole tiles from their back side to generate a saw-tooth shape.</p>
<p>When you press <strong>Ok </strong>the new wall is added to the stage.</p>
<p>The <strong>Delete </strong>button removes the wall from the stage but does not delete the underlying .obj file. Note that this action does not have an undo.</p>
<p>Changing the position of a wall in the list of LED wall can sometimes come at hand because the order will also be used when creating a projection setup (see below).</p>
<p>The <strong>Scale </strong>option can be used with .obj files that have been specified in another dimension than meters.</p>
<p>The <strong>position </strong>of the wall is the offset from the origin of the stage which is usually the origin of your (camera) tracking system. Both the position and rotation are relative to the origin of the wall model, which is usually in the centre bottom/back, but this might be different for externally created models.</p>
<p>The wall <strong>resolution </strong>is specified as the total number of pixels over the full width and height of the wall (not per tile as in the Model Creator discussed above). This resolution is used for linking a wall to a physical output. </p>
<p>Finally, the wall <strong>tile count</strong> is only used for generating a preview image to verify the wall mapping (see below). In case of a curved floor/roof wall, this is the count without any curvature.</p>
<h3 id="stage-model">Stage Model</h3>
<p>In the <strong>Model tab</strong> of the Stage Manager the stage model is displayed. Click and drag with the mouse to rotate the model. Ctrl + click and drag to zoom in / out of the model.</p>
<p>The origin or the stage is represented by the colored cube/arrows:  Z-axis in blue, X-axis in red, Y-axis in green. The origin of the stage usually corresponds to the origin of your (camera) tracking system.</p>
<p>When you open the Stage Manager in the player and there is a shot with an active camera, the camera and the camera frustum is shown in the model. This shows you what part of the LED wall(s) the camera is capturing at any point.</p>
<h3 id="mapper">Mapper</h3>
<p>Usually, the resolution of LED walls differ from the display output(s) of your system (dual head or VideoIO outputs). In the <strong>Mapper tab</strong> you configure how a LED wall relates to a physical display output. You want to <span class="HighlightNote">prevent as much as possible that any scaling</span> is required for the display output or being done by the LED wall processor unit.&nbsp; </p>
<p>The Mapper has the flexibility to tie walls to displays in different configurations: </p>
<ul>
    <li>Output a single wall over one or multiple VideoIO output(s)</li>
    <li>Output multiple walls through an Nvidia mosaic of displays</li>
    <li>A combination of the above</li>
</ul>
<p>The <strong>Display</strong> dropdown shows all available VideoIO outputs and the Dual Head if that has been enabled on the system. The combination of selected display and selected wall in the walls-list determines the combination that you are mapping.</p>
<p>The <strong>Map </strong>button links/unlinks the display and wall. When linked, you can set the <strong>XY Offset</strong> and <strong>Scale</strong>. </p>
<p>When you enable the <strong>Mosaic</strong> option with a display, you indicate that multiple walls can be mapped to the display. If the <strong>Mosaic </strong>is not enabled, then you can only map one wall to the selected display. Enabling the <strong>Map </strong>option will then automatically unlink any other wall that was previously mapped to the display.</p>
<p>The <strong>Mosaic </strong>option primarily meant for usage with the NVIDIA Mosaic functionality. There you create one big virtual display from multiple physical displays/outputs on your graphics card. This single big virtual display is then used as Dual Head for the system. Next, you map multiple LED walls onto that one display. Not all walls have to have the same resolution, hence the mosaic. This way the output to multiple walls can be send out as one image to the Dual Head.</p>
<p>Note that when you are not using the Mosaic option, then the offset and scale values are applied as regular offset and scale with that display as they are available in the Player-Settings-Monitor menu. You can adjust those settings also independently from the Stage Manager. But when doing so, the mapping for the stage configuration might become incorrect. </p>
<h5 id="dual-head-vs-videoio">Dual Head vs VideoIO</h5>
<p>In general, Dual Head output has less latency than VideoIO output. If the clip to project has little action or the scene does not involve camera motion then this might not matter. If it does, then Dual Head might be the preferred way. A combination of Dual Head and VideoIO outputs is possible. The latency difference will in general only be a few frames. If the LED walls are not joined or not captured by the camera at the same time, this should not be a problem. </p>
<h5 id="preview">Preview</h5>
<p>The <strong>Preview </strong>option in the Mapper tab, creates a Switcher node with underlying a node that generates a test pattern: a rectangle for each LED wall tile with the row/col number. The preview meant to make sure all pixels are included in the (mosaic) output and not left out because an offset was just too high/low. </p>
<p><img alt="" src="../../assets/official-reference/live-fx-user-guide/LFX_WallPreview_v01.png" /></p>
<p>When the Preview is invoked from the Construct, the test pattern is automatically opened in the player. When already in the player, the test pattern replaces the active node. Clicking the <strong>Reset </strong>button takes back to the Construct or prior node.</p>
<h3 id="mapper-examples">Mapper Examples</h3>


<p>To make the concept of mapping Walls and Displays in the Stage Manager more clear and concrete, here are two example mappings. The first very basic, the second using the Mosaic option.</p>


<h4 id="stage-a">Stage A </h4>
<ul>
    <li>Single square wall – 6 x 6 tiles, each with 200x200 resolution. So total resolution of 1200 x 1200). </li>
    <li>Output over 4k Video IO SDI to (also 4k) LED wall processor. </li>
</ul>
<p>First ensure that you have the VideoIO output setup correctly through the VideoIO settings panel that you can open either from the start screen or from the Player – Settings menu panel.<br />
Next:</p>
<ul>
    <li>In the Stage Manager define a new stage and load or create a new wall according to the specs.</li>
    <li>In the Mapper tab, select the VideoIO channel from the Display dropdown and select the Map option to tie the two together.</li>
    <li>Since the resolution of the wall is smaller than the actual output resolution, you might have to offset the image to ensure the image is covering the wall. This depends on how / if the LED wall processor places the incoming image on the wall. An easy way to determine the correct offset is to use the Preview option. This will send out a test pattern of 6x6 tiles which should exactly cover the wall.</li>
    <li>The test pattern is shown through a Switcher node. On the Display tab of the Channel Controller of the Switcher node, ensure that the VideoIO channel is tied to the first channel of the Switcher node. Normally this is done automatically when using activating the Preview option.</li>
</ul>
<h4 id="stage-b">Stage B</h4>
<ul>
    <li>Main wall with resolution of 4928 x 1936, driven by 2 x LED wall processors with 4k input (3840 x 2160). Square side wall of 1056 x 1056 pixels, driven by a LED wall processor with an HD input (1920 x 1080). </li>
    <li>HDMI output directly from the graphics card.</li>
</ul>
<p>To control 3 LED wall processors from the graphics card (next to the main UI display), we first need to create one virtual display which we can use as second output / dual head in Live FX - using the NVIDIA Mosaic functions (<a href="https://www.nvidia.com/en-us/design-visualization/solutions/nvidia-mosaic-technology/" target="_blank" class="ApplyClass">Mosaic Technology for Multiple Displays | NVIDIA</a>). </p>
<p>Rather than creating a virtual display with 3 physical outputs, we can also create a mosaic that requires only 2 physical outputs and then we duplicate the first output to be send to two LED wall processors. This saves on resources as splitting an HDMI output does not take any overhead. So, the setup that we are after looks like the image below.</p>
<p><img alt="" src="../../assets/official-reference/live-fx-user-guide/LFX_Mapping_Example_v01.png" /></p>
<p>The resolution of this virtual display is 3840 + 3840 = 7680 width and 2160 in height (two 4k displays next to each other). The image of the small wall is added to the first display, which is then duplicated and send to 2 processors. Note that the default settings of the LED wall processor might have to be adjusted to show the correct part on of the image on the wall. <br />
Once you have created the NVIDIA mosaic display, start Live FX and enable the Dual Head option in the System Settings panel which can be opened from the start-up screen.</p>
<p>Next:</p>
<ul>
    <li>In the Stage Manager, load or create both walls and make sure the resolution is entered correct. </li>
    <li>In the Mapper tab, select the Dual Head display and enable the Mosaic option with this display. Then after selecting each wall, enable the Map option so that both walls are mapped on the Dual Head.</li>
    <li>Now we need to offset the walls to cover the correct portion of the virtual display. You can use the Preview option for this of do the math.</li>
    <li>By default all walls are mapped to the centre. The Main wall also needs to be centred vertically and the Side wall needs to be offset to the left top part of the virtual display. Doing the math with the origin (0, 0) in the center of the display we get:
    <ul>
        <li>Main wall X offset = 0</li>
        <li>Main wall Y offset = 112 (vertical centre)</li>
        <li>Side wall X offset = -3312 (to top left)</li>
        <li>Side wall Y offset = 552</li>
    </ul>
    </li>
</ul>
<p>Note that the Preview option can also help to offsets the mappings accurately.</p>


