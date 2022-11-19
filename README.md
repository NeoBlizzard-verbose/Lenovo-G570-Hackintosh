# Lenovo-G570-Hackintosh
[WIP] MacOS High Sierra on Lenovo G570 (20079) using OpenCore 

Hello, true believers and newcomers alike!
Here is the EFI that I will be using to get Hackintosh OC High Sierra to work on my Lenovo G570 20079

Specs <here/>

Notes:- 
Legacy systems can't boot GPT, but the usage of GPT USB is unavoidable because that's the M.O of OCBL.
Using bootice, duetpkg will be flashed which gets written @ the MBR and PBR of boot USB, enabling users to boot GPT on legacy
(intuitive, indeed)
This device does not need USB patching IMO (Please, CMIIW. I don't "explicitly" remember applying USB Patches)
IRQ is self-compiled and ACPI-patched in config.plist, rest are prebuilt.

3 March 2022 = fail
WIP! NOT READY! WILL BE, SOON...

4th March 2022
placed files needed for duetpkg to read OCBL.
USB boots (finally) but throws a kernel panic error, which i cannot fix with my expertise rn

PS:- I had more luck booting off of a blunt USB on the first try than this calculated approach. How ironic 

20 November 2022

The blind build is back, except it is now more raw and messed up.
But hey, it boots, so, profit?
I blame incycledream for guilting me into doing this again. Wrapped it up in 2 hrs. tops, nice record xD
There's a lot of work to do, NGL. Checklist soon
