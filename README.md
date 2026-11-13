# GOHO-firmware

Versioned firmware artifacts for GOHO products. This repository contains release images and metadata only; it does not contain the GOHO source tree.

## Current artifacts

| Product | Current catalog image | Flash address | Status |
|---|---|---:|---|
| GOHO Bootloader | `bootloaders/GOHO-BOOTLOADER-v1.0.0-TEST` (`.bin`, `.hex`) | `0x08000000` | TEST |
| GOHO BEADS | `beads/GOHO-BEADS-v0.2.7-TEST` (`.bin`, `.hex`) | `0x08020000` | TEST |
| GOHO PLAITS | `plaits/GOHO-PLAITS-v0.1.6-TEST` (`.bin`, `.hex`) | `0x08020000` | TEST |
| GOHO PLAITS PLUS | `plaits/GOHO-PLAITS-PLUS-v0.1.0-TEST` (`.bin`, `.hex`) | `0x08020000` | TEST |
| GOHO RINGS PLUS | `rings/GOHO-RINGS-PLUS-v0.1.0-TEST` (`.bin`, `.hex`) | `0x08020000` | TEST |
| GOHO ELEMENTS PLUS | `elements/GOHO-ELEMENTS-PLUS-v0.1.0-TEST` (`.bin`, `.hex`) | `0x08020000` | TEST |
| GOHO PEAKS PLUS | `peaks/GOHO-PEAKS-PLUS-v0.1.0-TEST` (`.bin`, `.hex`) | `0x08020000` | TEST |

The four X Plus entries are archived historical application builds from the `eurorack-master_HOHO/build/` output directories. Their catalog versions were assigned for the first archive entry because the original builds did not include semantic version metadata. Their source checkout was dirty, so rebuilding identical images from the recorded revision is not guaranteed. They use the `0x08020000` application address, but compatibility with the current GOHO Bootloader and current board behavior was not revalidated.

All images remain `TEST`; archive inclusion does not imply current hardware validation. The user later confirmed a broad functional smoke test on the v0.2.3-era BEADS firmware, including USB MIDI receive. BEADS v0.2.5 is the NEXT-009 shared-platform regression build and has not been newly tested on hardware. GOHO PLAITS v0.1.0 was reported nonfunctional after installation through the goho bootloader virtual disk. The user later confirmed engine switching and audible output on the currently installed build. v0.1.2-TEST adds Plaits WS2812B startup and knob display behavior; this image still needs installation to confirm the LEDs on a GOHO board. SHA-256, exact sizes, source revisions and build directories are recorded in `VERSION_HISTORY.md`, `SHA256SUMS.txt`, and `firmware-manifest.json`.


GOHO PLAITS v0.1.3-TEST restores the CDC monitor pages (`0=engines`, `9=all`), applies the shared GOHO H743 WS2812 display path to all five direct pots and seven 4051 controls, and labels USB product/configuration/interface descriptors `goho modular synth`. This is a clean STM32H743 build; the new image has not yet been installed for hardware confirmation.

GOHO-NEXT-010 added `GOHO-PLAITS-v0.1.4-TEST` and `GOHO-BEADS-v0.2.6-TEST`. Both use the GOHO-owned shared WS2812, CDC, product identity and Reverb paths. They are software-built test images and have not been installed on hardware.


The current NEXT-010 test images are GOHO PLAITS v0.1.5 and GOHO BEADS v0.2.7. Earlier v0.1.4 and v0.2.6 NEXT-010 builds are retained in the archive history. The final images passed Host and STM32H743 build checks but have not been installed on a board.


GOHO PLAITS v0.1.6-TEST corrects the USB MIDI product-string reference and gives the USB serial a product suffix to avoid stale host identity reuse. It removes the all-telemetry monitor page, restores `S` full/compact formatting, and cycles model selection in original Plaits order 0-23. The STM32H743 clean build passed; this image has not yet been installed or tested on hardware.
