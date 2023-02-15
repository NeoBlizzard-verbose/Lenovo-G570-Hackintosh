NOTE:- EFI is up to date, but you need to do more stuff.
       GenSMBIOS for serial (patch as MBP8.1)
       OC beautification process -> resources folder -> paste accordingly
       
# Lenovo-G570-Hackintosh
[WIP] MacOS High Sierra on Lenovo G570 (20079) using the OpenCore Bootloader.
Can also boot Mojave (preferred) and Catalina with dosdude1's patched installers.

[DISCLAIMER]
Before you proceed any further, you, the reader and a probable user of this EFI, accept that all changes that you are willing to perform on 
your personal G570 computer are at your own risk, and that I will NOT BE HELD RESPONSIBLE if you managed to summon 
a nuke to your location or if you managed to bring world peace by letting aliens take over our planet... 
(the irony)
That said, if your G570's specifications are as accurate as mine, it shouldn't be a problem using this EFI OOTB. Adapt this EFI to your laptop
with due diligence and use responsibly.

Hello, true believers and newcomers alike!
Here is the EFI that I used to get MacOS working on my Lenovo G570 (20079).
I currently use Catalina. Thus, some information here is adopted for Catalina ONLY! I will try to include more for <10.15.x

My Specs:-
Intel Core i3 2310M
iHD 3000 (iGPU only, no dGPU for me)
8GB (2x4GB) Samsung DDR3L RAM
Crucial MX250 SSD
Conexant CX20590
Broadcom Bluetooth 2.1+EDR
BCM94322HM8L WiFi card
ACPI\VPC2004 YogaSMC included
1366x768 BOE display panel
Unlocked BIOS ADV+NWL (40CN33WW)
more...

Notes/observations:- 
1.) Legacy systems can't boot GPT. But, OpenCore can only boot GPT boot drives and thus, duetpkg will be used automagically by OpenCorePkg.
2.) Post installation, disable SIP and use the BootInstallx64.command found in "Utilities" to patch the boot drive 
    so that the laptop can be booted without the USB drive.
The above step is important as (in my experience) the NVRAM patch works only when the EFI is in the boot drive, but not when booting off of USB.
3.) To fix sleep, use XOSI SSDT. However, sleep acts weird. When the device is woke up post sleep, it boots back to BIOS and then to OS.
(Maybe it doesn't know the boot drive UUID?) 
I WON'T FIX SLEEP
4.) All SSDTs are compiled. No prebuilts were used.
Fixed SMBusPCI, NumLockIndicator, ECRW on YogaSMC with battery notifier when Conservative mode is enabled (Thanks to oc-little guide)
5.) Thanks to 1Revenger1 for ultimate fixes to the Synaptics touchpad. However, Touchpad is wonky for a while after booting. Eventually works good.
6.) Mapped USB for Catalina, USE USBMAP TO EDIT THE IOCLASS FOR VERSIONS LOWER THAN CATALINA!!
7.) Too many controls to control brightness. I gave up eliminating the others since I stopped bothering.
8.) Display artefacts exist, even after patches. Even EDID patching didn't help.
9.) Occasional freezes when multitasking heavily, so, tread lightly (ig?)
10.) Tried to fix resolution but gave up.  
13.) Inbuilt Keyboard does not work in OpenCore boot menu. Internal trackpad and external keyboard/mouse work fine. 
14.) Boot chime enabled.

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

[-] Fn keys working

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
[✔️] Battery Conservation mode (Using YogaSMC)

Battery
[✔️] Showing percentage
[✔️] Showing capacity/health
[✔️] Charge plug/unplug detected

Trackpad
[✔️] Basic functions
[✔️] Gestures

Changelog:-
> 15 February 2023
Much needed improvements were made. 

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
