# GOHO-firmware

Versioned firmware images for GOHO products. The repository contains firmware artifacts and release metadata, not application source code.

## Current products

| Product | Current image | Previous image | Flash address | Status |
|---|---|---|---:|---|
| GOHO Bootloader | `bootloaders/GOHO-BOOTLOADER-v1.0.0-TEST` (`.bin`, `.hex`) | — | `0x08000000` | TEST |
| GOHO Bennu | `bennu/GOHO-BENNU-v0.2.12-TEST` (`.bin`, `.hex`) | `bennu/GOHO-BENNU-v0.2.11-TEST` | `0x08020000` | TEST |
| GOHO Pluto | `pluto/GOHO-PLUTO-v0.1.11-TEST` (`.bin`, `.hex`) | `pluto/GOHO-PLUTO-v0.1.10-TEST` | `0x08020000` | TEST |
| Plaits Plus | `plaits-plus/PLAITS-PLUS-v0.1.0-TEST` (`.bin`, `.hex`) | — | `0x08020000` | TEST |
| Rings Plus | `rings-plus/RINGS-PLUS-v0.1.0-TEST` (`.bin`, `.hex`) | — | `0x08020000` | TEST |
| Elements Plus | `elements-plus/ELEMENTS-PLUS-v0.1.0-TEST` (`.bin`, `.hex`) | — | `0x08020000` | TEST |
| Peaks Plus | `peaks-plus/PEAKS-PLUS-v0.1.0-TEST` (`.bin`, `.hex`) | — | `0x08020000` | TEST |

The Plus images were copied from existing prebuilt artifacts. Their archive names and folders changed; their contents and embedded USB names did not. No separate Bennu Plus image was present in the supplied build/archive files.

All images are marked `TEST`. A build or archive entry does not mean the exact image has been checked on a GOHO board. File sizes and SHA-256 values are in `firmware-manifest.json` and `SHA256SUMS.txt`. Older application artifacts were removed from the current repository tree to keep the current and previous GOHO Bennu/Pluto versions easy to select. Earlier Git commits remain available as repository history.
