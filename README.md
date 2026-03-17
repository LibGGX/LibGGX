## LibGGX
A suite of Xbox 360 NAND utilities written in Rust, tied together by Mandeville.

## Who did what, and what can we license?
The vast majority of the code in this project is not original. 70+% of the code is ported from existing projects and utilities. The most apparent example is Keychain, in which i didnt write a single line of original code, just ported it to Rust from XeCrypt and Xbox-360-Crypto.

As for licensing, All but two projects are unlicensed, meaning by law i have no permission to have made this. Unfortunately for anyone who cares, i don't. I will leave the licensed code under the licenses they were released under, but everything else is unlicensed.

For all we know, tools like xeBuild and JungleFlasher could be entirely made of copywrited and stolen code, but we would have no idea because its completely closed. Infact, tools that ARE open source, like in the Wii Homebrew community, still have stolen or decompiled code from copywrited Nintendo software.

Furthermore, this entire scene violates any and every EULA that Microsoft has ever put out. The concept of licensing a project like this is absurd. it LITERALLY has the 1BL keys hardcoded which could get it Digital Millenium'd at any point in time. If this project goes down, email me at `exposuremg@protonmail.com` and i will ALWAYS be willing to send the source.

I am a big advocate for Free and Open Source Software; The reason i undertook this project in the first place is because xeBuild is closed source and not easy to decompile, and i would like a future where J-Runner with Extras runs on Linux. 

/* Maybe remove, its provocative */
Do not get me wrong, though, if you think i "stole" your code, you are just a r\*t\*rd. Do NOT ask me to take it down, i will not comply. I will ALWAYS send out source code for free. You will have to jail me to stop me from distributing this.

## Project Structure

### Wenlock
Wenlock is the official frontend CLI for LibGGX. It is the least required part of this project, and can be safely subsituted with just about any CLI or GUI.

### Mandeville
Mandeville is a wrapper around the other five LibGGX components. It forms full commands out of loose functions, and exposes them either via Cargo or FFI. Wenlock directly interfaces Mandeville.

### Bilateral
Bilateral is the core 2-Stage patching engine. It reads an input of bytes and applies patches in one of two ways:
1. Traditional XeBuild Binaries - Hardcoded offsets
2. GGX Signature Patches (GSP1/GSP2) - Pattern matched

### Assembler
Assembler provides the vital Xbox 360 NAND building, injection and extraction. Heavily based on work by GliGli, 15432 and DrSchottky, This component could easily be substituted with one of many NAND builders already available.

### Keychain
Almost entirely ported from XeCrypt by jogolden and Xbox-360-Crypto by GoobyCorp. This library provides all the core encryption and decryption functions.

### STFS-Rs
STFS-Rs was designed as a multi-platform replacement for WxPirs, but it has been extended to support CON and LIVE in addition to PIRS. This component provides the CF and CG extraction from SU containers, but can also be used independant of LibGGX for any STFS package

### LZX-XP
This package provides LZX and XPress compression and decompression algorithms, heavily used by the Xbox 360 FlashFS. This was designed as the only available implementations of LZX and Xpress were usually Windows-only, unmaintained, and written in C. As you can see, i am a fan of Rust.
- Nearly 100% Ported from `wimlib` and `ms-compress`
- LGPL v3 Licensed


### Full Project Credits:
- Wenlock
ExposureMG

- Mandeville
ExposureMG

- Bilateral
GoobyCorp (Xbox-360-Crypto)
RGLoader Team - TODO add names (RGBuild Patches & Patcher)
XDKBuild Team - TODO add names (XDKBuild Patches)
InvoxiPlayGames (UsbDSec Patch)
ExposureMG (LibGGX)

- Assembler
GliGli (tools/imgbuild.py)
15432 (RGH3)
DrSchottky (RGH2to3)
ExposureMG (LibGGX)

- Keychain
jogolden (XeCrypt)
GoobyCorp (Xbox-360-Crypto)

- STFS-Rs
Anthony (anthony's world) - WxPirs Author
Free60 Wiki Contributors
ExposureMG

- LZX-XP
Carl Thijssen (wimlib.net)
Eric Biggers (wimlib.net)
Jeffrey Bush (CoderForLife.com)
ExposureMG