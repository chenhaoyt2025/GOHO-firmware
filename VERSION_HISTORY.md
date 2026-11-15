# GOHO Firmware Version History

Only the current and immediately previous images for each GOHO product and bootloader variant (including GOHO Bootloader EX) are kept in the latest repository tree. Older releases remain recoverable from Git commit history.

## 2026-11-13 — GOHO Rhea first firmware

| Product | Version | Status | Artifacts | Notes |
|---|---:|---|---|---|
| GOHO Rhea | v0.1.0 | TEST | `rhea/GOHO-RHEA-v0.1.0-TEST.bin`, `.hex` | First GOHO Rhea target, built from `goho_modules/rhea/makefile` using the official fixed-source Rings DSP and GOHO H743 audio/control/USB/LED services. Host tests and H743 target build passed; no physical-board test was run. |

## 2026-11-13 — GOHO Bennu and GOHO Pluto naming/build outputs

| Product | Version | Status | Artifacts | Notes |
|---|---:|---|---|---|
| GOHO Bennu | v0.2.12 | TEST | `bennu/GOHO-BENNU-v0.2.12-TEST.bin`, `.hex` | Fresh STM32H743 build from `goho_modules/bennu/makefile`; output target and directory use the approved name. USB/CDC product identity is `GOHO Bennu`. |
| GOHO Bennu | v0.2.11 | TEST | `bennu/GOHO-BENNU-v0.2.11-TEST.bin`, `.hex` | Previous archived GOHO Bennu image; bytes preserved. |
| GOHO Pluto | v0.1.11 | TEST | `pluto/GOHO-PLUTO-v0.1.11-TEST.bin`, `.hex` | Fresh STM32H743 build from `goho_modules/pluto/makefile`; output target and directory use the approved name. USB/CDC product identity is `GOHO Pluto`. |
| GOHO Pluto | v0.1.10 | TEST | `pluto/GOHO-PLUTO-v0.1.10-TEST.bin`, `.hex` | Previous archived GOHO Pluto image; bytes preserved. |
| GOHO Bootloader | v1.0.0 | TEST | `bootloaders/GOHO-BOOTLOADER-v1.0.0-TEST.bin`, `.hex` | Existing artifact retained unchanged; no new bootloader build was made for this rename. |

## Plus images

| Product | Version | Status | Artifacts | Notes |
|---|---:|---|---|---|
| Plaits Plus | v0.1.0 | TEST | `plaits-plus/PLAITS-PLUS-v0.1.0-TEST.bin`, `.hex` | Existing prebuilt image; only archive path/name changed. |
| Rings Plus | v0.1.0 | TEST | `rings-plus/RINGS-PLUS-v0.1.0-TEST.bin`, `.hex` | Existing prebuilt image; only archive path/name changed. |
| Elements Plus | v0.1.0 | TEST | `elements-plus/ELEMENTS-PLUS-v0.1.0-TEST.bin`, `.hex` | Existing prebuilt image; only archive path/name changed. |
| Peaks Plus | v0.1.0 | TEST | `peaks-plus/PEAKS-PLUS-v0.1.0-TEST.bin`, `.hex` | Existing prebuilt image; only archive path/name changed. |

The prebuilt Plus binaries retain their original embedded USB descriptors. No separate Bennu Plus image was present to archive.

All newly built GOHO images use GNU Arm Embedded Toolchain 10.3.1 and link their application vectors at `0x08020000`. Exact build directories, sizes, and hashes are recorded in `firmware-manifest.json` and `SHA256SUMS.txt`. The fresh images remain `TEST` until the user checks these exact images on hardware.


## 2026-11-13 — Plus device identity rebuilds

