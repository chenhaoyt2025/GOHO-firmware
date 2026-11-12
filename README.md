# GOHO-firmware

Versioned firmware artifacts for GOHO products. This repository contains release images and metadata only; it does not contain the GOHO source tree.

## Current artifacts

- `bootloaders/GOHO-BOOTLOADER-v1.0.0-TEST.bin` / `.hex`
- `beads/GOHO-BEADS-v0.2.2-TEST.bin` / `.hex` (current BEADS test image)
- `beads/GOHO-BEADS-v0.2.1-TEST.bin` / `.hex` (previous image)
- `beads/GOHO-BEADS-v0.2.0-TEST.bin` / `.hex` (older image)

All images are `TEST`, not `STABLE`. On v0.2.1, USB MIDI enumeration through macOS CoreMIDI, a CDC echo, USB Audio device recognition, and the virtual-disk bootloader update path were verified. v0.2.2 adds the 4051 DMA interrupt and RGB mapping fix; its hardware behavior still requires confirmation.

See `VERSION_HISTORY.md`, `SHA256SUMS.txt`, and `firmware-manifest.json` for exact sizes, build provenance, addresses, and SHA-256 values.
