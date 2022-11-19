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
TBA

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
