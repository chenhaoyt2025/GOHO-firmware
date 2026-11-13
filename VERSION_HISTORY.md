# GOHO Firmware Version History

## 2026-11-12 — GOHO-NEXT-007

| Product | Version | Status | Artifacts | Notes |
|---|---:|---|---|---|
| GOHO Bootloader | v1.0.0 | TEST | `bootloaders/GOHO-BOOTLOADER-v1.0.0-TEST.bin`, `.hex` | Rebuilt from the GOHO H743 no-WAV bootloader target; no bootloader source change in NEXT-007. |
| GOHO BEADS | v0.2.0 | TEST | `beads/GOHO-BEADS-v0.2.0-TEST.bin`, `.hex` | WS2812 initialization/display ownership and H743 clock alignment fixes; USB MIDI composite target retained. Hardware verification is still pending. |

`TEST` is intentional: target compilation passed, but WS2812 behavior and USB MIDI enumeration were not verified on physical hardware in this run.

Hashes and sizes are recorded in `SHA256SUMS.txt` and `firmware-manifest.json`.


## 2026-11-12 — GOHO-NEXT-007 descriptor repair follow-up

| Product | Version | Status | Artifacts | Notes |
|---|---:|---|---|---|
| GOHO BEADS | v0.2.1 | TEST | `beads/GOHO-BEADS-v0.2.1-TEST.bin`, `.hex` | Adds a GOHO-owned USB composite descriptor repair for MIDIStreaming/AIC association; retains WS2812 initialization/clock/display fixes. Clean target build passed. On this exact image, macOS CoreMIDI source/destination enumeration, CDC echo, USB Audio device recognition, and virtual-disk bootloader update passed. WS2812B behavior and continuous USB Audio streaming remain unverified. |

v0.2.1 remains `TEST`: MIDI event send/receive and physical WS2812B behavior were not tested.

## 2026-11-12 — GOHO-NEXT-007 4051 input interrupt fix

| Product | Version | Status | Artifacts | Notes |
|---|---:|---|---|---|
| GOHO BEADS | v0.2.2 | TEST | `beads/GOHO-BEADS-v0.2.2-TEST.bin`, `.hex` | Adds the missing ADC3 DMA Stream4 IRQ dispatch required to publish accepted 4051 samples, and maps the seventh muxed Pitch Amount pot into RGB knob feedback. H743 clean target build passed. Hardware confirmation of mux movement, reverb response, WS2812 output, and USB regressions is pending. |

v0.2.2 remains `TEST` until those hardware checks pass.


## 2026-11-12 — GOHO-NEXT-007 reverb extension and X Plus archive

| Product | Version | Status | Artifacts | Notes |
|---|---:|---|---|---|
| GOHO BEADS | v0.2.3 | TEST | `beads/GOHO-BEADS-v0.2.3-TEST.bin`, `.hex` | Reverb control extension: original maximum at 80%, extended decay/density/diffusion above 80%, feedback damping and output safety. H743 build artifacts were produced; this image has not yet received user listening validation. |
| GOHO PLAITS PLUS | v0.1.0 | TEST | `plaits/GOHO-PLAITS-PLUS-v0.1.0-TEST.bin`, `.hex` | First archive catalog version; sourced from `build/plaits_plus`. |
| GOHO RINGS PLUS | v0.1.0 | TEST | `rings/GOHO-RINGS-PLUS-v0.1.0-TEST.bin`, `.hex` | First archive catalog version; sourced from `build/rings_plus`. |
| GOHO ELEMENTS PLUS | v0.1.0 | TEST | `elements/GOHO-ELEMENTS-PLUS-v0.1.0-TEST.bin`, `.hex` | First archive catalog version; sourced from `build/elements_plus`. |
| GOHO PEAKS PLUS | v0.1.0 | TEST | `peaks/GOHO-PEAKS-PLUS-v0.1.0-TEST.bin`, `.hex` | First archive catalog version; sourced from `build/peaks_plus`. |

The four X Plus catalog versions are archive labels, not upstream version claims. The source checkout was at `42a740fc7c019aacd1307e43ba50112cee5ab5e1` with local modifications, including product makefiles; reproducibility from the clean commit is unverified. The ELF program headers place each application at `0x08020000`. These historical application images were not repackaged with any bootloader, and compatibility with the current GOHO Bootloader was not verified.

