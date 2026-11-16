# GOHO-firmware

Versioned GOHO firmware images and release metadata. This repository contains firmware artifacts, not application source code.

## Current products

| Product | Current image | Previous image | Flash address | Status |
|---|---|---|---:|---|
| GOHO bootloader (768 KiB Duo) | `GOHO-BOOTLOADER-v1.1.0-TEST` (`.bin`, `.hex`) | `GOHO-BOOTLOADER-v1.0.9-TEST` (`.bin`, `.hex`) | `0x08000000` | TEST |
| GOHO bootloader EX (768 KiB) | `GOHO-BOOTLOADEREX-v1.0.7-TEST` (`.bin`, `.hex`) | `GOHO-BOOTLOADEREX-v1.0.6-TEST` (`.bin`, `.hex`) | `0x08000000` | TEST |
| GOHO 512 bootloader | `GOHO-BOOT-LOADER-512-v1.0.8-TEST` (`.bin`, `.hex`) | `GOHO-BOOT-LOADER-512-v1.0.7-TEST` (`.bin`, `.hex`) | `0x08000000` | TEST |
| GOHO 512 EX bootloader | `GOHO-BOOT-LOADER-EX-512-v1.0.6-TEST` (`.bin`, `.hex`) | `GOHO-BOOT-LOADER-EX-512-v1.0.5-TEST` (`.bin`, `.hex`) | `0x08000000` | TEST |
| GOHO Bennu | `GOHO-BENNU-v0.3.3-TEST` (`.bin`, `.hex`) | `GOHO-BENNU-v0.3.2-TEST` (`.bin`, `.hex`) | `0x08020000` | TEST |
| GOHO Bennu EX | `GOHO-BENNU-EX-v0.3.3-TEST` (`.bin`, `.hex`) | `GOHO-BENNU-EX-v0.3.2-TEST` (`.bin`, `.hex`) | `0x08020000` | TEST |
| GOHO Pluto | `GOHO-PLUTO-v0.2.3-TEST` (`.bin`, `.hex`) | `GOHO-PLUTO-v0.2.2-TEST` (`.bin`, `.hex`) | `0x08020000` | TEST |
| GOHO Rhea | `GOHO-RHEA-v0.2.3-TEST` (`.bin`, `.hex`) | `GOHO-RHEA-v0.2.2-TEST` (`.bin`, `.hex`) | `0x08020000` | TEST |
| GOHO Eris | `GOHO-ERIS-v0.1.7-TEST` (`.bin`, `.hex`) | `GOHO-ERIS-v0.1.6-TEST` (`.bin`, `.hex`) | `0x08020000` | TEST |
| Plaits Plus | `PLAITS-PLUS-v0.1.1-TEST` (`.bin`, `.hex`) | `PLAITS-PLUS-v0.1.0-TEST` (`.bin`, `.hex`) | `0x08020000` | TEST |
| Rings Plus | `RINGS-PLUS-v0.1.1-TEST` (`.bin`, `.hex`) | `RINGS-PLUS-v0.1.0-TEST` (`.bin`, `.hex`) | `0x08020000` | TEST |
| Elements Plus | `ELEMENTS-PLUS-v0.1.1-TEST` (`.bin`, `.hex`) | `ELEMENTS-PLUS-v0.1.0-TEST` (`.bin`, `.hex`) | `0x08020000` | TEST |
| Peaks Plus | `PEAKS-PLUS-v0.1.1-TEST` (`.bin`, `.hex`) | `PEAKS-PLUS-v0.1.0-TEST` (`.bin`, `.hex`) | `0x08020000` | TEST |

## Bennu variants

Use GOHO Bennu with `GOHO bootloader` (768 KiB) for the normal product build; Freeze and Seed buttons are enabled. GOHO Bennu EX is a separate test application with its established Freeze/Seed policy. Both application images link at `0x08020000`. Normal Bennu uses USB2/PB14-PB15 for CDC, Audio and MIDI and does not initialize USB1; Bennu EX uses USB1/PA11-PA12 for all three classes and does not initialize USB2.

For a virtual-disk application update, copy only the matching application `.bin` to the bootloader disk. Bootloader `.bin` files are separate programming images and must not be copied to the application update disk. All new images remain `TEST`; this archive does not claim hardware validation.

The 768 KiB GOHO bootloader uses PB14/PB15 for its MSC virtual-disk updater and leaves native OTG_FS uninitialized. The 768 KiB GOHO bootloaderex uses native OTG_FS on USB1 and does not initialize PB14/PB15. The separately named 512 KiB builds keep the same USB-port split. GOHO Bennu U2 can request a one-shot handoff to the STM32 system-memory ROM DFU on native OTG_FS PA11/PA12; this is the ST-provided ROM, not a custom GOHO DFU class. Without an application, MIDI is unavailable; the virtual disk is entered with the Media startup button.

Standard GOHO Bennu, Pluto, Rhea and Eris applications use USB2/OTG_HS Full-Speed PHY (PB14/PB15) for CDC, Audio and MIDI; USB1/OTG_FS (PA11/PA12) is not initialized. Bennu EX is the exception: all runtime classes use USB1 and USB2 is not initialized. The NEXT-019 initial split-routed images were superseded after the USB assignment error was found. Physical host behavior is not implied by a build. `GOHO bootloader` uses USB2 for MSC virtual-disk updates; `GOHO bootloaderex` uses USB1. The STM32 ROM DFU path remains separate. All images are `TEST` unless explicitly hardware-accepted. Application images link at `0x08020000`, and the updater protects the settings sector beginning at `0x081E0000`. Exact artifact sizes, SHA-256 values, source revision, build target and toolchain are recorded in `firmware-manifest.json` and `SHA256SUMS.txt`. The current downloadable tree retains only the latest and immediately previous image for each product; older images remain recoverable from Git history.


