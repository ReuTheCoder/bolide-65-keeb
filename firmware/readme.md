# bolide65

![bolide65](imgur.com image replace me!)

A 65% keyboard with a rotary encoder and RGB backlighting per key, built around the Waveshare RP2040-Zero

* Keyboard Maintainer: [Reuben O](https://github.com/ReuTheCoder)
* Hardware Supported: Bolide65 PCB with a Waveshare RP2040-Zero
* Hardware Availability: [Custom PCB made in KiCAD](https://github.com/ReuTheCoder/bolide-65-keeb/tree/main/pcb) 

Make example for this keyboard (after setting up your build environment):

    make bolide65:default

Flashing example for this keyboard:

    make bolide65:default:flash

See the [build environment setup](https://docs.qmk.fm/#/getting_started_build_tools) and the [make instructions](https://docs.qmk.fm/#/getting_started_make_guide) for more information. Brand new to QMK? Start with our [Complete Newbs Guide](https://docs.qmk.fm/#/newbs).

## Bootloader

Enter the bootloader in 3 ways:

* **Bootmagic reset**: Hold down the key at (0,0) in the matrix (usually the top left key or Escape) and plug in the keyboard
* **Physical reset button**: Hold the BOOT button on the RP2040-Zero while plugging connected USB-C to keyboard
* **Keycode in layout**: Press the key mapped to `QK_BOOT` if it is available