| Product | Version | Status | Artifacts | Notes |
|---|---:|---|---|---|
| Plaits Plus | v0.1.1 | TEST | `plaits-plus/PLAITS-PLUS-v0.1.1-TEST.bin`, `.hex` | Rebuilt H743 image; USB product/configuration/interface and CDC startup label use `Plaits Plus`. |
| Rings Plus | v0.1.1 | TEST | `rings-plus/RINGS-PLUS-v0.1.1-TEST.bin`, `.hex` | Rebuilt H743 image; USB product/configuration/interface and CDC startup label use `Rings Plus`. |
| Elements Plus | v0.1.1 | TEST | `elements-plus/ELEMENTS-PLUS-v0.1.1-TEST.bin`, `.hex` | Rebuilt H743 image; USB product/configuration/interface and CDC startup label use `Elements Plus`. |
| Peaks Plus | v0.1.1 | TEST | `peaks-plus/PEAKS-PLUS-v0.1.1-TEST.bin`, `.hex` | Rebuilt H743 image; USB product/configuration/interface and CDC startup label use `Peaks Plus`. |

The preceding v0.1.0 images remain as rollback versions; their bytes and embedded USB names are unchanged. The Plus projects do not add a USB MIDI class in this identity-only change. Exact sizes and SHA-256 values are in `firmware-manifest.json` and `SHA256SUMS.txt`. All v0.1.1 builds are untested on hardware and remain `TEST`.


## 2026-11-14 — GOHO Bennu and GOHO Pluto Pitch-control regression builds

| Product | Version | Status | Artifacts | Notes |
|---|---:|---|---|---|
| GOHO Bennu | v0.2.13 | TEST | `bennu/GOHO-BENNU-v0.2.13-TEST.bin`, `.hex` | Clean STM32H743 regression build after the shared Pitch Bend/panel-control arbiter change; no physical-board test was run. |
| GOHO Pluto | v0.1.12 | TEST | `pluto/GOHO-PLUTO-v0.1.12-TEST.bin`, `.hex` | Clean STM32H743 regression build after the shared Pitch Bend/panel-control arbiter change; no physical-board test was run. |

The current archive tree keeps the new images and their immediately previous versions. Exact build directories, sizes, and SHA-256 values are recorded in `firmware-manifest.json` and `SHA256SUMS.txt`; superseded files remain recoverable in Git history.


## 2026-11-14 — GOHO Rhea Reverb control correction

| Product | Version | Status | Artifacts | Notes |
|---|---:|---|---|---|
| GOHO Rhea | v0.1.2 | TEST | `rhea/GOHO-RHEA-v0.1.2-TEST.bin`, `.hex` | Clean H743 rebuild. M3 Reverb and M1 Feedback paths are separated per Rings Plus; Host CTest 40/40 passed. Hardware test not run. |
| GOHO Rhea | v0.1.1 | TEST | `rhea/GOHO-RHEA-v0.1.1-TEST.bin`, `.hex` | Earlier H743 build; removed from the current tree when the archive was trimmed. Hardware test not run. |

The earlier Rhea v0.1.0 files were removed from the current archive tree; they remain recoverable from Git history.


## 2026-11-14 — GOHO Rhea Rings Plus signal-path correction

| Product | Version | Status | Artifacts | Notes |
|---|---:|---|---|---|
| GOHO Rhea | v0.1.4 | TEST | `rhea/GOHO-RHEA-v0.1.4-TEST.bin`, `.hex` | Matches Rings Plus external-exciter RMS threshold, disconnected-CV neutralization, and 0–60 semitone Pitch range. Rhea Host tests 2/2 and clean H743 build passed; hardware audio test not run. |
| GOHO Rhea | v0.1.2 | TEST | `rhea/GOHO-RHEA-v0.1.2-TEST.bin`, `.hex` | Previous published image retained for rollback. |

The unpublished v0.1.3 candidate was superseded before publication. Rhea v0.1.1 was removed from the current tree; earlier published bytes remain in Git history.


## 2026-11-14 — GOHO-NEXT-012 clean H743 test candidates

