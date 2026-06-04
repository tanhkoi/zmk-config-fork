# ZMK Dongle Corne Sofle

A comprehensive [ZMK Firmware](https://zmk.dev/) configuration repository for custom split keyboards with dongle (wireless transceiver) and traditional wireless support.

## Overview

This repository contains optimized ZMK firmware configurations for building and customizing split mechanical keyboards. It supports multiple keyboard layouts including Corne, Sofle, Lily58, and SplitKB Aurora Sofle, with flexibility for both standalone split setups and dongle-based wireless connectivity.

**Key Features:**
- 🎮 **Multiple Keyboard Layouts**: Pre-configured support for Corne, Sofle, Lily58, and SplitKB Aurora Sofle
- 📡 **Dongle Support**: Wireless transceiver configurations for reduced latency and improved connectivity
- 🔧 **Flexible Board Support**: Compatible with nRF Micro v11, nRF Micro v13, Nice Nano v2, and Pro Micro variants
- ⌨️ **Customizable Keymaps**: Easy-to-modify keymap files with language support (German ISO included)
- 🎨 **Display Support**: Optional dongle display widget integration
- 🌈 **RGB Configuration**: Built-in RGB lighting snippets
- 📊 **Keymap Visualization**: Keymap drawer configurations for visual keymap documentation

## Repository Structure

```
├── boards/                    # Board-specific overlays and configurations
│   ├── *.overlay             # Device tree overlays for different microcontroller boards
│   └── shields/              # Shield definitions for each keyboard
│       ├── corne/            # Corne keyboard configuration
│       ├── lily58/           # Lily58 keyboard configuration
│       ├── sofle/            # Sofle keyboard configuration
│       └── dongle_display/   # Dongle display widget support
├── config/                   # Central configuration files
│   ├── *.keymap             # Keymap definitions per keyboard
│   ├── *.conf               # ZMK configuration settings
│   └── west.yml             # Zephyr Manifest file for dependency management
├── snippets/                # Reusable configuration snippets
│   ├── common-config/       # Shared configurations
│   ├── dongle-config/       # Dongle-specific settings
│   └── rgb-config/          # RGB lighting configurations
├── keymap-drawer/           # Visual keymap documentation
│   └── *.yaml              # Keymap drawer configuration files
├── zephyr/                  # Zephyr module configuration
├── build.yaml              # Build configuration
└── README.md               # This file
```

## Supported Keyboards

### Corne
- **Half-size split keyboard** with 3x6 keys per side
- **Supported Boards**: Pro Micro, nRF Micro 11, nRF Micro 13, Nice Nano v2, XIAO
- **Dongle Variant**: Wireless connectivity via transceiver

### Sofle
- **Full-size split keyboard** with 4x6 keys per side plus encoder support
- **Supported Boards**: Pro Micro, nRF Micro 11, nRF Micro 13, Nice Nano v2, XIAO
- **Dongle Variant**: Wireless transceiver option
- **Variants**: SplitKB Aurora Sofle with integrated lighting

### Lily58
- **Ergonomic split keyboard** with 4x6+2 keys per side
- **Supported Boards**: Pro Micro, nRF Micro 11, nRF Micro 13, Nice Nano v2, XIAO
- **Dongle Variant**: Wireless connectivity support

## Microcontroller Boards

Configurations support multiple microcontroller options:
- **nRF Micro v11** - Standard and flipped orientation
- **nRF Micro v13** - Latest version with improved specifications
- **Nice Nano v2** - Popular ZMK-optimized board
- **Pro Micro** - Legacy board support for compatibility

## Configuration Options

### Common Configurations
Located in `/snippets/`:
- **common-config**: Shared settings across keyboards
- **dongle-config**: Wireless transceiver-specific settings
- **rgb-config**: RGB underglow and backlight configurations

### Language Support
- **German ISO**: Custom keymap include file (`keymap_german_mac_iso_zmk.h`) for German keyboard layouts

### Display Support
Optional dongle display widget (`dongle_display`) for status information and visual feedback.

## Building and Flashing

This repository uses the [ZMK Build System](https://zmk.dev/docs/development/setup) with [west](https://docs.zephyrproject.org/latest/develop/west/) for managing dependencies and builds.

### Prerequisites
- ZMK development environment set up
- `west` CLI tool installed
- Appropriate firmware build toolchain

### Automated Builds with GitHub Actions

This repository uses **GitHub Actions** to automatically build firmware for all supported keyboards and boards.

**How it works:**
- Firmware builds are triggered automatically on every push or can be manually triggered
- Compiled `.uf2` files are generated for each keyboard and board combination
- Build artifacts are available in the [Actions](../../actions) tab

**To get your firmware:**

1. **Clone the repository**
   ```bash
   git clone <repository-url>
   cd zmk-dongle-corne-sofle
   ```

2. **Download pre-built firmware**
   - Navigate to the [Actions](../../actions) tab
   - Select the latest successful workflow run
   - Download the `.uf2` file for your keyboard and board combination

3. **Flash the firmware** to your microcontroller
   - Connect your microcontroller in bootloader mode
   - Copy the `.uf2` file to the mounted USB drive
   - Wait for the flash to complete and the device to reboot

**For local builds:**

If you prefer to build locally, ensure you have the [ZMK development environment](https://zmk.dev/docs/development/setup) set up, then:
```bash
west update
west build -b <board> -s app
```

For detailed ZMK build instructions, refer to the [official ZMK documentation](https://zmk.dev/docs/user-setup).

## Keymap Customization

Modify keyboard layouts in:
- `/config/*.keymap` - Central keymap files
- `/boards/shields/<keyboard>/*.keymap` - Shield-specific keymaps
- `/boards/shields/<keyboard>/<board>*.overlay` - Board-specific modifications

## Keymap Visualization

Generate visual keymap documentation using [keymap-drawer](https://github.com/nickcoutsos/keymap-drawer):
- Configuration files located in `/keymap-drawer/`
- Customize layout, labels, and visual appearance
- Export to PNG, SVG, or other formats for documentation

## Contributing

Feel free to submit issues, fork the repository, and create pull requests for improvements or new keyboard support.

## Resources

- [ZMK Documentation](https://zmk.dev/)
- [ZMK Discord Community](https://discord.gg/8gH7ZuQ)
- [Keyboard Firmware Best Practices](https://zmk.dev/docs)
- [keymap-drawer](https://github.com/nickcoutsos/keymap-drawer)

## License

Check the repository for license information.
