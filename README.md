# Lenovo-G570-Hackintosh
[WIP] MacOS High Sierra on Lenovo G570 (20079) using the OpenCore Bootloader 

[DISCLAIMER]
Before you proceed any further, you, the reader and a probable user of this EFI, accept that all changes that you are willing to perform on 
your personal G570 computer are at your own risk, and that I will NOT BE HELD RESPONSIBLE if you managed to summon 
a nuke to your location or if you managed to bring world peace by letting aliens take over our planet... 
(the irony)

Hello, true believers and newcomers alike!
Here is the EFI that I used to get Hackintosh High Sierra working on my Lenovo G570 20079

My Specs:-
Core i3 2310M
iHD 3000 (iGPU only, no dGPU for me)
8GB (2x4GB) Samsung DDR3L RAM
Crucial MX250 SSD
Dying keyboard
nice battery (90% health xd)
moar?

Notes/observations:- 
1.) Legacy systems can't boot GPT. But, OpenCore can only boot GPT boot drives and thus, duetpkg will be used.
2.) Post installation, disable SIP and use the BootInstallx64.command found in Utilities to flash the boot drive 
    so that the laptop can be booted without the USB drive.
> The above step is important as (in my experience) the nvram patch works only when the EFI is in the boot drive, but not when booting off of USB.
3.) To fix sleep, use XOSI SSDT. However, sleep acts weird. When the device is woke up post sleep, it boots back to BIOS and then to OS.
(Maybe it doesn't know the boot drive UUID?) 
4.) All SSDTs are self-compiled. No prebuilts were used. So, I'm omitting them from my repo. The list of SSDTs required will be posted soon on the wiki?
5.) Touchpad is wonky right after booting. It settles after a while but deadzones are fucked. Buttons work using the kext included in this repo. (Thanks to 1Revenger1)
6.) My wifi card is cooked, I don't know why. It works. Period. 
7.) Native b0rightness control keys do not work, managed to remap brightness keys shortcuts to F6 and F7 from system settings but this option disappeared after injecting edid via hackintool (removing it did not work, so did rebuilding kext cache)
8.) Occasional glitches to the UI and a freeze when AppStore is loaded in the background. Meh, pretty common for me on Windows so I didn't bother.
9.) Inbuilt mic is fucked, along with external 3.5mm mic. BT is da wae? or Camo Studio yay!
10.) Used the lenovo T470 AppleHDA layout-id as it is identical. 
11.) Don't forget to enable TRIM else SSD fuck-up soon...
12.) Use ECEnabler for fixing battery readouts
More?  

Hackintosh Checklist - What's working?
Desktop and General
OpenCore Booting
[✔️] Correct OS choices shown in OpenCore Menu/GUI
[✔️] Keyboard shortcuts working (only USB external keyboard, not native PS/2)
[✔️] NVRAM working (No log during boot saying NVRAM not found)
[✔️] Security (especially SIP) use Menu Bar SIP Detector
[?] FileVault
[?] Multibooting

Display
[ ] Display via HDMI
[ ] Display via VGA
[✔️] Resolution
[✔️] Refresh rates
[ ] Multimonitor displays

Graphics Acceleration
[ ] dGPU dedicated GPU (No dGPU for me)
[✔️] iGPU internal GPU
[✔️] QE/CI (full acceleration requires both Quartz Extreme and Core Image)
[✔️] VDA (Video Decode Acceleration framework)
[X] Metal (Was it ever supported on the Intel HD 3000?)

GLView

Geekbench -> Compute -> Metal

Audio
[✔️] Audio out (Audio MIDI Setup)
[-] Audio in
[-] Sidepanel audio connectors (audio out ok, audio in dead)
[?] Audio over HDMI
[✔️] Audio quality (on par with Linux, but ok for me)

Sleep & Power
[✔️] Manual Sleep (Apple menu -> Sleep) (Fixed after adding XOSI)
[?] Auto Sleep (System preferences -> Energy Saver) (I remember my Hackintosh random rebooting after this, so, unsure...)
[✔️] Wake by keyboard
[X] Wake by mouse/trackpad
[?] Sleep by Press and hold power button for 1.5 seconds
[✔️] Shutdown (from Apple menu)
[✔️] Restart (from Apple menu)

CPU
[ ] CPU Power Management Optimizing Power Management
Check with IORegistryExplorer

[ ] Temperatures and stability with 100% CPU
Use Prime95 Torture Test

Disk
Test with Blackmagic Disk Speedtest
[✔️] SATA SSD
[✔️] TRIM support (System Information -> SATA -> SSD drive)

Keyboard
[✔️] Option/Command correctly mapped in macOS
For PC Keyboards swap in: System preferences -> Keyboard -> Modifier Keys

[✔️] Fn keys working

USB
Use USBMap (?)

Test external drives with Blackmagic Disk Speedtest

[✔️] USB 2 ports
[?] SD Card Reader
[✔️] Camera (Photo Booth, Facetime, Zoom)

Ethernet
[✔️] Gigabit LAN (System preferences -> Network -> Ethernet -> Advanced -> Hardware -> Speed should be 1000baseT)

Wifi & Bluetooth
[✔️] Wifi transmission speed (Option Click -> Wifi menu bar icon -> check Tx Rate)
[✔️] Bluetooth devices (trackpad, mouse, keyboard, headset)
[ ] AirDrop (test with iDevices)

OS Features
[ ] iMessage, FaceTime, App Store, iTunes Store
[ ] DRM support (iTunes Movies, Apple TV+, Amazon Prime and Netflix, and others)

Display
[✔️] Backlight setting

Audio
[✔️] Speaker (built-in)
[X] Microphone (built-in)

Sleep & Power
[X] Sleep by close lid
[?] Sleep by close lid with external display
[?] Wake by open lid

Battery
[✔️] Showing percentage
[✔️] Showing capacity/health
[✔️] Charge plug/unplug detected

Trackpad
[✔️] Basic functions
[✔️] Gestures

Changelog:-
> 20 November 2022
The blind build is back, except it is now more raw and messed up.
But hey, it boots, so, profit?
I blame incycledream for guilting me into doing this again. Wrapped it up in 2 hrs. tops, nice record xD
There's a lot of work to do, NGL. Checklist soon

> 4th March 2022
placed files needed for duetpkg to read OCBL.
USB boots (finally) but throws a kernel panic error, which i cannot fix with my expertise rn

> 3 March 2022 = fail
WIP! NOT READY! WILL BE, SOON...
PS:- I had more luck booting off of a blunt USB on the first try than this calculated approach. How ironic 
