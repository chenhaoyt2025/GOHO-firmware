# GOHO-firmware

Versioned firmware images for GOHO products. The repository contains firmware artifacts and release metadata, not application source code.

## Current products

| Product | Current image | Previous image | Flash address | Status |
|---|---|---|---:|---|
| GOHO Bootloader | `bootloaders/GOHO-BOOTLOADER-v1.0.3-TEST` (`.bin`, `.hex`) | `bootloaders/GOHO-BOOTLOADER-v1.0.2-TEST` (`.bin`, `.hex`) | `0x08000000` | TEST |
| GOHO Bootloader EX | `bootloaders/GOHO-BOOTLOADER-EX-v1.0.1-TEST` (`.bin`, `.hex`) | `bootloaders/GOHO-BOOTLOADER-EX-v1.0.0-TEST` (`.bin`, `.hex`) | `0x08000000` | TEST |
| GOHO Bennu | `bennu/GOHO-BENNU-v0.2.16-TEST` (`.bin`, `.hex`) | `bennu/GOHO-BENNU-v0.2.15-TEST` (`.bin`, `.hex`) | `0x08020000` | TEST |
| GOHO Pluto | `pluto/GOHO-PLUTO-v0.1.15-TEST` (`.bin`, `.hex`) | `pluto/GOHO-PLUTO-v0.1.14-TEST` (`.bin`, `.hex`) | `0x08020000` | TEST |
| GOHO Rhea | `rhea/GOHO-RHEA-v0.1.6-TEST` (`.bin`, `.hex`) | `rhea/GOHO-RHEA-v0.1.5-TEST` (`.bin`, `.hex`) | `0x08020000` | TEST |
| Plaits Plus | `plaits-plus/PLAITS-PLUS-v0.1.1-TEST` (`.bin`, `.hex`) | `plaits-plus/PLAITS-PLUS-v0.1.0-TEST` (`.bin`, `.hex`) | `0x08020000` | TEST |
| Rings Plus | `rings-plus/RINGS-PLUS-v0.1.1-TEST` (`.bin`, `.hex`) | `rings-plus/RINGS-PLUS-v0.1.0-TEST` (`.bin`, `.hex`) | `0x08020000` | TEST |
| Elements Plus | `elements-plus/ELEMENTS-PLUS-v0.1.1-TEST` (`.bin`, `.hex`) | `elements-plus/ELEMENTS-PLUS-v0.1.0-TEST` (`.bin`, `.hex`) | `0x08020000` | TEST |
| Peaks Plus | `peaks-plus/PEAKS-PLUS-v0.1.1-TEST` (`.bin`, `.hex`) | `peaks-plus/PEAKS-PLUS-v0.1.0-TEST` (`.bin`, `.hex`) | `0x08020000` | TEST |

GOHO Bootloader v1.0.3 is the user version for PB14/PB15; GOHO Bootloader EX v1.0.1 is the experimental native-USB version. Each has one previous build retained. The EX v1.0.0 rollback image predates the explicit EX USB product-name suffix. All bootloader images remain TEST; only their H743 software builds are confirmed.

The current Plus v0.1.1 images were rebuilt from the local H743 Plus projects with matching Product, Configuration, Interface, and CDC startup names: Plaits Plus, Rings Plus, Elements Plus, and Peaks Plus. The v0.1.0 files are retained unchanged as the previous versions. No separate Bennu Plus source or image was present in the supplied build/archive files.

All images are marked TEST. GOHO Bennu v0.2.16, Pluto v0.1.15 and Rhea v0.1.6 are clean STM32H743 builds using GOHO_USB_RUNTIME_HS_ONLY: runtime USB uses PB14/PB15, and Freeze/Seed button scanning on PA11/PA12 is enabled in the normal product builds. The exact images have not been tested on hardware. Their previous Bennu v0.2.15, Pluto v0.1.14 and Rhea v0.1.5 versions are dual-port candidates that also use PA11/PA12 for native OTG_FS, so use the current versions for the buttons-enabled configuration. USB and audio hardware behavior remains unverified. Build success does not establish hardware operation. The catalog keeps the current and immediately previous version for each product; older artifact files were removed from this tree and remain recoverable from Git history. Exact sizes and SHA-256 values are in firmware-manifest.json and SHA256SUMS.txt.
