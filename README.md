# Low-Cost VR
This guide is for anyone with a PC and an Android phone looking to get their feet wet with VR gaming on a budget. It is the result of many hours of googling on my part trying to do exactly that. Hopefully it will save you some time.

## You Will Need
1. A capable Windows gaming computer
   This setup works on my Lenovo Legion 5 (i7-12700h, 16GB DDR5, RTX 3060) but it should theoretically work on any computer that meets the [system requirements](https://store.steampowered.com/app/250820/SteamVR/) for SteamVR.
2. An Android phone running Android 8.0 or above. See the [README for PhoneVR](https://github.com/alvr-org/PhoneVR/blob/master/README.md)
3. A VR headset phone accessory. This could be a Google Cardboard, Google Daydream, or any other headset intended for use with a phone in steroscopic VR apps. I am using a HYPER VR headset I picked up from a thrift store for under $10 that also has built-in headphones and volume control.
4. A **LONG** USB cable. Depending on your phone this could be a USB Micro-B or Type-C but it needs to be at least 8ft long for an unhindered VR experience.
5. A game controller of some sort. Choose your favorite.

## Software Setup
### 1. Install Steam
If you don't already have it, download and install Steam from the [Steam Store](https://store.steampowered.com/about). Steam will be our source of VR games and will also allow us to install SteamVR in the next step. Once Steam is installed, open it. You will be prompted to create an account and log in.

### 2. Install SteamVR
Once you are logged in to Steam, navigate to the Store tab and search for SteamVR. Download and install the first item that comes up. SteamVR will be our VR environment and will let us play VR games on Steam.
> **WARNING for those with metered connections:**
> SteamVR has a download size of approximately 2 GB, so if it's near the end of the month and you're almost out of data, you may want to either use public WiFi if you have a portable laptop or wait till next month if you have an immobile desktop PC.

### 3. Install PhoneVR
PhoneVR is an open-source Android app that plays a SteamVR video stream from a PC on a phone and sends the phone's orientation back to the PC. To install, go to PhoneVR's [releases](https://github.com/alvr-org/PhoneVR/releases/latest) page on your phone. Note the latest version of ALVR compatible with PhoneVR. Under Assets, download PhoneVR-vX.X.X-beta.apk. When the file is finished downloading, open it and select "Package Installer" if prompted to choose an app to open it with. Follow the prompts to finish installation.

### 4. Install ALVR
ALVR is an open-source software that streams the video feed from SteamVR to a VR headset (or in our case, an Android phone). To install, visit ALVR's [releases](https://github.com/alvr-org/ALVR/releases) page and find the latest version of ALVR compatible with PhoneVR. Under its Assets, download alvr_streamer_windows.zip. Once downloaded, extract it to a directory **that contains only ASCII characters and has edit permissions without administrator rights** (See [ALVR installation guide](https://github.com/alvr-org/ALVR/wiki/Installation-guide)).

### 5. Install VB Cable
VB Cable is a virtual audio cable that will allow us to use the microphone. To install, visit the [VB-Cable website](https://vb-audio.com/Cable/) and click the Windows download button. VBCable_Driver_PackXX.zip will be downloaded. Extract the zip to any directory and run VBCable_Setup.exe to install the driver.

## Now for the fun part!
### Enable USB Tethering
Connect your phone to your PC with the long USB cable and enable USB tethering on the phone (On Android 12, this can be found inn Settings > Connections > Mobile Hotspot and Tethering > USB tethering).
> **Note:** Your phone must have a plan that includes mobile hostpot and tethering for this to work. If you don't have such a plan, follow the instructions [here](https://github.com/alvr-org/ALVR/wiki/ALVR-wired-setup-(ALVR-over-USB)) to set up ALVR over ADB.
Now you need to find your phone's IP address on the tethering network. Open a command prompt by typing "cmd" in the Windows search box and pressing Enter. Type the following command:
   ipconfig
A list of all of your connected network interfaces will be shown. Find the only Ethernet adapter that contains an "IPV4 Address" field. Jot down the number in this field. This your phone's IP address.

### Configure PhoneVR
Open the PhoneVR app on your phone. Turn on "Remember my choice" and select the ALVR server. You will be prompted to accept permissions; click "Allow" for all of them. A camera window will open. Scan your VR headset's Google Cardboard QR code if present, or skip. You may be promtped to accept storage permissions. On Android 12, you would need to go to Settings > Apps > PhoneVR > Permissions > Files and media and select "Allow access to media only." You should now be in stereoscopic (side by side) view. You can now put your phone into your VR headset. You won't see much right now, but you should see a hostname something along the lines of XXXX.client. Jot that down as we will use it in the next step.

### Configure ALVR
Launch SteamVR on your PC and close it. This prepares the environment for ALVR. Then open the ALVR Dashboard (double-click "ALVR Dashboard.exe" in the directory in which you extracted ALVR). Open the Settings tab and adjust settings as follows:
1. Under Presets, set the resolution to Low and the Preferred framerate to 60Hz.
2. Under Headset, turn off Controllers
3. Under Connection, set the Stream protocol to TCP.
4. Under Installation, click Register ALVR driver.
Finally, navigate to the Connections tab (not Settings > Connection). Click "Add client manually" and put in what you jotted down for the hostname. Click "Add new" under IP Address and put in what you jotted down for your phone's IP address earlier. Then click Save.

### Experience VR!
Launch SteamVR. Your phone should automatically connect to your computer and show the SteamVR video feed. Connect your gamepad to your computer and you should be ready to game!

## Going Further
Want even more immersion? Here are some extra instructions for an even better VR experience.

### Body tracking
If you also want to have support for body tracking for games like VRChat, you will need a Kinect sensor and Amethyst software from K2VR. Open the Microsoft Store on your computer and search for Amethyst. Click on "Amethyst - Open Source Body Tracking" and install it. Once it is installed, open it and follow the instructions to get it up and running.
> **Note:** If you have a Kinect v1 (the Xbox 360 Kinect), you will need to disable Memory Integrity to install the driver. To do this, search for "Core isolation" in the Windows search bar and click the first thing that comes up. Turn off the switch under Memory Integrity.

### Hand Tracking
This is still a **work in progress**. I have yet to figure this one out, but I am currently looking into a solution that uses [matzman666/OpenVR-InputEmulator](https://github.com/matzman666/OpenVR-InputEmulator) and Wiimotes. I'd love to hear any other ideas you come up with.

If there are any issues/inconsistencies/updates in this guide that need adddressing, please post a GitHub Issue. Hope this helps!