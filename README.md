# Lenovo-G570-Hackintosh
[WIP] MacOS High Sierra on Lenovo G570 (20079) using OpenCore 

[DISCLAIMER]
Before you proceed any further, you, the reader, accept that all changes that you are willing to perform on 
your personal computer are at your own risk, and that I will NOT BE HELD RESPONSIBLE if you managed to summon 
a nuke to your location or if you managed to bring world peace by letting aliens take over our planet... 
(the irony)

Hello, true believers and newcomers alike!
Here is the EFI that I will be using to get Hackintosh OC High Sierra to work on my Lenovo G570 20079

My Specs:-
Core i3 2310M
iHD 3000 (iGPU only, no dGPU for me) (sad noises)
8GB (2x4GB DDR3L)
Crucial MX250 SSD
dying keyboard
nice battery
moar?

Notes/observations:- 
Legacy systems can't boot GPT, but the usage of GPT USB is unavoidable because that's the M.O of OCBL.
Using bootice, duetpkg will be flashed which gets written @ the MBR and PBR of boot USB, enabling users to boot GPT on legacy
(intuitive, indeed)
This device does not need USB patching IMO (Please, CMIIW. I don't "explicitly" remember applying USB Patches)
IRQ is self-compiled and ACPI-patched in config.plist, rest are prebuilt.

What works/doesn't?
Hackintosh Checklist - What's working?
Desktop and General
OpenCore Booting
[ ] Correct OS choices shown in OpenCore Menu/GUI

[ ] Keyboard shortcuts working (see details below)

CMD+V — verbose mode.

[ ] NVRAM working Verifying if you have working NVRAM

Apple -> System Preferences -> Startup Disk (uses NVRAM).

[ ] Security (especially SIP) use Menu Bar SIP Detector

[ ] FileVault

[ ] Multibooting

Display
[ ] Display via HDMI

[ ] Display via DisplayPort

[ ] Display via DVI

[ ] Resolution

[ ] Refresh rates

[ ] Multimonitor displays

Graphics Acceleration
[ ] dGPU dedicated GPU

In Terminal: gfxutil -f GFX0 or check in IORegistryExplorer

[ ] iGPU internal GPU

In Terminal: gfxutil -f IGPU or check in IORegistryExplorer

[ ] QE/CI (full acceleration requires both Quartz Extreme and Core Image)

Check for transparent menu bar and fast smooth UI.

[ ] VDA (Video Decode Acceleration framework)

Hackintool -> System -> System -> VDA Decoder (should show 'fully supported')

[ ] Metal

System Information -> Graphics/Displays -> Metal: Supported

GLView

Geekbench -> Compute -> Metal

Audio
[ ] Audio out (Audio MIDI Setup)

[ ] Audio in

[ ] Frontpanel audio connectors

[ ] Audio over HDMI

[ ] Audio quality

Sleep & Power
[ ] Manual Sleep (Apple menu -> Sleep)

[ ] Auto Sleep (System preferences -> Energy Saver)

[ ] Wake by keyboard

[ ] Wake by mouse/trackpad

[ ] Sleep by Press and hold power button for 1.5 seconds

[ ] Shutdown (from Apple menu)

[ ] Restart (from Apple menu)

CPU
[ ] CPU Power Management Optimizing Power Management

Check with IORegistryExplorer

[ ] Temperatures and stability with 100% CPU

Use Prime95 Torture Test

Disk
Test with Blackmagic Disk Speedtest

[ ] NVMe SSD

[ ] SATA SSD

[ ] TRIM support (System Information -> SATA -> SSD drive)

Keyboard
[ ] Option/Command correctly mapped in macOS

For PC Keyboards swap in: System preferences -> Keyboard -> Modifier Keys

[ ] Fn keys working

USB
Use USBMap

Test external drives with Blackmagic Disk Speedtest

[ ] USB 2 ports

[ ] USB 2 on USB 3 ports

[ ] USB 3 and 3.1 ports (check transfer speed during copy)

[ ] USB C ports

[ ] SD Card Reader

[ ] Camera (Photo Booth, Facetime, Zoom)

[ ] Fingerprint reader

ThunderBolt
[ ] File transfer

[ ] Display

Ethernet
[ ] Gigabit LAN (System preferences -> Network -> Ethernet -> Advanced -> Hardware -> Speed should be 1000baseT)

[ ] 2.5GBase-T (especially on Comet Lake and above boards)

[ ] 10GBase-T (Aquantia with updated firmware)

Wifi & Bluetooth
[ ] Wifi transmission speed (Option Click -> Wifi menu bar icon -> check Tx Rate)

[ ] Bluetooth devices (trackpad, mouse, keyboard, headset)

[ ] AirDrop (test with iDevices)

[ ] AirPlay to Mac (macOS Monterey or later, test with iOS 14 or later devices)

tap the AirPlay icon on your Apple device to share videos to your Hackintosh

[ ] Handoff System requirements for Continuity and Use Continuity which requires macOS Catalina & iOS 13+

[ ] Sidecar requires macOS Catalina or later and a compatible iPad using iPadOS 13 or later.

OS Features
[ ] iMessage, FaceTime, App Store, iTunes Store

[ ] DRM support (iTunes Movies, Apple TV+, Amazon Prime and Netflix, and others)

Laptop Specific
additional checks relevant for Notebooks including MacBooks with Legacy Patchers

Display
[ ] Backlight setting

[ ] Backlight sensor

[ ] Backlight Fn keys

Audio
[ ] Speaker (built-in)

[ ] Microphone (built-in)

Sleep & Power
[ ] Sleep by close lid

[ ] Sleep by close lid with external display

[ ] Wake by open lid

Battery
[ ] Showing percentage

[ ] Showing capacity/health

coconutBattery

[ ] Charge plug/unplug detected

Trackpad
[ ] Basic functions

[ ] Gestures

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
