# GO HOME Firmware Library

Public firmware catalog for GOHO University.

GitHub repository names cannot contain spaces, so the repository uses the URL-safe name `go-home-firmware`.

## Where to add files

- Fixed bootloaders: `bootloaders/`
- Application and combo firmware: `firmware/`
- Catalog metadata: `firmware-manifest.json`

The website reads `firmware-manifest.json` and displays the friendly `name` and `version`. The `file` field is a repository-relative path; do not paste long raw GitHub URLs.

## Firmware entry rules

- `type: "bootloader"`: fixed bootloader image.
- `type: "application"`: application-only image, normally paired with a bootloader.
- `type: "combo"`: image containing bootloader plus application; do not add a bootloader separately.
- `format: "bin"` or `format: "hex"`.

For application-only BIN files, fill in `flashAddress` with the application start address. HEX files normally carry their own addresses.

## Catalog example

```json
{
  "schema": 1,
  "bootloaders": [
    {
      "id": "goho-stm32-default",
      "name": "GOHO Fixed Bootloader",
      "version": "1.0.0",
      "file": "bootloaders/goho-bootloader.hex",
      "format": "hex",
      "device": "GOHO",
      "default": true
    }
  ],
  "firmwares": [
    {
      "id": "eurorack-1.0.0",
      "name": "Eurorack",
      "version": "1.0.0",
      "file": "firmware/eurorack-1.0.0.hex",
      "format": "hex",
      "type": "application",
      "device": "Eurorack",
      "vendorId": "0x0483",
      "productId": "0x4011"
    }
  ]
}
```

Do not store GitHub tokens or private credentials in this repository.
