# GOHO-firmware

Versioned GOHO firmware images and release metadata. This repository contains firmware artifacts, not application source code.

## Current products

| Product | Current image | Previous image | Flash address | Status |
|---|---|---|---:|---|
| GOHO bootloader (768 KiB, Duo) | `bootloaders/GOHO-BOOTLOADER-v1.0.8-TEST` (`.bin`, `.hex`) | `bootloaders/GOHO-BOOT-LOADER-512-v1.0.7-TEST` (`.bin`, `.hex`) | `0x08000000` | TEST |
| GOHO bootloaderex (768 KiB, EX) | `bootloaders/GOHO-BOOTLOADEREX-v1.0.5-TEST` (`.bin`, `.hex`) | `bootloaders/GOHO-BOOT-LOADER-EX-512-v1.0.4-TEST` (`.bin`, `.hex`) | `0x08000000` | TEST |
| GOHO Bennu | `bennu/GOHO-BENNU-v0.2.25-TEST` (`.bin`, `.hex`) | `bennu/GOHO-BENNU-v0.2.24-TEST` (`.bin`, `.hex`) | `0x08020000` | TEST |
| GOHO Bennu EX | `bennu/GOHO-BENNU-EX-v0.2.21-TEST` (`.bin`, `.hex`) | `bennu/GOHO-BENNU-EX-v0.2.20-TEST` (`.bin`, `.hex`) | `0x08020000` | TEST |
| GOHO Pluto | `pluto/GOHO-PLUTO-v0.1.20-TEST` (`.bin`, `.hex`) | `pluto/GOHO-PLUTO-v0.1.19-TEST` (`.bin`, `.hex`) | `0x08020000` | TEST |
| GOHO Rhea | `rhea/GOHO-RHEA-v0.1.11-TEST` (`.bin`, `.hex`) | `rhea/GOHO-RHEA-v0.1.10-TEST` (`.bin`, `.hex`) | `0x08020000` | TEST |
| GOHO Eris | `eris/GOHO-ERIS-v0.1.2-TEST` (`.bin`, `.hex`) | `eris/GOHO-ERIS-v0.1.1-TEST` (`.bin`, `.hex`) | `0x08020000` | TEST |
| Plaits Plus | `plaits-plus/PLAITS-PLUS-v0.1.1-TEST` (`.bin`, `.hex`) | `plaits-plus/PLAITS-PLUS-v0.1.0-TEST` (`.bin`, `.hex`) | `0x08020000` | TEST |
| Rings Plus | `rings-plus/RINGS-PLUS-v0.1.1-TEST` (`.bin`, `.hex`) | `rings-plus/RINGS-PLUS-v0.1.0-TEST` (`.bin`, `.hex`) | `0x08020000` | TEST |
| Elements Plus | `elements-plus/ELEMENTS-PLUS-v0.1.1-TEST` (`.bin`, `.hex`) | `elements-plus/ELEMENTS-PLUS-v0.1.0-TEST` (`.bin`, `.hex`) | `0x08020000` | TEST |
| Peaks Plus | `peaks-plus/PEAKS-PLUS-v0.1.1-TEST` (`.bin`, `.hex`) | `peaks-plus/PEAKS-PLUS-v0.1.0-TEST` (`.bin`, `.hex`) | `0x08020000` | TEST |

## Bennu variants

Use GOHO Bennu with `GOHO bootloader` (768 KiB) for the normal product build; Freeze and Seed buttons are enabled, and runtime USB uses PB14/PB15. GOHO Bennu EX is a separate test application for single-port `GOHO bootloaderex`; its Freeze and Seed buttons are intentionally disabled. Both application images are linked at `0x08020000`.

For a virtual-disk application update, copy only the matching application `.bin` to the bootloader disk. Bootloader `.bin` files are separate programming images and must not be copied to the application update disk. All new images remain `TEST`; this archive does not claim hardware validation.

The 768 KiB GOHO bootloader uses PB14/PB15 for its MSC virtual-disk updater and leaves native OTG_FS uninitialized. The 768 KiB GOHO bootloaderex uses native OTG_FS on USB1 and does not initialize PB14/PB15. The separately named 512 KiB builds keep the same USB-port split. GOHO Bennu U2 can request a one-shot handoff to the STM32 system-memory ROM DFU on native OTG_FS PA11/PA12; this is the ST-provided ROM, not a custom GOHO DFU class. Without an application, MIDI is unavailable; the virtual disk is entered with the Media startup button.

Standard GOHO Bennu, Pluto, Rhea and Eris applications use USB2/OTG_HS (PB14/PB15) for CDC, USB Audio and USB MIDI. They do not initialize USB1/OTG_FS (PA11/PA12), which remains available for STM32 ROM DFU. Bennu EX is the separate USB1-only application test variant. `GOHO bootloader` uses USB2 for MSC virtual-disk updates; `GOHO bootloaderex` uses USB1. The STM32 ROM DFU path remains separate. All images are `TEST` unless explicitly hardware-accepted. Application images link at `0x08020000`, and the updater protects the settings sector beginning at `0x081E0000`. Exact artifact sizes, SHA-256 values, source revision, build target and toolchain are recorded in `firmware-manifest.json` and `SHA256SUMS.txt`. The current downloadable tree retains only the latest and immediately previous image for each product; older images remain recoverable from Git history.


Bennu v0.2.21 was withdrawn from the current download set after the user reported missing USB Audio and non-working shared Freeze/Seed controls. v0.2.22 restores the USB2-only application route: USB1/OTG_FS is not initialized, and CDC, USB Audio and USB MIDI run on PB14/PB15. The exact image has passed a clean H743 build; board retest is still required. v0.2.20 is retained as the rollback image.

## GOHO-NEXT-016 TEST candidate

GOHO Eris v0.1.2 is the current Eris TEST image. It uses the independent GOHO Eris target and application address `0x08020000`; its standard USB route puts CDC, Audio and MIDI on USB2/PB14-PB15. H743 clean build passed, but hardware acceptance has not been run. Exact source revision, size and SHA-256 are in `firmware-manifest.json` and `SHA256SUMS.txt`.


## GOHO-NEXT-014 TEST images

Bennu v0.2.23, Bennu EX v0.2.20, Pluto v0.1.18 and Rhea v0.1.9 are clean STM32H743 builds with the shared Sector 7 user-data backend. The Host suite passed 46/46. These images remain TEST: no physical Flash migration, power-loss, cross-firmware persistence or USB/audio board verification was run. See `firmware-manifest.json` for exact source revision, build directory, size and SHA-256.

## GOHO-NEXT-015 TEST candidates

The current Bennu v0.2.24, Bennu EX v0.2.21, Pluto v0.1.19 and Rhea v0.1.10 images include the shared persistence/calibration software. All four are clean H743 builds at `0x08020000`. Host CTest 48/48 passed; physical Flash programming, power-cycle persistence, calibration accuracy and MSC-update preservation remain untested. They are TEST candidates, not hardware-accepted releases. SHA-256 and byte size are in `firmware-manifest.json` and `SHA256SUMS.txt`.


## GOHO Bennu v0.2.25 startup audio fix

Bennu v0.2.25 starts the processor-mode audio callback during normal boot, allowing the jack probe to run. With no input, the existing AUTO behavior switches to internal Synth after ten seconds. The H743 clean build passed; physical board retest is pending. v0.2.24 is retained as the rollback image.