| Product | Version | Status | Artifacts | Notes |
|---|---:|---|---|---|
| GOHO Bootloader | v1.0.1 | TEST | bootloaders/GOHO-BOOTLOADER-v1.0.1-TEST.bin, .hex | Clean H743 build with dual USB MSC and custom DFU candidate paths; no physical protocol/update test has run. Preserve v1.0.0 as rollback. |
| GOHO Bennu | v0.2.14 | TEST | bennu/GOHO-BENNU-v0.2.14-TEST.bin, .hex | Clean current-source H743 build. Existing v0.2.13 output differed from this clean build; new version is explicit and no hardware test was run. |
| GOHO Pluto | v0.1.13 | TEST | pluto/GOHO-PLUTO-v0.1.13-TEST.bin, .hex | Clean current-source H743 build. Existing v0.1.12 output differed from this clean build; new version is explicit and no hardware test was run. |
| GOHO Rhea | v0.1.4 | TEST | Existing archive reused | Clean current-source rebuild matched the existing v0.1.4 BIN and HEX exactly; no new version was created. |

All artifacts remain TEST. The firmware archive does not imply successful dual-port enumeration, DFU transfer, CDC/MIDI/Audio host behavior, or hardware operation.

## 2026-11-14 — GOHO-NEXT-012 dual USB application candidates

| Product | Version | Status | Artifacts | Notes |
|---|---:|---|---|---|
| GOHO Bennu | v0.2.15 | TEST | `bennu/GOHO-BENNU-v0.2.15-TEST.bin`, `.hex` | Clean STM32H743 build with independent FS/HS CDC, Audio and MIDI class state plus service-level port arbitration. Host suite 44/44 passed; physical USB tests not run. |
| GOHO Pluto | v0.1.14 | TEST | `pluto/GOHO-PLUTO-v0.1.14-TEST.bin`, `.hex` | Same GOHO dual USB application integration, built from Pluto GOHO target. Host suite 44/44 passed; physical USB tests not run. |
| GOHO Rhea | v0.1.5 | TEST | `rhea/GOHO-RHEA-v0.1.5-TEST.bin`, `.hex` | Same GOHO dual USB application integration, built from Rhea GOHO target. Host suite 44/44 passed; physical USB tests not run. |

All three application images link at `0x08020000` and use GNU Arm Embedded Toolchain 10.3.1. The bundled ST USB Middleware class copies were modified with explicit authorization to isolate per-device endpoint and MIDI state. Firmware artifacts remain TEST pending physical board/host verification. The repository tree retains only the current and immediately previous version of each product; removed older artifacts remain in Git history. Exact file sizes and SHA-256 values are in `firmware-manifest.json` and `SHA256SUMS.txt`.


## 2026-11-14 — GOHO Bootloader and GOHO Bootloader EX split

| Product | Version | Status | Artifacts | Notes |
|---|---:|---|---|---|
| GOHO Bootloader | v1.0.3 | TEST | `bootloaders/GOHO-BOOTLOADER-v1.0.3-TEST.bin`, `.hex` | Current user version; MSC virtual disk on PB14/PB15 only. Native OTG_FS is not initialized. No custom DFU. Build passed; physical update behavior not verified. |
| GOHO Bootloader | v1.0.2 | TEST | `bootloaders/GOHO-BOOTLOADER-v1.0.2-TEST.bin`, `.hex` | Previous dual-port MSC-only build; retained as rollback. |
| GOHO Bootloader EX | v1.0.1 | TEST | `bootloaders/GOHO-BOOTLOADER-EX-v1.0.1-TEST.bin`, `.hex` | Current experimental version; MSC virtual disk on native OTG_FS only. PB14/PB15 is not initialized. No custom DFU. Build passed; physical update behavior not verified. |
| GOHO Bootloader EX | v1.0.0 | TEST | `bootloaders/GOHO-BOOTLOADER-EX-v1.0.0-TEST.bin`, `.hex` | Previous single-port OTG_FS build before explicit EX naming; retained as rollback. |

