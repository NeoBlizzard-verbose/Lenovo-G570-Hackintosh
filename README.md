# Lenovo-G570-Hackintosh
[WIP] MacOS High Sierra on Lenovo G570 (20079) using the OpenCore Bootloader 0.8.9
Can also boot Mojave (preferred) and Catalina optionally with dosdude1's patched installers.
(you need to patch some things manually without patched installer)
# CAUTION
IMAC SMBIOS DOESN'T WORK PROPERLY, DON'T EVER TRY TO GET SUPPORT, IT'S UNUSABLE
- TESTED ON: CATALINA AND [BIG SUR](https://codeberg.org/satan/HackintoshNext-G570)
## [DISCLAIMER]
Before you proceed any further, you, the reader and a probable user of this EFI, accept that all changes that you are willing to perform on 
your personal G570 computer are at your own risk, and that I will NOT BE HELD RESPONSIBLE if you managed to summon 
a nuke to your location or if you managed to bring world peace by letting aliens take over our planet... 
(the irony)
That said, if your G570's specifications are as accurate as mine, it shouldn't be a problem using this EFI OOTB. Adapt this EFI to your laptop
with due diligence and use responsibly.
## ——————————
Hello, true believers and newcomers alike!
Here is the EFI that I used to get MacOS working on my Lenovo G570 (20079).
I currently use Catalina. Thus, some information here is adopted for Catalina ONLY! I will try to include more for <10.15.x

# Notes:
- EFI is up to date, but you need to do more stuff.
- GenSMBIOS for serial (patch as MBP8,1 or MBP10,1)
- OC beauty treatment -> resources folder -> paste accordingly

# Tested on:
#### NeoBlizzard
- macOS: 10.15.7
- SMBIOS: MacBookPro8,1
- CPU: Intel Core i3 2310M
- GPU: Intel HD 3000 (iGPU only, no dGPU for me)
- RAM: 8GB (2x4GB) Samsung DDR3L RAM
- SSD: Crucial MX250
- Audio: Conexant CX20590
- Bluetooth: Broadcom Bluetooth 2.1+EDR
- WiFi card: BCM94322HM8L
- ACPI\VPC2004 YogaSMC included
- 1366x768 BOE display panel
- Unlocked BIOS ADV+NWL (40CN33WW)

#### incycledream
- macOS: 10.15.7
- SMBIOS: MacPro5,1
- CPU: Intel Core i5 2410M
- GPU: Intel HD 3000, Radeon HD 3670M (384 > 2048 MB patch)
- RAM: 4GB (2x2GB) Samsung DDR3L RAM
- SSD: Apacer Panther AS340
- Audio: Conexant CX20590
- Bluetooth: Broadcom Bluetooth 2.1+EDR
- WiFi card: Atheros AR9285
- ACPI\VPC2004 YogaSMC included
- 1366x768 BOE display panel
- Locked BIOS (40CN33WW)

# Notes/observations:
- Legacy systems can't boot GPT. But, OpenCore can only boot GPT boot drives and thus, duetpkg will be used automagically by OpenCorePkg.
- Press the power button twice to boot laptop from a shutdown if you have ADV+NWL BIOS
- Post installation, disable SIP and use the BootInstallx64.command found in "Utilities" to patch the boot drive 
    so that the laptop can be booted without the USB drive.
The above step is important as (in my experience) the NVRAM patch works only when the EFI is in the boot drive, but not when booting off of USB.
- To fix sleep, use XOSI SSDT. However, sleep acts weird. When the device is woke up post sleep, it boots back to BIOS and then to OS.
(Maybe it doesn't know the boot drive UUID?) 
I WON'T FIX SLEEP
- All SSDTs are compiled. No prebuilts were used.
Fixed SMBusPCI, NumLockIndicator, ECRW on YogaSMC with battery notifier when Conservative mode is enabled (Thanks to oc-little guide)
- Thanks to 1Revenger1 for ultimate fixes to the Synaptics touchpad. However, Touchpad is wonky for a while after booting. Eventually works good.
- Mapped USB for Catalina, USE USBMAP TO EDIT THE IOCLASS FOR VERSIONS LOWER THAN CATALINA!!
- Too many controls to control brightness. I gave up eliminating the others since I stopped bothering.
- Display artefacts exist, even after patches. Even EDID patching didn't help.
- Occasional freezes when multitasking heavily, so, tread lightly (ig?)
- Tried to fix resolution during picker but gave up.  
- Inbuilt Keyboard does not work in OpenCore boot menu. Internal trackpad and external keyboard/mouse work fine. 
- Boot chime enabled. Using VoodooHDA as it has internal mic working. Mic port is still dead and I don't have any interest to write custom AppleALC codec

# Hackintosh Checklist - What's working?
## Desktop and General
### OpenCore Booting
- [✔️] Correct OS choices shown in OpenCore Menu/GUI
- [✔️] Keyboard shortcuts working (only USB external keyboard, not native PS/2)
- [✔️] NVRAM working (No log during boot saying NVRAM not found)
- [✔️] Security (especially SIP) use Menu Bar SIP Detector
- [?] FileVault
- [✔️] Multibooting

### Display
- [✔️] Display via HDMI
- (window borders may be shown incorrectly on a monitor)
- [?] Display via VGA
- [✔️] Resolution
- [✔️] Refresh rates
- [✔️] Multimonitor displays
- [✔️] Backlight setting

### Graphics Acceleration
#### Dedicated GPU:
- [❌] Radeon HD 6370M [tested by incycledream long time ago]
- [?] NVIDIA GeForce GT 410M [not tested]
#### ——————————
- [✔️] iGPU internal GPU
- [✔️] QE/CI (full acceleration requires both Quartz Extreme and Core Image)
- [✔️] VDA (Video Decode Acceleration framework)
- [❌] Metal (Was it ever supported on the Intel HD 3000?)

### GLView
- Geekbench -> Compute -> Metal

### Audio
- [✔️] Audio out (Audio MIDI Setup)
- [-] Audio in
- [-] Sidepanel audio connectors (audio out ok, audio in dead)
- [?] Audio over HDMI
- [✔️] Audio quality (on par with Linux, but ok for me)
- [✔️] Speaker (built-in)
- [❌] Microphone (built-in)

### Sleep & Power
- [✔️] Manual Sleep (Apple menu -> Sleep) (Fixed after adding XOSI)
- [?] Auto Sleep (System preferences -> Energy Saver) (I remember my Hackintosh random rebooting after this, so, unsure...)
- [✔️] Wake by keyboard
- [❌] Wake by mouse/trackpad
- [?] Sleep by Press and hold power button for 1.5 seconds
- [✔️] Shutdown (from Apple menu)
- [✔️] Restart (from Apple menu)
- [❌] Sleep by close lid
- [?] Sleep by close lid with external display
- [?] Wake by open lid
- [✔️] Battery Conservation mode (Using YogaSMC)

### Battery
- [✔️] Showing percentage
- [✔️] Showing capacity/health
- [✔️] Charge plug/unplug detected

### CPU
- [  ] CPU Power Management Optimizing Power Management
Check with IORegistryExplorer
- [ ] Temperatures and stability with 100% CPU
Use Prime95 Torture Test

### Drive
- Test with Blackmagic Disk Speedtest
- [✔️] SATA SSD
- [✔️] TRIM support (System Information -> SATA -> SSD drive)

### Keyboard
- [✔️] Option/Command correctly mapped in macOS
For PC Keyboards swap in: System preferences -> Keyboard -> Modifier Keys
- [-] Fn keys working

### USB
- [?] Use USBMap

### External devices
- Test drives with Blackmagic Disk Speedtest
- [✔️] USB 2 ports
- [?] SD Card Reader
- [✔️] Camera (Photo Booth, Facetime, Zoom)

### Trackpad
- [✔️] Basic functions
- [✔️] Gestures

### Ethernet
- [✔️] Gigabit LAN (System preferences -> Network -> Ethernet -> Advanced -> Hardware -> Speed should be 1000baseT)

### Wifi & Bluetooth
- [✔️] Wifi transmission speed (Option Click -> Wifi menu bar icon -> check Tx Rate)
- [✔️] Bluetooth devices (trackpad, mouse, keyboard, headset)
- [  ] AirDrop (test with iDevices)

### OS Features
- [  ] iMessage, FaceTime, App Store, iTunes Store
- [  ] DRM support (iTunes Movies, Apple TV+, Amazon Prime and Netflix, and others)

### Changelog:
- 3 March 2022 = fail
> WIP! NOT READY! WILL BE, SOON...
> PS:- I had more luck booting off of a blunt USB on the first try than this calculated approach. How ironic 

- 4 March 2022
> placed files needed for duetpkg to read OCBL.
> USB boots (finally) but throws a kernel panic error, which i cannot fix with my expertise rn

- 20 November 2022
> The blind build is back, except it is now more raw and messed up.
> But hey, it boots, so, profit?
> I blame incycledream for guilting me into doing this again. Wrapped it up in 2 hrs. tops, nice record xD
> There's a lot of work to do, NGL. Checklist soon

- 15 February 2023
> Much needed improvements were made. Sorry for the fucked layout. I'll try to fix it (soon)

- 1 March 2023 (incycledream)
> I fixed the fucked layout

- 7 March 2023 (incycledream)
> BIG SUR INSTALLER BOOTED SUCCESSFULLY.
> graphics doesn't work but I'll try to do something with my Terascale 2 GPU
<img src="https://files.catbox.moe/xyav88.jpg">
