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