The former generic bootloader v1.0.0/v1.0.1 artifacts were removed from the current tree because they lacked variant identity. Existing records remain in Git history. Exact artifact sizes and SHA-256 values are in `firmware-manifest.json` and `SHA256SUMS.txt`.


## 2026-11-14 — GOHO Bennu buttons-enabled runtime USB build

| Product | Version | Status | Artifacts | Notes |
|---|---:|---|---|---|
| GOHO Bennu | v0.2.16 | TEST | `bennu/GOHO-BENNU-v0.2.16-TEST.bin`, `.hex` | Fresh clean STM32H743 build from the normal Bennu target. It defines `GOHO_USB_RUNTIME_HS_ONLY`, uses PB14/PB15 for runtime USB, and enables the normal Freeze/Seed button path on PA11/PA12. Hardware button, USB and audio behavior for this image have not been tested. Retain v0.2.15 as the previous image. |

Bennu v0.2.14 was removed from the current tree to keep only v0.2.16 and its immediately previous v0.2.15; older files remain in Git history.


## 2026-11-14 — GOHO Pluto and GOHO Rhea buttons-enabled runtime USB builds

| Product | Version | Status | Artifacts | Notes |
|---|---:|---|---|---|
| GOHO Pluto | v0.1.15 | TEST | `pluto/GOHO-PLUTO-v0.1.15-TEST.bin`, `.hex` | Fresh clean H743 build using HS-only runtime USB; normal shared Freeze/Seed button scanning remains enabled. Hardware tests not run. |
| GOHO Pluto | v0.1.14 | TEST | `pluto/GOHO-PLUTO-v0.1.14-TEST.bin`, `.hex` | Previous dual-port build retained for rollback; native OTG_FS shares PA11/PA12 with Freeze/Seed. |
| GOHO Rhea | v0.1.6 | TEST | `rhea/GOHO-RHEA-v0.1.6-TEST.bin`, `.hex` | Fresh clean H743 build using HS-only runtime USB; normal shared Freeze/Seed button scanning remains enabled. Hardware tests not run. |
| GOHO Rhea | v0.1.5 | TEST | `rhea/GOHO-RHEA-v0.1.5-TEST.bin`, `.hex` | Previous dual-port build retained for rollback; native OTG_FS shares PA11/PA12 with Freeze/Seed. |

Pluto v0.1.13 and Rhea v0.1.4 were removed from the current tree so each product keeps only its newest two versions; older files remain in Git history.

## 2026-11-14 — GOHO Bootloader and Bennu button-policy builds

| Product | Version | Status | Artifacts | Notes |
|---|---:|---|---|---|
| GOHO Bootloader (Duo) | v1.0.4 | TEST | `bootloaders/GOHO-BOOTLOADER-v1.0.4-TEST.bin`, `.hex` | Clean H743 build; MSC updater on PB14/PB15. Physical behavior not tested. |
| GOHO Bootloader | v1.0.3 | TEST | `bootloaders/GOHO-BOOTLOADER-v1.0.3-TEST.bin`, `.hex` | Previous user version retained for rollback. |
| GOHO Bootloader EX | v1.0.2 | TEST | `bootloaders/GOHO-BOOTLOADER-EX-v1.0.2-TEST.bin`, `.hex` | Clean H743 single-port native-USB build; physical behavior not tested. |
| GOHO Bootloader EX | v1.0.1 | TEST | `bootloaders/GOHO-BOOTLOADER-EX-v1.0.1-TEST.bin`, `.hex` | Previous EX version retained for rollback. |
| GOHO Bennu | v0.2.17 | TEST | `bennu/GOHO-BENNU-v0.2.17-TEST.bin`, `.hex` | Clean H743 normal product build. Freeze/Seed buttons enabled; runtime USB uses PB14/PB15. Hardware behavior not tested. |
| GOHO Bennu | v0.2.16 | TEST | `bennu/GOHO-BENNU-v0.2.16-TEST.bin`, `.hex` | Previous normal Bennu build retained for rollback. |
| GOHO Bennu EX | v0.2.17 | TEST | `bennu/GOHO-BENNU-EX-v0.2.17-TEST.bin`, `.hex` | Separate EX test application; Freeze/Seed buttons intentionally disabled for GOHO Bootloader EX testing. Runtime USB uses PB14/PB15. Hardware behavior not tested. |

