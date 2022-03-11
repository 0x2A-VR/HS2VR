# This project is not being maintained anymore. Check out other forks (e.g. https://github.com/OrangeSpork/HS2VR) if you encounter issues or want to contribute.

# About

This is a hack to get VR functionality into Honey Select 2, since the offical VR mode hadn't been released yet. Unless someone makes a proper release of VRGIN that works with HS2, consider this project abandoned.

Credit for the underlying library (VRGIN) goes to Eusth (https://github.com/Eusth/VRGIN) and Ooetksh for their AI-Shoujo version.
The present Honey Select 2 VR mod is based off (https://github.com/Ooetksh/KoikatuVR). 

# Installation
## Enabling VR
**This may not be necessary anymore now that native VR is supported but I haven't tested this yet.** The current build of HS2 doesn't have the Unity VR mode enabled. To enable VR, follow these steps (taken from https://github.com/vrhth/KoikatuVR):

- Get UABE (https://github.com/DerPopo/UABE).
- Open `HoneySelect2_Data/globalgamemanagers`
- Find the asset of Type BuildSettings
- Export Dump
- Open the exported dump with a text editor and change the lines

```
0 vector enabledVRDevices
0 Array Array (0 items)
0 int size = 0
```
to
```
0 vector enabledVRDevices
0 Array Array (2 items)
0 int size = 2
[0]
1 string data = "None"
[1]
1 string data = "OpenVR"
```
- Import Dump and save. It won't allow you to overwrite the file in the game directory, so save it somewhere else and make a backup of your original `globalgamemanagers` before copying your patched version into `HoneySelect2_Data`.

You can also find a pre-patched `globalgamemanagers` on discord.

To check that VR is working, start Steam VR and run `HoneySelect2.exe` with the the option `-vrmode "OpenVR"`. This should show the game in VR, albeit without any UI.

## Install the mod

Copy `BebInEx` and `HoneySelect2_Data` folders into your game directory. That should deposit `HS2VR` in `BebInEx/plugins` and `openvr_api.dll` in `HoneySelect2_Data/Plugins`.

If SteamVR is running, the game should start in VR mode. If you need to force the game into non-VR mode while SteamVR is running and don't want to disable the VR mod for whatever reason, pass the `--novr` command line argument.

## Controls
The controls follow the `VRGIN` setup: 
- The B/Y buttons switch the current tool.
- The menu tool gives access to the UI. Use the grip button to grap the UI plane and reposition it.
- The warp tool allows movement. Grip button moves the camera, grip+trigger rotates it. Clicking the touchpad warps the camera to the indicated location.
- The play tool allows for interaction during H-Scenes. For now, moving the touchpad up/down acts as the mouse wheel for starting, speed up, and speed down. Pressing touchpad left/right cycles through the finish options, pressing in the center actives the current active option.

# Building from source

The mod currently uses a patched `VRGIN.dll` from the AI-Shoujo VR mod by Ooetksh, not the included git submodule. Once that version of VRGIN makes it onto github, the repo can be updated to include it.

# Known issues
- Camera placement is buggy. The effects of Unity XR input tracking, SteamVR, and whatever VRGIN is doing on the various cameras is less than clear to me. If someone knows how that stuff works, please let me know.
- During scene transitions seizure-iduction flickering is happening. Until that is fixed, just close your eyes ¯\\_(ツ)_/¯.
- Mirrors don't work properly. 
- Resolution of UI is crap.
