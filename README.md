# GOHO-firmware

Versioned firmware images for GOHO products. The repository contains firmware artifacts and release metadata, not application source code.

## Current products

| Product | Current image | Previous image | Flash address | Status |
|---|---|---|---:|---|
| GOHO Bootloader | `bootloaders/GOHO-BOOTLOADER-v1.0.1-TEST` (`.bin`, `.hex`) | `bootloaders/GOHO-BOOTLOADER-v1.0.0-TEST` | `0x08000000` | TEST |
| GOHO Bennu | `bennu/GOHO-BENNU-v0.2.14-TEST` (`.bin`, `.hex`) | `bennu/GOHO-BENNU-v0.2.13-TEST` | `0x08020000` | TEST |
| GOHO Pluto | `pluto/GOHO-PLUTO-v0.1.13-TEST` (`.bin`, `.hex`) | `pluto/GOHO-PLUTO-v0.1.12-TEST` | `0x08020000` | TEST |
| GOHO Rhea | `rhea/GOHO-RHEA-v0.1.4-TEST` (`.bin`, `.hex`) | `rhea/GOHO-RHEA-v0.1.2-TEST` | `0x08020000` | TEST |
| Plaits Plus | `plaits-plus/PLAITS-PLUS-v0.1.1-TEST` (`.bin`, `.hex`) | `plaits-plus/PLAITS-PLUS-v0.1.0-TEST` | `0x08020000` | TEST |
| Rings Plus | `rings-plus/RINGS-PLUS-v0.1.1-TEST` (`.bin`, `.hex`) | `rings-plus/RINGS-PLUS-v0.1.0-TEST` | `0x08020000` | TEST |
| Elements Plus | `elements-plus/ELEMENTS-PLUS-v0.1.1-TEST` (`.bin`, `.hex`) | `elements-plus/ELEMENTS-PLUS-v0.1.0-TEST` | `0x08020000` | TEST |
| Peaks Plus | `peaks-plus/PEAKS-PLUS-v0.1.1-TEST` (`.bin`, `.hex`) | `peaks-plus/PEAKS-PLUS-v0.1.0-TEST` | `0x08020000` | TEST |

The current Plus v0.1.1 images were rebuilt from the local H743 Plus projects with matching Product, Configuration, Interface, and CDC startup names: Plaits Plus, Rings Plus, Elements Plus, and Peaks Plus. The v0.1.0 files are retained unchanged as the previous versions. No separate Bennu Plus source or image was present in the supplied build/archive files.

All GOHO images are marked TEST. Bootloader v1.0.1 is a software build candidate and has not been installed on hardware; its dual USB and custom DFU paths still need protocol and board testing. Bennu v0.2.14 and Pluto v0.1.13 are clean current-source H743 builds. Rhea v0.1.4 rebuilt byte-for-byte to its existing archive. A build or archive entry does not mean the exact image has been checked on a GOHO board. File sizes and SHA-256 values are in firmware-manifest.json and SHA256SUMS.txt. Older archived files remain available for rollback and traceability.