The four current images were built clean from the GOHO source project using GNU Arm Embedded Toolchain 10.3.1. Both Bennu application vector tables link at `0x08020000`. No hardware tests were run for these exact builds. Bennu v0.2.15 and bootloader v1.0.2 / EX v1.0.0 were removed from the current tree to retain the latest two images in each established series; older artifacts remain in Git history.


## 2026-11-15 — GOHO Bennu U2 native STM32 ROM DFU entry

| Product | Version | Status | Artifacts | Notes |
|---|---:|---|---|---|
| GOHO Bootloader (Duo) | v1.0.5 | TEST | `bootloaders/GOHO-BOOTLOADER-v1.0.5-TEST.bin`, `.hex` | Consumes the one-shot U2 DFU request before GOHO peripheral initialization and branches to the STM32H743 system-memory bootloader at `0x1FF09800`; normal MSC remains on PB14/PB15. Clean H743 build; physical handoff and DFU transfer not tested. |
| GOHO Bootloader (Duo) | v1.0.4 | TEST | `bootloaders/GOHO-BOOTLOADER-v1.0.4-TEST.bin`, `.hex` | Previous published version retained for rollback. |
| GOHO Bennu | v0.2.18 | TEST | `bennu/GOHO-BENNU-v0.2.18-TEST.bin`, `.hex` | U2 on PD12 requests native STM32 ROM DFU; U1 and MIDI System Reset retain virtual-disk entry. Clean H743 build; physical button, ROM handoff, MIDI and disk behavior not tested. |
| GOHO Bennu | v0.2.17 | TEST | `bennu/GOHO-BENNU-v0.2.17-TEST.bin`, `.hex` | Previous published version retained for rollback. |

Native STM32 ROM DFU uses the PA11/PA12 OTG_FS port. All new artifacts remain `TEST`; exact file sizes and SHA-256 values are in `firmware-manifest.json` and `SHA256SUMS.txt`. Source revision: `499098d5863c0ee8564df78c5f2c9370775459b6` plus uncommitted GOHO U2 ROM DFU changes.


## 2026-11-15 — USB MIDI product-name descriptor correction

| Product | Version | Status | Artifacts | Notes |
|---|---:|---|---|---|
| GOHO Bennu | v0.2.19 | TEST | `bennu/GOHO-BENNU-v0.2.19-TEST.bin`, `.hex` | Clean H743 build; retains the `GOHO Bennu` USB product identity and sets USB-MIDI 1.0 unused interface/jack string indices to zero. Host descriptor test passed; physical host display not tested. |
| GOHO Bennu EX | v0.2.18 | TEST | `bennu/GOHO-BENNU-EX-v0.2.18-TEST.bin`, `.hex` | Clean H743 EX build; USB product identity is `GOHO Bennu EX`. Host descriptor test passed; physical host display not tested. |
| GOHO Pluto | v0.1.16 | TEST | `pluto/GOHO-PLUTO-v0.1.16-TEST.bin`, `.hex` | Clean H743 build; USB product identity is `GOHO Pluto`. Host descriptor test passed; physical host display not tested. |
| GOHO Rhea | v0.1.7 | TEST | `rhea/GOHO-RHEA-v0.1.7-TEST.bin`, `.hex` | Clean H743 build; USB product identity is `GOHO Rhea`. Host descriptor test passed; physical host display not tested. |

