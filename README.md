# Cura-Dremel-3D20-Plugin
Dremel Ideabuilder 3D20 plugin for [Cura version 3.2](https://ultimaker.com/en/products/ultimaker-cura-software) or greater. This plugin enables the user to export the proprietary .g3drem files using Cura.  This code is **heavily** based upon the [cura gcode writer plugin](https://github.com/Ultimaker/Cura/tree/master/plugins/GCodeWriter).  Although the software functions reasonably well for the author, the author will not guarantee that the software won't break your 3D printer, set it on fire, or do other **really_bad_things**.  The software is supplied without warranty and the user is responsible if they use this software and bad things happen either to their person, their 3d printer, or any of their other property as a result of using this software, or the files that it creates.  Please remain near the 3D printer while using files generated by this software, and pay close attention to the 3D printer to verify that the machine is functioning properly. The software is provided as-is and any usage of this software or its output files is strictly at the user's own risk.

![The Cura GUI](/docs/GUI.PNG)

This software consists of one plugins for Cura.  The Dremel3D20 plugin contains the necessary printer files to add the Dremel IdeaBuilder 3D20 to Cura and enables cura to export the proprietary g3drem file format that the Dremel 3D20 needs.

**Note:**  This version of the Cura-Dremel-3D20-Plugin will not work with Cura versions 3.1 or earlier due to changes that Ultimaker implemented in the Cura architecture.  For a version that works with Cura versions 3.0 or 3.1, please check out version 0.2.5 of the plugin [here](https://github.com/timmehtimmeh/Cura-Dremel-3D20-Plugin/releases/tag/0.2.5)

---
# Installation

**Note** As of release 0.4.0 the Dremel3D20 plugin now combines the functionality of the DremelGCodeWriter plugin as well as including the ability to automatically install the Dremel printer files.  If you had previously installed the DremelGCodeWriter plugin, please delete it from the following folders before proceeding:
- Windows:  $USER/AppData/Roaming/cura/$CURA_VERSION/plugins
        and
            %CURA_INSTALL_DIR%/plugins (i.e. C:\Program Files\Ultimaker Cura\plugins)

- Mac:      $User/Library/Application\ Support/Cura/$CURA_VERSION/plugins
        and
            Applications/Ultimaker Cura.app/Contents/Resources/plugins
- Linux:    $USER/.local/share/cura/$CURA_VERSION/plugins/

To install the plugins, follow the instructions below:

0.  [Download and install Cura](https://ultimaker.com/en/products/ultimaker-cura-software) on your machine.  This plugin has been tested on Windows 10 Professional 64 bit edition, and MacOS 10.12 (Sierra), but this plugin should work equally well on linux or any other operating system that Cura supports.

1.  Download the plugin files by peforming one of the two actions:

    EITHER
    1. Navigate to the ["Releases"](https://github.com/timmehtimmeh/Cura-Dremel-3D20-Plugin/releases/latest) page to download the latest released version in zip format (named Cura-Dremel-3D20-Plugin-<version>.zip) and extract the zip file to your computer

    OR

    2.  clone the repository onto your machine using the following command
    ```
    git clone https://github.com/timmehtimmeh/Cura-Dremel-3D20-Plugin.git
    ```

2.  Navigate to the folder where you downloaded or extracted the plugin

3.  Install the Dremel Printer Plugin by following the steps below

    1. Open Cura and navigate to the Plugins menu and select "Installed Plugins"

    ![Installed Plugins](/docs/installed_plugins.png)

    2. Click the Install new plugin button on the screen that pops up:

    ![Install new plugin](/docs/install_new_plugin.png)

    3. Navigate to the folder where you extracted the release, (if you cloned the git repository, this is under Cura-Dremel-3D20-Plugin/plugins) and select the Dremel3D20.curaplugin

    ![Install new plugin](/docs/curaplugins.png)

    4. A message window will appear telling you to restart Cura.

    ![Install new plugin](/docs/restart.png)

    5.  Close the Cura application

    6.  (Optional) Copy the dremel_3D20_platform.stl to the `%CURA_INSTALL_DIR%/resources/meshes` folder (if you cloned the git repo this file is under Cura-Dremel-3D20-Plugin/resources/meshes/).  This file contains the 3D model of the Dremel Ideabuilder print bed.  On MacOS copy this file to the folder located at `Ultimaker Cura.app/Contents/Resources/resources/meshes/`  The easiest way on the mac to get to this folder is to right click on the Ultimaker Cura.app application and select the "show package contents" option.  Skip this step on Linux

    ![Copy the contents of Dremel print bed file to the meshes directory of cura](/docs/meshesdir.png)

    7.  Upon restart you should have an option to add a Dremel3D20 printer (see Usage section below) - the plugin is now installed!  

    **Note:** If any errors occurred the Dremel printer files can be re-installed by going to the Extensions menu->Dremel3D20 Printer Plugin->Install Dremel3D20 printer

    ![Install Printer Files](/docs/install_printer_files.png)

**Note:**  If the Dremel3D20 plugin detects an older installation in the main Cura application directory, it will pop up warnings telling the user to remove the old files before it installs the new files.  Once the files have been removed the plugin will automatically install new files to the appropriate locations.

![Warn about old installs](/docs/old_install_warning.png)


---
# Uninstallation
To uninstall the Dremel printer files, open the Extensions menu->Dremel3D20 Printer Plugin and select "Uninstall Dremel3D20 printer".  

To delete the plugin itself navigate to the directory listed below and delete the Dremel3D20 folder.
  - Windows:  $USER/AppData/Roaming/cura/$CURA_VERSION/plugins
  - Linux:  $USER/.local/share/cura/$CURA_VERSION/plugins/
  - Mac:  $User/Library/Application\ Support/Cura/$CURA_VERSION/plugins

**Note:**  These directories are subject to change at Ultimaker's discretion.  The latest information on these directories can be found on [this page](https://github.com/Ultimaker/Cura/wiki/Cura-Preferences-and-Settings-Locations)  

---
# Usage
Once the plugin has been installed you can use it by following the steps outlined below:
1. open Cura
2. Select the Dremel 3D20 as your printer (cura->preferences->printers->add)
![Select the Dremel 3D20](/docs/addprinter.png)

3. Select Dremel PLA filament (even if you're using a different brand) as your filament type - this enables the print quality settings for the Dremel3D20.
![Select the Dremel pla](/docs/selectpla.png)

4. Set the slicing options that you want.

5. <a name="Step5"></a>(Optional, but recommended if using the screenshot feature outlined in the [Preview Image Options](#Preview_Image_Options) section below) Zoom in on the part until it fills the screen.  As the plugin saves out the .g3drem file it will grab a screenshot of the main cura window for use as the preview image that is displayed on the Ideabuilder screen. The area inside the red box shown in the image below will be used in the screenshot (the red box will not appear in the actual cura window when you use the plugin).  **Please Note:** The preview on the Dremel will be **much** better if you zoom in on the part that you're printing until the part fills the screenshot area.

For instance:
![Zoom in on the part](/docs/Zoom_For_Screenshot.PNG)

Will show this on the IdeaBuilder 3D20:
![Ideabuilder Screen](docs/Ideabuilder_screen.jpg)

**Nifty Feature:** The screenshot will work with the visualizer plugins, so feel free to try the "xray view" or "layer view" options if you like those visualizations better.

6. Click "File->Save As", or "save to file", selecting .g3drem as the output file format.

![Save as .g3drem file](/docs/saveas.PNG)

7. Save this file to a SD card
8. Insert the SD card into your IdeaBuilder 3D20
9. Turn on the printer
10. Select the appropriate file to print.  
    **New - [Version 0.3 and above](https://github.com/timmehtimmeh/Cura-Dremel-3D20-Plugin/releases/latest):** The plugin now can implements the logic outlined in the [Preview Image Options](#Preview_Image_Options) section below to select a preview image on the Dremel screen.
11. Click print
12. Enjoy - if you have any feature suggestions or encounter issues, feel free to raise them in the ["Issues" section](https://github.com/timmehtimmeh/Cura-Dremel-3D20-Plugin/issues).
---
# <a name="Preview_Image_Options"></a>Preview Image Options
The plugin has implemented the following logic for selecting a preview image that will show up on the Dremel screen:

1. The plugin allows you to optionally select an image file for use as the preview on the Ideabuilder 3D20 screen.  To enable this feature, go to the Extensions menu, and select Dremel3D20 Printer Plugin->Toggle Screenshot Selection

![toggle screenshot](/docs/toggle_screenshot.png)

Cura will then pop up a message stating that screenshot selection is enabled
![screenshot enabled](/docs/screenshot_enabled.png)

Then once you select a location to save the .g3drem file out a secondary file selection menu will come up allowing you to select a screenshot.  If you select one then it will be used, if you press cancel, then the plugin will proceed to Step 3

To disable this feature simply click the "Toggle Screenshot Selection" menu item again, and a message will state that the screenshot selection is disabled

2. If manual screenshot selection is disabled, then the plugin searches the directory where the user saves the .g3drem file for an image file with the same name.  If no valid image file with the same name is found in the same directory, then the plugin proceeds to Step 3.  Valid image extensions are .png, .jpg, .jpeg, .gif, and .bmp.  

For example if the user saves llama.g3drem to the dekstop and the desktop folder has a llama.jpg image file within it then the llama.jpg file will be used as the preview image on the Dremel:
![llama preview](/docs/llama.png)

3.   The plugin attempts to take a screenshot of the main Cura window as it saves out the file (see [Step 5 above](#Step5))  This is the default behavior of the plugin, and is what will happen normally if the user doesn't do anything after installation.

4.  If the screenshot fails for some reason then a generic Cura icon will be shown on the Dremel IdeaBuilder screen as the preview.

![cura icon](https://github.com/Ultimaker/Cura/blob/master/icons/cura-64.png)
---
# Note
Please note the following:
* This plugin has been tested using Cura 3.2.1 on Windows 10 x64, MacOS Sierra (MacOS 10.12), MacOS El Capitan (10.11), and Ubuntu versions 17.10 and 16.04.  If you are using another platform and encounter issues with the plugin, feel free to raise an issue with the ["Issues" section](https://github.com/timmehtimmeh/Cura-Dremel-3D20-Plugin/issues) above.
* With many thanks to [metalman3797](https://github.com/metalman3797) the Dremel 3D20 printer json definition has had an optimization pass - it should work even better now than it did before!
  * While this plugin works in the basic print case, you may still encounter problems with the print head crashing into your parts if you attempt to print multiple parts on the same print bed one-after-another instead of printing them all-at-once.
* The .g3drem file format is not fully understood yet - I've done a bit of reverse engineering on the file format, as described here: http://forums.reprap.org/read.php?263,785652 and have used the information I discovered to create this plugin, however there are still magic numbers in the Dremel header that may or may not have an effect on the print.  See more information in the [Technical Details below](#Technical_Details).
---
# Wishlist
The following items would be great to add to this plugin - any and all collaboration is welcome - feel free to raise an issue if there's a feature you'd like
* ~~Optimized print profiles for IdeaBuilder 3D20 (current non-custom profiles are pretty generic and may not work as well on the Dremel as they could)~~ **New - [Version 0.3 and above](https://github.com/timmehtimmeh/Cura-Dremel-3D20-Plugin/releases/latest):** Thanks to  [metalman3797](https://github.com/metalman3797) the print profiles have been optimized
* ~~Optimized [Dremel3D20.def.json](resources/definitions/Dremel3D20.def.json) file~~ **New - [Version 0.3 and above](https://github.com/timmehtimmeh/Cura-Dremel-3D20-Plugin/releases/latest):** Thanks to  [metalman3797](https://github.com/metalman3797) the Dremel json file has been further improved
* ~~Optimization of Dremel brand PLA settings~~  **New - [Version 0.3 and above](https://github.com/timmehtimmeh/Cura-Dremel-3D20-Plugin/releases/latest):** Thanks to  [metalman3797](https://github.com/metalman3797) the Dremel brand PLA material has been optimized.
* ~~ Creation of plugin container with Dremel printer json, material json, and printer bed mesh to ease user installation ~~
* Figure out a way Auto-install the printer bed .stl file in the same way as the other files.  
---
# <a name="Technical_Details"></a>Technical Details of the .g3drem File Format
The g3drem file format consists of a few sections.  The header is a mix of binary data and ASCII data, which is followed by an 80x60 pixel bitmap image written to the file, which is then followed by standard 3d printer gcode saved in ASCII format.

**An Example of the binary header looks like this:**

![File Header](/docs/FileHeader.JPG)

A description of the current understanding of this file format is below:

| Binary Data                                     | Description                                  |
|-------------------------------------------------|----------------------------------------------|
`67 33 64 72 65 6d 20 31 2e 30 20 20 20 20 20 20` | Ascii for 'g3drem 1.0      ' (see 1 below )  |
`3a 00 00 00 b0 38 00 00 b0 38 00 00 38 04 00 00` | Magic #s and Time(sec) (See 2 and 3 below )  |
`8f 04 00 00 00 00 00 00 01 00 00 00 19 00 03 00` | Filament(mm), Magic #s (See 4, 5, 6 and 7 )  |
`64 00 00 00 DC 00 00 00 01 ff [80x60 Bmp image]` | Magic #s and BMP image (See 8, 9, 10, 11  )  |
`[standard 3d printer gcode]`                     | Gcode in ASCII         (See 12 below      )  |

**The sections of the file are:**
1. `67 33 64 72 65 6d 20 31 2e 30 20 20 20 20 20 20` = ASCII text 'g3drem 1.0      '
2. `3a 00 00 00 b0 38 00 00 b0 38 00 00` = Some magic numbers that seem to be the same for every file
3. `38 04 00 00` = four-byte little-endian integer representing the number of seconds that the print will take
4. `8f 04 00 00` = four-byte little-endian integer representing the estimated number of millimeters of filament that the print will use
5. `00 00 00 00 01 00 00 00` = Two four-byte magic numbers that seem to be the same for every file
6. `19 00` = A two-byte number that is different in some files that I've downloaded, but seem to remain the same on all files that I've generated with both the Dremel 3D and Simplify 3D software that I have, and doesn't have an obvious effect on the print.
7. `03 00` = A two-byte magic number that always seems to be the same
8. `64 00 00 00` = Two two-byte, or one four-byte number that is different in some files that I've downloaded, but seem to remain the same on all files that I've generated with both the Dremel 3D and Simplify 3D software that I have, and doesn't have an obvious effect on the print. **Note**, the last two bytes seem to be zeros in all files I've encountered.
9. `DC 00 00 00` = Two two-byte, or one four-byte number that is different in some files that I've downloaded, but seem to remain the same on all files that I've generated with both the Dremel 3D and Simplify 3D software that I have, and doesn't have an obvious effect on the print. **Note**, the last two bytes seem to be zeros in all files I've encountered.
10. `01 ff` = Another magic numbers that don't seem to change across files, and seems to indicate the end of the header
11. An 80x60 bitmap containing the image that the Dremel 3D20 will use to display on the screen (See the usage instructions [step 5](#Step5))
12. Standard 3d printer gcode (Marlin flavor seems to be working, but if you encounter issues please feel free to raise them [here](https://github.com/timmehtimmeh/Cura-Dremel-3D20-Plugin/issues)

**Interesting observations about the file format:**
1.  The maximum number of minutes that the Dremel can read is 0xFFFFFF00, which comes out to 4660 hours and 20 minutes
2.  The maximum fiament length that the file can handle is hex 0xFFFFFFFF, or 4,294,967,295 millimeters. The [Dremel 3D software](https://dremel3d.at/pages/software) reports this value as (after some rounding): 4,294,967.5 meters
3.  The image size seems to be hardcoded inside the Dremel firmware (at least for firmware 1.3.20160621).  Storing an image that is larger than 80x60 is allowable in the file, and the Windows-based ["Dremel 3D" software](https://dremel3d.at/pages/software) will read this file with a larger image with no problem.  The Dremel 3D sofware will read and show the correct part to build, but loading this file with the larger image into the actual Ideabuilder will result in the ideabuilder successfully showing the image, and allowing the user to select it, but will result in the IdeaBuilder rebooting when the user tries to print the file.
---
# Contributors:
Many thanks belong to the following users, who have spent their time and energy to report issues and help make the plugin better:
* [WeavingColors](https://github.com/WeavingColors)
* [SwapFaceL](https://github.com/SwapFaceL)
* [metalman3797](https://github.com/metalman3797)