The GOHO Bootloader v1.0.0-TEST artifact is retained unchanged from its existing archive entry; the rebuilt image SHA-256 matches the archived artifact.

## 2026-11-12 — GOHO-NEXT-008 platform integration

| Product | Version | Status | Artifacts | Notes |
|---|---:|---|---|---|
| GOHO BEADS | v0.2.4 | TEST | `beads/GOHO-BEADS-v0.2.4-TEST.bin`, `.hex` | H743 Board pin/peripheral profile, Board system startup, reusable WS2812 transmitter/encoder and shared build-source integration. Independent clean target build; application address `0x08020000`. No new hardware test was performed for this image. |

Build evidence: source HEAD `0f323c9dacd01715c238b6f3525ba16931707581` plus the pre-existing dirty workspace and NEXT-008 changes; build directory `build/next008-h743`; GNU Arm Embedded Toolchain 10.3.1. BIN: 326056 bytes, SHA-256 `5cfba19e0bd0c05794c756235c4140a884fecdc10cac83c35d58270b148dd357`. HEX: 917065 bytes, SHA-256 `d42c70c9c25dbad9542323d690cd46afb4b92b20ca70059b297aeafeb93080d6`.

The GOHO Bootloader is unchanged and was not rebuilt or re-archived in NEXT-008. The v0.2.4 image remains `TEST`; build success does not imply this exact image passed hardware validation.

## 2026-11-13 — GOHO-NEXT-009 Plaits module and shared-platform regression

| Product | Version | Status | Artifacts | Notes |
|---|---:|---|---|---|
| GOHO PLAITS | v0.1.0 | TEST | `plaits/GOHO-PLAITS-v0.1.0-TEST.bin`, `.hex` | First independent GOHO PLAITS application. Uses the Mutable Instruments Plaits DSP source subset, shared GOHO H743 Board audio/ADC runtime, physical controls/CV, and USB MIDI Note On/Off processing. |
| GOHO BEADS | v0.2.5 | TEST | `beads/GOHO-BEADS-v0.2.5-TEST.bin`, `.hex` | Clean regression build after shared H743 audio, ADC, USB, and target build integration. The image differs from v0.2.4 and was not hardware retested. |

Both application vectors are linked at `0x08020000`. GNU Arm Embedded Toolchain 10.3.1 was used. GOHO source HEAD was `0f323c9dacd01715c238b6f3525ba16931707581` plus the pre-existing dirty workspace and NEXT-009 uncommitted changes. Build output directories are `build/next009-plaits` and `build/next009-beads`. Hashes and byte counts are in `firmware-manifest.json` and `SHA256SUMS.txt`.

The Plaits test image has not been installed or run on hardware. Host DSP/control tests and the target compile/link passed; this is not a hardware audio, MIDI enumeration, CV calibration, USB CDC, or USB Audio pass. Both images remain `TEST`.


## 2026-11-13 — GOHO-NEXT-009 Plaits recovery build

| Product | Version | Status | Artifacts | Notes |
|---|---:|---|---|---|
| GOHO PLAITS | v0.1.1 | TEST | `plaits/GOHO-PLAITS-v0.1.1-TEST.bin`, `.hex` | Recovery build after v0.1.0 was reported nonfunctional following virtual-disk installation. Defaults to the continuous Virtual Analog engine; uses Media/Assign to select models and Board gate inputs for triggers; restores Plaits Plus reverb, CDC monitoring, and USB Audio routing. Host/target checks pass; GOHO-board confirmation is pending. |


## 2026-11-13 — GOHO-NEXT-009 Plaits WS2812B integration

| Product | Version | Status | Artifacts | Notes |
|---|---:|---|---|---|
| GOHO PLAITS | v0.1.2 | TEST | `plaits/GOHO-PLAITS-v0.1.2-TEST.bin`, `.hex` | Adds the Plaits startup chase and knob-value display in the GOHO module application; reuses the existing GOHO H743 transmitter and encoder. Hardware LED confirmation is pending. |

