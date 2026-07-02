# GGP Keyboards — Firmware Builds

A public mirror of ready-to-flash firmware builds for GGP Keyboards products. These are convenience copies for easy sharing and direct download. The authoritative sources are the [ggpkbd Vial-QMK fork](https://github.com/ggpkbd/vial-qmk) and the ggpkbd-configurator project — this repo holds the compiled outputs only.

---

## Repository Layout

Firmware is organized **keyboard-first, then stack**:

```
<keyboard>/<stack>/<build-file>
```

| Segment | Values | Notes |
|---|---|---|
| `<keyboard>` | `corne-v4.1`, `planck`, `hotdox76v2`, … | Use the product name, lowercase, hyphens |
| `<stack>` | `vial-qmk`, `qmk`, `zmk` | Matches the firmware framework |
| `<build-file>` | `.uf2` (RP2040), `.hex` (AVR) | Keep the native tool filename |

Current tree:

```
ggpkbd/firmware
└── corne-v4.1/
    └── vial-qmk/
        └── crkbd_rev4_1_standard_vial.uf2
```

### Adding a future build

Drop the compiled file into the matching `<keyboard>/<stack>/` directory and add a row to the index table below. Do not create empty directories for keyboards that have no build yet.

---

## Available Builds

> **Note:** Raw GitHub links resolve only after the PR is merged to `main`.

| Keyboard | Stack | File | Download |
|---|---|---|---|
| Corne V4.1 (CRKBD) | Vial-QMK | `crkbd_rev4_1_standard_vial.uf2` | [Download](https://raw.githubusercontent.com/ggpkbd/firmware/main/corne-v4.1/vial-qmk/crkbd_rev4_1_standard_vial.uf2) |

---

## Flashing Instructions

### RP2040 boards — Corne V4.1 / CRKBD (`.uf2`)

1. Double-tap the reset button on the controller. The board mounts as a USB drive named **`RPI-RP2`**.
2. Drag and drop the `.uf2` file onto the `RPI-RP2` drive.
3. The drive unmounts automatically when flashing is complete. Repeat for the second half if your Corne is split.

### AVR boards — e.g. HotDox76 V2, Sofle (`.hex`)

Flash the `.hex` file using one of the following:

- **QMK Toolbox** — open the file, put the board into bootloader mode, click Flash.
- **dfu-programmer** — `dfu-programmer atmega32u4 erase && dfu-programmer atmega32u4 flash <file>.hex && dfu-programmer atmega32u4 reset` (the `reset` step exits the bootloader so the board comes back as a keyboard)
- The board's native bootloader utility if applicable.

Consult the [QMK documentation](https://docs.qmk.fm/#/flashing) for board-specific bootloader entry methods.

---

## Disclaimer

Firmware is provided as-is without warranty. Flash at your own risk. GGP Keyboards is not responsible for damage caused by incorrect firmware or flashing errors. Always verify you are flashing the correct file for your specific keyboard and controller.
