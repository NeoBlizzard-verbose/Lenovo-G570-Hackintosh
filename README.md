# Lenovo-G570-Hackintosh
[Test][WIP] MacOS High Sierra on Lenovo G570 (20079) using OpenCore 

Hello, true believers and newcomers alike!
Here is the EFI that I will be using to get Hackintosh OC High Sierra to work on my Lenovo G570 20079

Specs <here/>

Note:- 
Legacy systems can't boot GPT, but the usage of GPT USB is unavoidable because that's the M.O of OCBL.
Using bootice, duetpkg will be flashed (ig?) which gets written @ the MBR and PBR of usb, enabling users to boot GPT on legacy
(intuitive, indeed)

IRQ is self-compiled and ACPI-patched in config.plist, rest are prebuilt.

3 march 2022 = fail
WIP! NOT READY! WILL BE, SOON...

4th march 2022
placed files needed for duetpkg to read OCBL.
USB boots (finally) but throws a kernel panic error, which i cannot fix with my expertise rn

PS:- I had more luck booting off of a blunt USB on the first try than this calculated approach. How ironic 
