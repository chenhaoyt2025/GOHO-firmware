# GOHO-firmware

Versioned firmware artifacts for GOHO products. This repository contains release images and metadata only; it does not contain the GOHO source tree.

## Current artifacts

| Product | Current catalog image | Flash address | Status |
|---|---|---:|---|
| GOHO Bootloader | `bootloaders/GOHO-BOOTLOADER-v1.0.0-TEST` (`.bin`, `.hex`) | `0x08000000` | TEST |
| GOHO BEADS | `beads/GOHO-BEADS-v0.2.3-TEST` (`.bin`, `.hex`) | `0x08020000` | TEST |
| GOHO PLAITS PLUS | `plaits/GOHO-PLAITS-PLUS-v0.1.0-TEST` (`.bin`, `.hex`) | `0x08020000` | TEST |
| GOHO RINGS PLUS | `rings/GOHO-RINGS-PLUS-v0.1.0-TEST` (`.bin`, `.hex`) | `0x08020000` | TEST |
| GOHO ELEMENTS PLUS | `elements/GOHO-ELEMENTS-PLUS-v0.1.0-TEST` (`.bin`, `.hex`) | `0x08020000` | TEST |
| GOHO PEAKS PLUS | `peaks/GOHO-PEAKS-PLUS-v0.1.0-TEST` (`.bin`, `.hex`) | `0x08020000` | TEST |

The four X Plus entries are archived historical application builds from the `eurorack-master_HOHO/build/` output directories. Their catalog versions were assigned for the first archive entry because the original builds did not include semantic version metadata. Their source checkout was dirty, so rebuilding identical images from the recorded revision is not guaranteed. They use the `0x08020000` application address, but compatibility with the current GOHO Bootloader and current board behavior was not revalidated.

All images remain `TEST`; archive inclusion does not imply current hardware validation. The BEADS v0.2.3 image contains the reverb extension and still needs listening validation. SHA-256, exact sizes, source revisions and build directories are recorded in `VERSION_HISTORY.md`, `SHA256SUMS.txt`, and `firmware-manifest.json`.
