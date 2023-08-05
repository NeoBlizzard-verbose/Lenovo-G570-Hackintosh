# Lenovo-G570-Hackintosh
[EOL] Boot OS X on Lenovo G570 (20079) using the OpenCore Bootloader

Tested on High Sierra, Mojave (preferred) and Catalina (the latter two with dosdude1's patched installers)

Wanna go on an adventure? [Big Sur](https://codeberg.org/satan/HackintoshNext-G570)

# Notes:
- EFI is finally up to date and EOL.
- Use GenSMBIOS to inject DeviceProperties before first boot! (patch as MBP8,1 or MBP10,1 depending on the OS version)

<details>
<summary>Changelog</summary>

#### - 3 March 2022 = fail
- WIP! NOT READY! WILL BE, SOON...
- PS:- I had more luck booting off of a blunt USB on the first try than this calculated approach. How ironic 

#### - 4 March 2022
- placed files needed for duetpkg to read OCBL.
- USB boots (finally) but throws a kernel panic error, which i cannot fix with my expertise rn

#### - 20 November 2022
- The blind build is back, except it is now more raw and messed up.
- But hey, it boots, so, profit?
- I blame incycledream for guilting me into doing this again. Wrapped it up in 2 hrs. tops, nice record xD
- There's a lot of work to do, NGL. Checklist soon

#### - 15 February 2023
- Much needed improvements were made. Sorry for the fucked layout. I'll try to fix it (soon)

#### - 1 March 2023 (incycledream)
- I fixed the fucked layout

#### - 7 March 2023 (incycledream)
- BIG SUR INSTALLER BOOTED SUCCESSFULLY.
- graphics doesn't work but I'll try to do something with my Terascale 2 GPU
<img src="https://files.catbox.moe/xyav88.jpg">

#### - 9 March 2023 (incycledream)
- Big Sur works like a charm with some things broken like audio and brightness
- from now, big sur updates will be posted here [satan/HackintoshNext-G570](https://codeberg.org/satan/HackintoshNext-G570) (codeberg)
- I drop active development, almost everything works normally
<img src="https://preview.redd.it/kyp56ad5ddma1.png?width=1080&crop=smart&auto=webp&v=enabled&s=de6422e70dc28de7fc0deec2448b14404f690f37">
</details>