Built for STM32H743 with GNU Arm Embedded Toolchain 10.3.1 at application address `0x08020000`. Source revision: `0f323c9dacd01715c238b6f3525ba16931707581 plus pre-existing dirty workspace and GOHO-NEXT-009 Plaits LED changes`. Build directory: `build/next009-plaits-led-20261113`. BIN: 302416 bytes, SHA-256 `a3617bbc6b4068932b5fa2dc861573c98971063f00548aa3b59e65ccd1d100ff`. HEX: 850571 bytes, SHA-256 `fc7cd2544af4e1fe09f43cd5f793078da0cbcdc3cc9ef37ef2b2eae829922346`. The image remains `TEST`; clean build success does not confirm LED behavior on hardware.


## 2026-11-13 — GOHO-NEXT-009 Plaits CDC and board LED correction

| Product | Version | Status | Artifacts | Notes |
|---|---:|---|---|---|
| GOHO PLAITS | v0.1.3 | TEST | `plaits/GOHO-PLAITS-v0.1.3-TEST.bin`, `.hex` | Shared GOHO H743 WS2812 display for five direct pots plus seven 4051 channels; CDC pages with `0=engines` and `9=all`; USB product/configuration/interface descriptors use `goho modular synth`.

Built from GOHO source HEAD `0f323c9dacd01715c238b6f3525ba16931707581` plus the existing dirty workspace and this NEXT-009 correction. Build directory: `/Users/hoho_mini/Documents/GOHO-eurorack/build/next009-plaits-repair-20261113`; target: STM32H743, application address `0x08020000`, GNU Arm Embedded Toolchain 10.3.1. BIN: 304016 bytes, SHA-256 `9d52e12b8f218645761c3ee53ce8d3673f1225d2c681aa0d2ffb6456881f66e2`. HEX: 855071 bytes, SHA-256 `d02450fdeefbbc50de19f66f09d452f5794d280fbe85ddc2e2e96ef18c7e7a1c`. Hardware LED, CDC, and host USB-name confirmation remain pending; status is TEST.


## 2026-11-13 — GOHO-NEXT-010 shared platform update

| Product | Version | Status | Artifacts | Notes |
|---|---:|---|---|---|
| GOHO PLAITS | v0.1.4 | TEST | `plaits/GOHO-PLAITS-v0.1.4-TEST.bin`, `.hex` | Shares the GOHO H743 WS2812 display, CDC page/banner/XXX service, GOHO-PLAITS USB identity and established BEADS reverb implementation through the public GOHO facade. H743 clean build and Host suite passed; this exact image was not installed on hardware. |
| GOHO BEADS | v0.2.6 | TEST | `beads/GOHO-BEADS-v0.2.6-TEST.bin`, `.hex` | Regression image for shared WS2812, CDC, USB identity and reverb entry point; preserves BEADS extended reverb controls. H743 clean build and Host suite passed; this exact image was not installed on hardware. |

Both applications use GNU Arm Embedded Toolchain 10.3.1 and link at `0x08020000`. Source HEAD was `0f323c9dacd01715c238b6f3525ba16931707581` plus the pre-existing dirty workspace and NEXT-010 edits. Exact build directories, sizes and SHA-256 values are recorded in `firmware-manifest.json` and `SHA256SUMS.txt`. Both artifacts remain `TEST`; build and Host tests do not constitute board verification.


## 2026-11-13 — GOHO-NEXT-010 final verified software builds

| Product | Version | Status | Artifacts | Notes |
|---|---:|---|---|---|
| GOHO PLAITS | v0.1.5 | TEST | `plaits/GOHO-PLAITS-v0.1.5-TEST.bin`, `.hex` | Final NEXT-010 image with shared WS2812 panel display, CDC monitor digit parsing/commands/XXX path, GOHO-PLAITS USB identity and existing BEADS-based reverb path. Host CTest `37/37 PASS`; H743 clean build passed. Hardware installation and user-facing USB name/LED tests remain pending. |
| GOHO BEADS | v0.2.7 | TEST | `beads/GOHO-BEADS-v0.2.7-TEST.bin`, `.hex` | Final BEADS regression image for shared board display, CDC service, USB identity and Reverb entry point; extended BEADS reverb controls retained. Host CTest `37/37 PASS`; H743 clean build passed. Hardware retest not run. |

