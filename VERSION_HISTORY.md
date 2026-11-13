# GOHO Firmware Version History

Only the current and immediately previous images for GOHO Bennu, GOHO Pluto, and the four Plus products are kept in the latest repository tree. Older releases remain recoverable from Git commit history.

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