The latest two versions are retained for each affected series. Bennu normal v0.2.17, Pluto v0.1.14 and Rhea v0.1.5 were removed from the current tree; older history remains in Git. Exact sizes and SHA-256 values are listed in `firmware-manifest.json` and `SHA256SUMS.txt`. Source revision: `499098d5863c0ee8564df78c5f2c9370775459b6 + uncommitted GOHO source changes including USB-MIDI string-index correction`.

## 2026-11-15 — Bennu USB 2-only isolation build

| Product | Version | Status | Artifacts | Notes |
|---|---:|---|---|---|
| GOHO Bennu | v0.2.20 | TEST | `bennu/GOHO-BENNU-v0.2.20-TEST.bin`, `.hex` | Clean H743 build with `GOHO_USB_RUNTIME_HS_ONLY`: USB 1 / OTG_FS is not initialized; USB 2 / PB14-PB15 carries CDC, USB Audio and USB MIDI. This is an isolation test image following the user's report that v0.2.19's ports did not operate correctly. Physical USB and audio behavior are not yet verified. |
| GOHO Bennu | v0.2.19 | TEST | `bennu/GOHO-BENNU-v0.2.19-TEST.bin`, `.hex` | Previous image retained for comparison. |

The user also reports that the GOHO Bennu EX image appears in the host MIDI list without the `unknown MIDI device` suffix; retain that as a user-reported reference for the later MIDI-name investigation. It was not verified by this build. Bennu v0.2.18 was removed from the current tree to retain the latest two images; it remains recoverable from Git history.

## 2026-11-15 — GOHO-NEXT-013 shared platform updates

| Product | Version | Status | Artifacts | Notes |
|---|---:|---|---|---|
| GOHO Bootloader | v1.0.6 | TEST | `bootloaders/GOHO-BOOTLOADER-v1.0.6-TEST.bin`, `.hex` | Clean H743 build; USB2/PB14-PB15 MSC. Physical update and handoff not tested. |
| GOHO Bootloader EX | v1.0.3 | TEST | `bootloaders/GOHO-BOOTLOADER-EX-v1.0.3-TEST.bin`, `.hex` | Clean H743 build; USB1/PA11-PA12 MSC. Physical update and handoff not tested. |
| GOHO Bennu | v0.2.21 | TEST | `bennu/GOHO-BENNU-v0.2.21-TEST.bin`, `.hex` | Standard USB split, common U1/U2, CV/Gate/probe and shared Reverb updates. H743 build and Host suite passed; hardware not tested. |
| GOHO Bennu EX | v0.2.19 | TEST | `bennu/GOHO-BENNU-EX-v0.2.19-TEST.bin`, `.hex` | USB1-only EX build; Freeze/Seed handlers remain disabled. H743 build passed; hardware not tested. |
| GOHO Pluto | v0.1.17 | TEST | `pluto/GOHO-PLUTO-v0.1.17-TEST.bin`, `.hex` | Standard USB split and common CV/Gate/probe/Reverb integration. H743 build passed; hardware not tested. |
| GOHO Rhea | v0.1.8 | TEST | `rhea/GOHO-RHEA-v0.1.8-TEST.bin`, `.hex` | Standard USB split and common CV/Gate/probe/Reverb integration. H743 build passed; hardware not tested. |

All six builds used the GOHO source project at `5c24927fe2f675134095d0827742532c5d113b8e` plus its uncommitted NEXT-013 working tree, and GNU Arm Embedded Toolchain 10.3.1. Artifacts remain TEST pending hardware verification. Exact sizes and hashes are in `firmware-manifest.json` and `SHA256SUMS.txt`.


## 2026-11-16 — GOHO Bennu USB2-only recovery build

| Product | Version | Status | Artifacts | Notes |
|---|---:|---|---|---|
| GOHO Bennu | v0.2.22 | TEST | `bennu/GOHO-BENNU-v0.2.22-TEST.bin`, `.hex` | Restores the USB2-only route. USB1/OTG_FS is not initialized; CDC, USB Audio and USB MIDI use PB14/PB15; PA11/PA12 remain available for Freeze/Seed. Clean H743 build passed; exact image awaits board retest. |
| GOHO Bennu | v0.2.20 | TEST | `bennu/GOHO-BENNU-v0.2.20-TEST.bin`, `.hex` | Retained as rollback image. |