These final images use GNU Arm Embedded Toolchain 10.3.1 and application address `0x08020000`. The earlier v0.1.4/v0.2.6 NEXT-010 successful builds remain archived as separate immutable TEST artifacts; their build maps/logs were preserved under the source repository `build/next010-intermediate-*` directories. The v0.1.5/v0.2.7 build directories, byte sizes, source revision note, and hashes are listed in `firmware-manifest.json` and `SHA256SUMS.txt`.


## 2026-11-13 — GOHO Plaits CDC, USB MIDI identity and engine-order fix

| Product | Version | Status | Artifacts | Notes |
|---|---:|---|---|---|
| GOHO PLAITS | v0.1.6 | TEST | `plaits/GOHO-PLAITS-v0.1.6-TEST.bin`, `.hex` | MIDI interface/jack strings now reference the module product name and USB serial includes a product suffix; the all-data CDC page is removed, `S` toggles full/compact format, and button/`E+`/`E-` model traversal follows original Plaits model numbers 0-23. H743 clean build passed; hardware installation and host USB enumeration were not run. |

Built with GNU Arm Embedded Toolchain 10.3.1 for STM32H743 at application address `0x08020000`. GOHO source HEAD was `0f323c9dacd01715c238b6f3525ba16931707581` plus the pre-existing dirty workspace and this user-requested Plaits fix. Build directory: `build/plaits-user-fix-016`. BIN: 307000 bytes, SHA-256 `53a85f8abe6118f182abd99f44e1323b2617dec238b3260877a95e40876813ba`. HEX: 863470 bytes, SHA-256 `73c11ff48872fb310b93529362c57448e5b2daa64536076dbc6cf584bd11b3fc`. Status remains TEST until the user installs and checks the image.


## 2026-11-13 — GOHO MIDI Pitch and Plaits model correction

| Product | Version | Status | Artifacts | Notes |
|---|---:|---|---|---|
| GOHO PLAITS | v0.1.7 | TEST | `plaits/GOHO-PLAITS-v0.1.7-TEST.bin`, `.hex` | MIDI pitch now uses Pitch Bend, the USB product name is `goho plaits`, MODEL CV is centered around 0 V, and all 24 model indices follow upstream Plaits registration order. Host CTest and H743 clean build passed; physical verification is pending. |
| GOHO BEADS | v0.2.8 | TEST | `beads/GOHO-BEADS-v0.2.8-TEST.bin`, `.hex` | MIDI pitch now uses Pitch Bend rather than CC1; the USB product name is `goho beads`. Host CTest and H743 clean build passed; physical verification is pending. |

Built with GNU Arm Embedded Toolchain 10.3.1 for STM32H743, application address `0x08020000`, from GOHO source HEAD `0f323c9dacd01715c238b6f3525ba16931707581` plus the pre-existing dirty workspace and these user-requested corrections. Exact sizes, hashes and build directories are recorded in `firmware-manifest.json` and `SHA256SUMS.txt`. Both images remain `TEST`.


## 2026-11-13 — BEADS operating-state WS2812 indicator

| Product | Version | Status | Artifacts | Notes |
|---|---:|---|---|---|
| GOHO BEADS | v0.2.9 | TEST | `beads/GOHO-BEADS-v0.2.9-TEST.bin`, `.hex` | Adds WS2812B idle state slots: 0 Auto/waiting, 1 USB, 2 Line, 3 Synth. USB product string remains lowercase pending the separately authorized shared identity update. Hardware verification is pending. |

Built with GNU Arm Embedded Toolchain 10.3.1 for STM32H743 at application address `0x08020000`. Build directory: `build/goho-baseline-beads-029`. BIN: 327160 bytes, SHA-256 `23191d305010fde7ec980c7f981a168a02492ae618cfac8fb4835c4f0b64a58f`. HEX: 920170 bytes, SHA-256 `ea29b4771941395a979e498b12996cb36a9b2feb0850d303d371295892594f3d`. This is a clean target build only; the image has not been installed on hardware.
