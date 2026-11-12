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
