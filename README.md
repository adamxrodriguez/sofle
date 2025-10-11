# ZMK Firmware for Sofle RGB

This is a ZMK user config repository for the Sofle keyboard with RGB underglow, OLED displays, and rotary encoders.

## Hardware

- **Keyboard**: Sofle RGB
- **Controller**: nice!nano v2 (or compatible nRF52840 board)
- **Features**: RGB underglow, OLED displays, rotary encoders

## Keymap

The keymap includes 4 layers:
- **Base Layer**: Standard QWERTY layout
- **Lower Layer**: Function keys, numbers, and symbols
- **Raise Layer**: Navigation, Bluetooth controls, and media keys
- **Adjust Layer**: RGB controls (accessed by holding both Lower and Raise)

### RGB Controls (Adjust Layer)
- **BT Clear**: Clear Bluetooth bonds
- **BT 1-5**: Select Bluetooth profiles
- **RGB Toggle**: Toggle RGB underglow on/off
- **RGB HUE +/-**: Adjust hue
- **RGB SAT +/-**: Adjust saturation
- **RGB BRI +/-**: Adjust brightness
- **RGB Effect**: Cycle through effects
- **Ext Power**: Toggle external power

## Building Firmware

### Automatic Build (Recommended)

This repository uses GitHub Actions to automatically build firmware when you push changes.

1. Fork this repository
2. Enable GitHub Actions in your fork
3. Push changes to trigger a build
4. Download the firmware from the Actions artifacts

### Using the Keymap Editor

You can edit your keymap visually using the web-based keymap editor:

1. Go to https://nickcoutsos.github.io/keymap-editor/
2. Sign in with GitHub
3. Select this repository
4. Edit your keymap visually
5. Commit changes directly from the editor
6. GitHub Actions will automatically build the new firmware

### Local Build

If you prefer to build locally:

```bash
# Install west and dependencies
pip3 install --user -U west

# Initialize workspace
west init -l config/
west update

# Build firmware
west build -s zmk/app -b nice_nano_v2 -- -DSHIELD=sofle_left
west build -s zmk/app -b nice_nano_v2 -- -DSHIELD=sofle_right
```

## Flashing

1. Download the `.uf2` files from GitHub Actions artifacts or your local build
2. Connect the keyboard half to your computer
3. Double-tap the reset button to enter bootloader mode
4. Drag and drop the corresponding `.uf2` file to the mounted drive
5. Repeat for the other half

## Customization

- **Keymap**: Edit `config/sofle.keymap`
- **Settings**: Edit `config/sofle.conf`
- **Build targets**: Edit `build.yaml`

## Resources

- [ZMK Documentation](https://zmk.dev/)
- [Sofle Keyboard](https://github.com/josefadamcik/SofleKeyboard)
- [Keymap Editor](https://nickcoutsos.github.io/keymap-editor/)
- [ZMK Discord](https://zmk.dev/community/discord/invite)

## License

MIT License - see LICENSE file for details
