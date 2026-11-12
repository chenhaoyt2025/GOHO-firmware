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
