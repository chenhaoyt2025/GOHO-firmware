# GOHO-firmware

Versioned GOHO firmware images and release metadata. This repository contains firmware artifacts, not application source code.

## Current products

| Product | Current image | Previous image | Flash address | Status |
|---|---|---|---:|---|
| GOHO Bootloader (Duo) | `bootloaders/GOHO-BOOTLOADER-v1.0.6-TEST` (`.bin`, `.hex`) | `bootloaders/GOHO-BOOTLOADER-v1.0.5-TEST` (`.bin`, `.hex`) | `0x08000000` | TEST |
| GOHO Bootloader EX | `bootloaders/GOHO-BOOTLOADER-EX-v1.0.3-TEST` (`.bin`, `.hex`) | `bootloaders/GOHO-BOOTLOADER-EX-v1.0.2-TEST` (`.bin`, `.hex`) | `0x08000000` | TEST |
| GOHO Bennu | `bennu/GOHO-BENNU-v0.2.23-TEST` (`.bin`, `.hex`) | `bennu/GOHO-BENNU-v0.2.22-TEST` (`.bin`, `.hex`) | `0x08020000` | TEST |
| GOHO Bennu EX | `bennu/GOHO-BENNU-EX-v0.2.20-TEST` (`.bin`, `.hex`) | `bennu/GOHO-BENNU-EX-v0.2.19-TEST` (`.bin`, `.hex`) | `0x08020000` | TEST |
| GOHO Pluto | `pluto/GOHO-PLUTO-v0.1.18-TEST` (`.bin`, `.hex`) | `pluto/GOHO-PLUTO-v0.1.17-TEST` (`.bin`, `.hex`) | `0x08020000` | TEST |
| GOHO Rhea | `rhea/GOHO-RHEA-v0.1.9-TEST` (`.bin`, `.hex`) | `rhea/GOHO-RHEA-v0.1.8-TEST` (`.bin`, `.hex`) | `0x08020000` | TEST |
| Plaits Plus | `plaits-plus/PLAITS-PLUS-v0.1.1-TEST` (`.bin`, `.hex`) | `plaits-plus/PLAITS-PLUS-v0.1.0-TEST` (`.bin`, `.hex`) | `0x08020000` | TEST |
| Rings Plus | `rings-plus/RINGS-PLUS-v0.1.1-TEST` (`.bin`, `.hex`) | `rings-plus/RINGS-PLUS-v0.1.0-TEST` (`.bin`, `.hex`) | `0x08020000` | TEST |
| Elements Plus | `elements-plus/ELEMENTS-PLUS-v0.1.1-TEST` (`.bin`, `.hex`) | `elements-plus/ELEMENTS-PLUS-v0.1.0-TEST` (`.bin`, `.hex`) | `0x08020000` | TEST |
| Peaks Plus | `peaks-plus/PEAKS-PLUS-v0.1.1-TEST` (`.bin`, `.hex`) | `peaks-plus/PEAKS-PLUS-v0.1.0-TEST` (`.bin`, `.hex`) | `0x08020000` | TEST |

## Bennu variants

Use GOHO Bennu with the current Duo bootloader for the normal product build; Freeze and Seed buttons are enabled, and runtime USB uses PB14/PB15. GOHO Bennu EX is a separate test application for the single-port GOHO Bootloader EX; its Freeze and Seed buttons are intentionally disabled. Both application images are linked at `0x08020000`.

For a virtual-disk application update, copy only the matching application `.bin` to the bootloader disk. Bootloader `.bin` files are separate programming images and must not be copied to the application update disk. All new images remain `TEST`; this archive does not claim hardware validation.

GOHO Bootloader uses PB14/PB15 for its MSC virtual-disk updater and leaves native OTG_FS uninitialized during normal operation. GOHO Bennu U2 can request a one-shot handoff to the STM32 system-memory ROM DFU on native OTG_FS PA11/PA12; this is the ST-provided ROM, not a custom GOHO DFU class. The handoff requires both the Bennu application and the matching GOHO Bootloader. Without an application, MIDI is unavailable; the virtual disk is entered with the Media startup button. GOHO Bootloader EX retains the single-port native OTG_FS virtual-disk behavior; PB14/PB15 is not initialized.

Standard GOHO products use USB1/OTG_FS (PA11/PA12) for CDC and USB2/OTG_HS (PB14/PB15) for USB Audio/MIDI, except the Bennu v0.2.22 recovery candidate, which uses USB2 for all application USB services. Bennu EX is the USB1-only application test variant; USB2 is not initialized. The GOHO Bootloader Duo uses USB2 for MSC virtual-disk updates, while Bootloader EX uses USB1. The STM32 ROM DFU path remains separate. All NEXT-013 artifacts are `TEST` builds; no hardware validation is claimed. Application images link at `0x08020000`, and the updater protects the settings sector beginning at `0x081E0000`. The current Plus images use their product names in their USB identity strings. Exact artifact sizes, SHA-256 values, source revision, build target and toolchain are recorded in `firmware-manifest.json` and `SHA256SUMS.txt`. The current downloadable tree retains only the latest and immediately previous image for each product; older images remain recoverable from Git history.


Bennu v0.2.21 was withdrawn from the current download set after the user reported missing USB Audio and non-working shared Freeze/Seed controls. v0.2.22 restores the USB2-only application route: USB1/OTG_FS is not initialized, and CDC, USB Audio and USB MIDI run on PB14/PB15. The exact image has passed a clean H743 build; board retest is still required. v0.2.20 is retained as the rollback image.


## GOHO-NEXT-014 TEST images

Bennu v0.2.23, Bennu EX v0.2.20, Pluto v0.1.18 and Rhea v0.1.9 are clean STM32H743 builds with the shared Sector 7 user-data backend. The Host suite passed 46/46. These images remain TEST: no physical Flash migration, power-loss, cross-firmware persistence or USB/audio board verification was run. See `firmware-manifest.json` for exact source revision, build directory, size and SHA-256.
