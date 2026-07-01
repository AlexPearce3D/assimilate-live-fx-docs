# System Settings

You can find the System Settings when you first open Assimilate, on the bottom left of the screen.

<figure><img src="../../../../assets/image (296).png" alt="" width="293"><figcaption></figcaption></figure>

## General

From the Startup screen, you can open the System Settings dialog that contains various system-wide configuration information of Live FX. The settings on the first **General tab** are discussed in this paragraph. The content of all other tabs is discussed in detail in various places throughout this guide.

### Language

As of version v8.4 the Live FX User Interface is also available in Chinese. At first time startup Live FX determines what language to use by default from the Operating system settings.

### System Folders

Live FX stores all Project databases and User Profiles, and created templates and presets in separate folders. You can change this configuration to suit your particular setup. E.g. you can point to the location of these folders to a network-shared directory to share projects and user profiles with multiple Live FX systems. Note though to share projects the network protocol used should enforce proper file locking otherwise two systems might end up adjusting the same project database, resulting in database corruption and loss of data. Also, Live FX does not lock the files in the Users folder when a User Profile is selected. Strict procedures for all users to only select a single User Profile from one system at any one time is recommended.

### **Project Directory**

The location where Live FX stores all projects - one sub-folder per project. Use the **Set** button to open a Live FX Browser and navigate to the desired folder.

### **User Directory**

The location where Live FX stores all User Profiles - one sub-folder per profile.

### **Shared Directory**

Location where you can store various templates and presets to be shared between all User Profiles on a single system, or amongst multiple Live FX systems when located on a network drive.

### **Global Watch Director**

The Global Watch Directory works in conjunction with the Live FX XML-script capabilities.

While Live FX is running, it is constantly monitoring – or watching – this folder for new files. If a new file with an .xml extension is copied into this folder, Live FX opens the file and attempts to process the XML commands that are contained within.

To warrant consistency in processing if multiplied files are inserted in the Watch Folder - files are processed in order of their modified date. The use of XML-script in Live FX is covered in more detail in Chapter 10 and Appendix B.

The **Clear** button can be used to remove the Watch folder completely.

### **Start up Logo**

Here you can select an image file with e.g. your company logo to replace the Live FX Logo on the Start screen. Use the **Clear** button to remove a previously selected image and revert to the normal Live FX logo.

**MATCHBOX PLUG-INS**

Matchbox plug-ins are so-called (shader)script-based image effects plug-ins, of which there are quite a few available for free: [https://logik-matchbook.org/](https://logik-matchbook.org/). Using the **Install** button you install the freely available plug-ins.

Alternatively, you can use the **Set** button to point Live FX to a folder where you already installed Matchbox plug-ins.

#### MISC SYSTEM SETTINGS

**AUTO-LOGON**

With Auto-Logon enabled, the initial Start-up Screen is bypassed and Live FX enters automatically the last Project that was used in your previous Live FX session.

Tip: To enable the Start-up Screen again, exit a Project and switch to the System Settings Menu; deactivate Auto-Logon. The next time you start Live FX you will be presented with the Start-up Screen.

**CHECK FOR UPDATES**

This option connects to the ASSIMILATE server at startup and checks for news updates, which are displayed on the login screen.

#### SDI AND DUAL HEAD SETTINGS

**ENABLE AND CONFIGURE**

Live FX will automatically detect and can use a second monitor or SDI output. This second output will not have the user interface overlaid on it and can be used as a clean feed for projection, client monitoring, or output to a tape deck.

Live FX currently automatically detects and supports the following SDI boards: AJA (KONA 3G or LHi, Kona 4), Bluefish cards, DeckLink, and NVIDIA SDI Option cards.

When one of these cards is detected you can enable SDI with the corresponding **Enable** button and the **Configure** button becomes available which in turn opens the SDI settings dialog window. The SDI configuration panel is discussed in more detail later in this paragraph.

Note: Some of the supported SDI cards require Live FX to restart after an Enable or Disable. On Windows Live FX will restart automatically, on OS X you need to manually restart the application.

**DUAL HEAD**

Enable or disable the second monitor if available. This option is on by default if Live FX detects a second monitor. However, if SDI is enabled this option is no longer available.

#### CONFIGURE SDI

This dialog panel lets you configure a number of your SDI Settings.

![SDI Configure](http://www.assimilatesupport.com/akb/Uploads/Images/Manual/Startup/System_settings/LO_SDI_V05.png)

**SIGNAL FORMAT**

Select the resolution and framerate of the signal. Note that this will override any signal selected in the SDI card control panel.

**DATA FORMAT**

This is either RGB or YUV in various SDI-specific layouts.

* Note that any 444 format requires a dual link.
* For 444 the AJA implementation only supports RGB formats.
* When selecting RGB 444 with an AJA card the SDI signal is always full-range and no colorspace matrix can be applied.

**COLOR SPACE MATRIX**

* Live FX always produces RGB values which need to be converted to SDI
* The conversion will be performed to either CCIR, REC709 or RGB
* **Scaled** means Live FX will scale its RGB values to fit into the _Legal_ SDI range
* **Full** means Live FX will not scale the levels but transfer them 1:1 to the SDI colorspace

The additional **H** (Headroom) option enables or disables the availability of super black/white on the SDI output signal. Note that **Scaled** already is in a legal range and can not produce super black/white levels.

**SYNC AND FRAME LOCK**

For NVIDIA cards only - you can either select to use the internal sync of the card or to work with an external sync device. The frame lock can be used to sync across multiple monitors. Please see the NVIDIA documentation for more details on these functions.

**SHOW FRAMES DROP**

Enabling this option will show an error message in the player each time a frame is dropped on the SDI signal.

**APPLY SETTINGS**

When using an NVIDIA SDI card Live FX will automatically restart after **Applying** new settings to re-initialize the SDI card. This is not required for the other supported cards.

Note: when using an NVIDIA card a warning may be displayed at the bottom of the panel indicating that the selected signal and any external sync do not correspond. This is an internal NVIDIA driver message.

Note: With the“NO CS matrix” option set, Live FX will not explicitly set the colorspace at start up. In that case, the color space that has been set through the SDI card settings panel will be used. However, after selecting “NO CS matrix”, you should first exit Live FX and (re)set the custom color space through the SDI card settings panel.

Note: The SDI Output only shows images from the Player. When you are in the Construct, or the Start-up screen, the SDI Output shows a Live FX logo screen or a custom logo if the Start-up screen has been customized. See Chapter 10 for details about customizing the Start-up screen.

Tip: The\[DUAL YUV 422] option is used for stereoscopic output. The two outputs of the SDI card will be configured to show the left and right sides of the Live FX DUAL VIEW. Details on configuring Live FX for stereoscopic projects are covered in a separate support article.





## General

<figure><img src="../../../../assets/image (306).png" alt=""><figcaption></figcaption></figure>

## Panel Setup

<figure><img src="../../../../assets/image (305).png" alt=""><figcaption></figcaption></figure>

## Formats

<figure><img src="../../../../assets/image (307).png" alt=""><figcaption></figcaption></figure>

## Aspects

<figure><img src="../../../../assets/image (308).png" alt=""><figcaption></figcaption></figure>

## Metadata

<figure><img src="../../../../assets/image (309).png" alt=""><figcaption></figcaption></figure>

## Notes

<figure><img src="../../../../assets/image (310).png" alt=""><figcaption></figcaption></figure>

## Custom Commands

<figure><img src="../../../../assets/image (311).png" alt=""><figcaption></figcaption></figure>

## Advanced

<figure><img src="../../../../assets/image (312).png" alt=""><figcaption></figcaption></figure>