Bennu v0.2.21 was removed from the current downloadable tree per the user's restoration request; its history remains in Git. v0.2.19 was also removed so the current tree keeps only v0.2.22 and v0.2.20.


## 2026-11-16 — GOHO-NEXT-014 shared H743 user-data persistence candidates

| Product | Version | Status | Artifacts | Notes |
|---|---:|---|---|---|
| GOHO Bennu | v0.2.23 | TEST | `bennu/GOHO-BENNU-v0.2.23-TEST.bin`, `.hex` | Clean H743 build with the Sector 7 shared user-data journal and Bennu legacy-data read/migration path. Host CTest 46/46 passed. Physical migration and power-loss recovery were not run. |
| GOHO Bennu EX | v0.2.20 | TEST | `bennu/GOHO-BENNU-EX-v0.2.20-TEST.bin`, `.hex` | Clean H743 EX build with the same persistent-storage backend. Physical persistence tests were not run. |
| GOHO Pluto | v0.1.18 | TEST | `pluto/GOHO-PLUTO-v0.1.18-TEST.bin`, `.hex` | Clean H743 build with its namespaced settings/calibration loading. A Pluto settings-save action and physical persistence test are not implemented/run. |
| GOHO Rhea | v0.1.9 | TEST | `rhea/GOHO-RHEA-v0.1.9-TEST.bin`, `.hex` | Clean H743 build with its namespaced settings/calibration loading. A Rhea settings-save action and physical persistence test are not implemented/run. |

All application images link at `0x08020000`; GNU Arm Embedded Toolchain 10.3.1. Source: local GOHO commit `f9a4a39d649f55a0877b717414c657c9588c388f`, mirrored on GitHub as `4b8a579a719181d916ccfbfbd47d7f0d288ca307` (tree `c399bc2169ec7e1c5574cbbed55f05bfaaf9bcfd`). Every image remains TEST. No Bootloader was rebuilt for NEXT-014.

## 2026-11-16 — GOHO-NEXT-015 shared persistence workflow candidates

| Product | Version | Status | Artifacts | Notes |
|---|---:|---|---|---|
| GOHO Bennu | v0.2.24 | TEST | `bennu/GOHO-BENNU-v0.2.24-TEST.bin`, `.hex` | Clean GOHO H743 build; shared CDC calibration/status, capacity reporting and coalesced Bennu state persistence. |
| GOHO Bennu EX | v0.2.21 | TEST | `bennu/GOHO-BENNU-EX-v0.2.21-TEST.bin`, `.hex` | Clean GOHO H743 EX build; persistence software included; EX remains a separate test variant. |
| GOHO Pluto | v0.1.19 | TEST | `pluto/GOHO-PLUTO-v0.1.19-TEST.bin`, `.hex` | Clean GOHO H743 build; explicit namespaced model/settings save and shared calibration console. |
| GOHO Rhea | v0.1.10 | TEST | `rhea/GOHO-RHEA-v0.1.10-TEST.bin`, `.hex` | Clean GOHO H743 build; explicit namespaced model/settings save and shared calibration console. |

All images were built independently from the GOHO project with GNU Arm Embedded Toolchain 10.3.1 and link at `0x08020000`. They remain TEST: no physical Flash programming, calibration measurement, power-cycle, cross-module persistence, or MSC-update-preservation test was run. Host CTest passed 48/48; exact file hashes are recorded in the source project NEXT-015 report and this repository's manifest/checksum list.

The current download tree now retains only the latest two firmware images for every product and Bootloader variant. Bootloader v1.0.4 and Bootloader EX v1.0.1 were removed from the current tree; both remain recoverable from Git history. No Bootloader was rebuilt for NEXT-015.