Bennu v0.2.21 was withdrawn from the current download set after the user reported missing USB Audio and non-working shared Freeze/Seed controls. v0.2.22 restores the USB2-only application route: USB1/OTG_FS is not initialized, and CDC, USB Audio and USB MIDI run on PB14/PB15. The exact image has passed a clean H743 build; board retest is still required. v0.2.20 is retained as the rollback image.

## GOHO-NEXT-016 Eris candidate (historical)

GOHO Eris v0.1.2 was an early Eris TEST candidate. It was superseded by v0.1.3 and the NEXT-018 v0.1.4 candidate. The current application USB assignment is USB1 CDC plus USB2 Audio/MIDI; older candidates may use earlier routing. See `firmware-manifest.json` for artifact-specific build records.


## GOHO-NEXT-014 TEST images

Bennu v0.2.23, Bennu EX v0.2.20, Pluto v0.1.18 and Rhea v0.1.9 are clean STM32H743 builds with the shared Sector 7 user-data backend. The Host suite passed 46/46. These images remain TEST: no physical Flash migration, power-loss, cross-firmware persistence or USB/audio board verification was run. See `firmware-manifest.json` for exact source revision, build directory, size and SHA-256.

## GOHO-NEXT-015 TEST candidates

The current Bennu v0.2.24, Bennu EX v0.2.21, Pluto v0.1.19 and Rhea v0.1.10 images include the shared persistence/calibration software. All four are clean H743 builds at `0x08020000`. Host CTest 48/48 passed; physical Flash programming, power-cycle persistence, calibration accuracy and MSC-update preservation remain untested. They are TEST candidates, not hardware-accepted releases. SHA-256 and byte size are in `firmware-manifest.json` and `SHA256SUMS.txt`.


## GOHO-NEXT-017 TEST candidates

The current NEXT-017 candidates are Bennu v0.2.26, Bennu EX v0.2.22, Pluto
v0.1.21, Rhea v0.1.12 and Eris v0.1.3. Release Host CTest passed 51/51;
independent clean H743 builds passed for all five targets. The common physical
K1-K5/MUX1-MUX7 map and CDC monitor updates are included. Firmware files remain
`TEST`: USB, audio, controls, LEDs, CV/Gate, persistence and bootloader behavior
were not re-tested on a physical board. The current download tree retains only
the latest two versions in each affected product series.

## GOHO Bennu v0.2.25 startup audio fix

Bennu v0.2.25 starts the processor-mode audio callback during normal boot, allowing the jack probe to run. With no input, the existing AUTO behavior switches to internal Synth after ten seconds. The H743 clean build passed; physical board retest is pending. v0.2.24 is retained as the rollback image.


## GOHO-NEXT-018 TEST candidates

NEXT-018 builds Bennu v0.3.0, Bennu EX v0.3.0, Pluto v0.2.0, Rhea v0.2.0,
Eris v0.1.4, GOHO bootloader Duo v1.0.9, bootloaderex v1.0.6, and EX512
v1.0.5. Application USB is split as USB1 CDC and USB2 Audio/MIDI. Firmware
implements MIDI Channel 16 CC115-119 version queries and version-derived WS2812B
startup digits. Host tests and H743 clean builds passed; exact-image physical
USB, audio, MIDI, LED and bootloader update tests were not run. All images remain
TEST. SHA-256, byte sizes, build targets and source working-tree boundary are in
`firmware-manifest.json` and `SHA256SUMS.txt`.


## GOHO-NEXT-019 fixed identity and MIDI device info

NEXT-019 implements fixed Bootloader identity and MIDI Device Info Protocol v2. The first app binaries were mistakenly routed as USB1 CDC + USB2 Audio/MIDI; follow-up corrected images are now the current TEST downloads above. Normal Bennu/Pluto/Rhea/Eris use USB2 for CDC/Audio/MIDI; Bennu EX uses USB1 for all three. Corrected clean H743 builds and Host CTest 53/53 passed. Physical board programming, MIDI host decoding, USB/audio operation and MSC update remain untested. Do not use the earlier NEXT-019 split images to verify current USB routing; their previous versions are retained only as rollback/history candidates.

The immediately previous image listed for each GOHO product is retained as a rollback. Those older images predate NEXT-019: older Bootloaders do not contain the fixed identity record/README line, and older applications do not implement MIDI Device Info Protocol v2. Use the current NEXT-019 image when testing the new identity protocol.


## GOHO-NEXT-019 runtime version re-query builds (2026-11-17)

Bennu v0.3.3, Bennu EX v0.3.3, Pluto v0.2.3, Rhea v0.2.3 and Eris v0.1.7 include the runtime USB MIDI version re-query fix. Each Channel 16 CC119=1 request now queues its own ordered Bootloader and APP records, including when a previous response is in progress. Host CTest passed 53/53 and all five clean STM32H743 application builds passed. Images remain TEST; no physical board/host MIDI test was run. Exact hashes and sizes are in `firmware-manifest.json` and `SHA256SUMS.txt`.
