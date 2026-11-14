# GOHO-firmware

Versioned GOHO firmware images and release metadata. This repository contains firmware artifacts, not application source code.

## Current products

| Product | Current image | Previous image | Flash address | Status |
|---|---|---|---:|---|
| GOHO Bootloader (Duo) | `bootloaders/GOHO-BOOTLOADER-v1.0.4-TEST` (`.bin`, `.hex`) | `bootloaders/GOHO-BOOTLOADER-v1.0.3-TEST` (`.bin`, `.hex`) | `0x08000000` | TEST |
| GOHO Bootloader EX | `bootloaders/GOHO-BOOTLOADER-EX-v1.0.2-TEST` (`.bin`, `.hex`) | `bootloaders/GOHO-BOOTLOADER-EX-v1.0.1-TEST` (`.bin`, `.hex`) | `0x08000000` | TEST |
| GOHO Bennu | `bennu/GOHO-BENNU-v0.2.17-TEST` (`.bin`, `.hex`) | `bennu/GOHO-BENNU-v0.2.16-TEST` (`.bin`, `.hex`) | `0x08020000` | TEST |
| GOHO Bennu EX | `bennu/GOHO-BENNU-EX-v0.2.17-TEST` (`.bin`, `.hex`) | — | `0x08020000` | TEST |
| GOHO Pluto | `pluto/GOHO-PLUTO-v0.1.15-TEST` (`.bin`, `.hex`) | `pluto/GOHO-PLUTO-v0.1.14-TEST` (`.bin`, `.hex`) | `0x08020000` | TEST |
| GOHO Rhea | `rhea/GOHO-RHEA-v0.1.6-TEST` (`.bin`, `.hex`) | `rhea/GOHO-RHEA-v0.1.5-TEST` (`.bin`, `.hex`) | `0x08020000` | TEST |
| Plaits Plus | `plaits-plus/PLAITS-PLUS-v0.1.1-TEST` (`.bin`, `.hex`) | `plaits-plus/PLAITS-PLUS-v0.1.0-TEST` (`.bin`, `.hex`) | `0x08020000` | TEST |
| Rings Plus | `rings-plus/RINGS-PLUS-v0.1.1-TEST` (`.bin`, `.hex`) | `rings-plus/RINGS-PLUS-v0.1.0-TEST` (`.bin`, `.hex`) | `0x08020000` | TEST |
| Elements Plus | `elements-plus/ELEMENTS-PLUS-v0.1.1-TEST` (`.bin`, `.hex`) | `elements-plus/ELEMENTS-PLUS-v0.1.0-TEST` (`.bin`, `.hex`) | `0x08020000` | TEST |
| Peaks Plus | `peaks-plus/PEAKS-PLUS-v0.1.1-TEST` (`.bin`, `.hex`) | `peaks-plus/PEAKS-PLUS-v0.1.0-TEST` (`.bin`, `.hex`) | `0x08020000` | TEST |

## Bennu variants

Use GOHO Bennu with the current Duo bootloader for the normal product build; Freeze and Seed buttons are enabled, and runtime USB uses PB14/PB15. GOHO Bennu EX is a separate test application for the single-port GOHO Bootloader EX; its Freeze and Seed buttons are intentionally disabled. Both application images are linked at `0x08020000`.

For a virtual-disk application update, copy only the matching application `.bin` to the bootloader disk. Bootloader `.bin` files are separate programming images and must not be copied to the application update disk. All new images remain `TEST`; this archive does not claim hardware validation.

GOHO Bootloader uses PB14/PB15 for its MSC virtual-disk updater and leaves native OTG_FS uninitialized. GOHO Bootloader EX retains the single-port native OTG_FS behavior; PB14/PB15 is not initialized. Neither has a custom GOHO DFU interface.

The current Plus images use the product names in their USB identity strings. Their previous images remain unchanged. Exact artifact sizes, SHA-256 values, source revision, build target and toolchain are recorded in `firmware-manifest.json` and `SHA256SUMS.txt`. Older image files are removed from the current tree when a newer second version is published; earlier commits retain the history.
