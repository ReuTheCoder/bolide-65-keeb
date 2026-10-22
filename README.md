# Bolide65
Bolide65 is a 66 key, 65% keyboard with a rotary encoder and RGB backlighting under each key. It was built as a submission to Hack Club's [Forge](https://forge.hackclub.com/) YSWS program.

![DONE](assets/journal/bolide-journal-IM_DONE_XD.png)

I was inspired to pursue this project after my sister's laptop's keyboard began acting up, preventing her from using the *t* and *u* key. She has to wait awhile before she can get a new laptop, so decided to make a keyboard for her in the meantime, using her design ideas (of incorporationg lights) to make the keyboard and consulting her on its appearance and functionality throughout the process. Not only am I helping my sister, but this project really helped me gain more hardware experience (especially regarding routing and CAD).

<img src="assets/readme/bolide-pcb_front.png" alt="PCB 3D" width="100%"> 

## Features

- 66 Cherry MX-compatible switch footprints in a custom 65% layout
- EC11 rotary encoder (push button enabled)
- RP2040 Zero microcontroller (USB-C) using QMK firmware
- 66 reverse mount SK6812MINI-E RGB LEDs on a single data chain
    - 74AHCT1G125 level shifter on the LED data line (3.3 V to 5 V) 
- 2-layer PCB with GND copper pours on both sides
- 4 PCB mounted stabilizers

## Layout
<img src="assets/readme/bolide-keeb_layout.png" alt="PCB Layout" width="100%"> 

*The keymap layout (`Bolide65_Layout.json`) was made with [Keyboard Layout Editor NG](https://editor.keyboard-tools.xyz/).

A 6.25u screw-in stabilizers is needed for the Backspace key, while 2u screw-in stabilizers are needed for the Enter, Left Shift, and Space keys. Any 65% compatible keycap set will work with this project. The one listed in the BOM was chosen for its see-through effect and low cost. The blank space in the top-right corner of the keymap is on purpose, as it leaves room for the microcontroller and the encoder. The blank keys is meant to be a custom macro.

## PCB

[![View PCB on KiCanvas](https://hack.club/pcb-badge)](https://kicanvas.org/?repo=https://github.com/reuthecoder/bolide-65-keeb/tree/main/pcb)

This is the PCB (307x101mm) I made for Bolide65, made in KiCad 10.0. Most of the footprints came from the [Marbastlib](https://github.com/ebastler/marbastlib) library, the microcontroller footprint was sourced from [SnapMagic](https://www.snapeda.com/parts/RP2040-ZERO/Waveshare%20Electronics/view-part/), and anything else came from KiCad's default libraries. I used the kbplacer plugin to correctly arrage the switches according to my keymap. 

The microcontroller, LEDs, diodes, resistors, and capacitors are meant to be soldered to the back of the board, while everything else is soldered tot the front. It is a 2 layer PCB with GND copper pours on both sides, and DRC passes with only silkscreen warnings. (No errors)

**Schematic:**

The project is split across three sheets: the root sheet (microcontroller, level shifter, LED capacitors, stabilizers), the key matrix, and the LED chain.

![Screenshot of root schematic](assets/readme/bolide-schematic_root.png)
![Screenshot of key matrix schematic](assets/readme/bolide-schematic_matrix.png)
![Screenshot of LED chain schematic](assets/readme/bolide-schematic_RGB.png)

**PCB:**

![Screenshot of PCB in KiCad](assets/readme/bolide65-pcb.png)

## Firmware 
The QMK firmware the keyboard microcontroller must be flashed with includes the matrix, encoder, and RGB matrix settings for the RP2040. Some notable firmware features are:
- Each function (F1, F2, etc) does not have its own button. Rather, each function can be accessed through the number row while holding down the `fn` key.
- The spare macro key switches through backlighting animations (normal press goes to next and shift goes back) and pressing it while on the `fn` setting changes the LED color.
- This keyboard uses the Grave Escape, so a plain press acts as the escape key, pressing shift inputs `~` and pressing it while on the `fn` setting inputs the backtick `.

## CAD

The PCB enclosure, designed in [Onshape](https://cad.onshape.com/documents/e99e54822f92a5f5925595cc/w/6180f1e1b18eeb4808e4ffdc/e/0a846f45fd57540ab5465ead?renderMode=0&leftPanel=false&uiState=6ad9a2dd98262f828faa99c4), utilizes a 'reverse' sandwich keyboard mount style: the top plate is the top most layer and there is a transluscent middle part that allows light to diffuse through the case and give a streak of color to the enclosure design (like a bolide does to the night sky). The case is designed for 4 M3x16mm screws, which are meant to screw into M3 heatset inserts with a 5mm OD and 4mm height. The inserts are inserted into the bottom case. Although the rotary encoder has a custom knob, keycaps are meant to be outsourced. See through keycaps are recommneded fo rthis keyboard design.

![DONE](assets/readme/bolide-CAD.png)

| Item Name | Qty | Price (USD) | Item link | Notes |
|---|---|---|---|---|
| 330 Ω 0603 resistor [Uni-Royal 0603WAF3300T5E] | 100 | $0.26 | [LCSC](https://www.lcsc.com/product-detail/Chip-Resistor-Surface-Mount_UNI-ROYAL-Uniroyal-Elec-0603WAF3300T5E_C23138.html) | Must purchase 100 in order to source the 1 resistor needed. 0603, SMD |
| 0.1 µF Ceramic Capacitors [Samsung Electro-Mechanics CL10B104KB8NNNC] | 100 | $0.79 | [LCSC](https://www.lcsc.com/product-detail/C1591.html) | Must purchase 100 in order to source the 67 capacitors needed. 0603, SMD |
| 74AHCT1G125 Level Shifter [TI SN74AHCT1G125DBVR] | 5 | $0.50 | [LCSC](https://www.lcsc.com/product-detail/C7484.html) | Must purchase 5 in order to source the 1 level shifter needed. SOT-23-5, use the AHCT version, not AHC |
| Fast Switching Diode [Changzhou Starsea Elec 1N4148] | 100 | $1.34 | [LCSC](https://www.lcsc.com/product-detail/C85057.html) | Must purchase 100 in order to source the 67 diodes needed. Through-hole (DO-35) |
| SK6812 MINI-E Addressable LEDs | 70 | $4.56 | [LCSC](https://www.lcsc.com/product-detail/Light-Emitting-Diodes-LED_OPSCO-Optoelectronics-SK6812MINI-E_C5149201.html) | Must purchase 70 in order to source the 66 LEDs needed. Reverse mount |
| PCB | 1 | $19.00 | [JLCPCB](https://github.com/ReuTheCoder/bolide-65-keeb/blob/main/assets/bolide-pcb_quote.png) | Uses default PCB settings on JLCPCB |
| Womier Pudding Keycaps, Black PBT Shine Through (130 Keycap Set) | 1 | $12.61 | [Amazon](https://www.amazon.ca/Womier-Pudding-Keyboard-Switches-Keyboard-Black/dp/B0D4DN5HK1?source=ps-sl-shoppingads-lpcontext&smid=AZ1RQDED92VC&th=1) | Keycap choice is not mandatory. Can choose other keycap set; see-through recommended. Matching key sizes specified in additional notes |
| PCB Mount Screw In Stabilizers (1x 6.25u, 4x 2u) | 1 | $4.72 | [Amazon](https://www.amazon.ca/Mechanical-Keyboard-Stabilizers-Stabilizer-Backlight/dp/B0GS7HQJP6?source=ps-sl-shoppingads-lpcontext&th=1) | Stabilizer choice is not mandatory. Can choose other screw in stabilizer set. 3x 2u, 1x 6.25u |
| Glorious Fox Linear Mechanical Switches (110 pcs) | 1 | $23.09 | [Amazon](https://www.amazon.ca/Glorious-Linear-Mechanical-Switches-Keyboards/dp/B0D7QW8SQ9?th=1) | Switch choice is not mandatory. Can choose other MX-style switch |
| Waveshare RP2040 Zero | 1 | $4.20 | [RobotShop](https://ca.robotshop.com/products/rp2040-zero-pico-like-mcu-board-based-on-rp2040-mini-version-w-o-header) | Ensure you have pin headers |
| EC11 Rotary Encoder | 1 | $2.22 | [LCSC](https://www.lcsc.com/product-detail/C202365.html) | CAD files have custom knob |
| Bottom Case | 1 | $16.73 | [JLCPCB](https://github.com/ReuTheCoder/bolide-65-keeb/blob/main/assets/readme/bolide-CAD_quote.png) | Uses 9000HE Resin |
| Middle Case | 1 | $3.22 | [JLCPCB](https://github.com/ReuTheCoder/bolide-65-keeb/blob/main/assets/readme/bolide-CAD_quote.png) | Uses Translucent 8001 Resin |
| Top Plate | 1 | $4.66 | [JLCPCB](https://github.com/ReuTheCoder/bolide-65-keeb/blob/main/assets/readme/bolide-CAD_quote.png) | Uses LEDO 6060 Resin (too thin for 9600HE) |
| Rotary Encoder Knob | 1 | $0.32 | [JLCPCB](https://github.com/ReuTheCoder/bolide-65-keeb/blob/main/assets/readme/bolide-CAD_quote.png) | Uses 9600 Resin |
| M3x16mm screws | 4 | $8.69 | [Amazon](https://www.amazon.ca/uxcell-M3x16mm-Alloy-Socket-Screws/dp/B012T9FWEI) | Price is only for 12 screws; likely better price at local stores |
| M3x5mmx4mm Heatset Inserts | 4 | $7.69 | [AliExpress](https://www.aliexpress.com/item/4000232858343.html) | Price is for 100pcs |
| **Total Price (USD):** | | **$114.60** | | |

## Additonal Notes

This was my second ever PCB project and I am quite satisfied with what I could get done in a week! Below is an explanation of some technical choices I made for my PCB schematics:
- No hotswap; this keyboard is meant to have all its components hand soldered to it. It's cheaper, and I wanted to get more soldering experience through this project.
- The encoder's push button is wired through the matrix (9 columns by 8 rows) so it can be used when pushed (function not decided yet) while its rotation pins go straight to the microcontroller GPIO.
- To protect my LEDs and ensure stable signal transmission, its data chain passes through the level shifter (U2) and a 330 Ω series resistor (R1) before LED1, and every LED has its own 0.1 µF decoupling capacitor (C2-C67), with C1 for the shifter. I did not add a bulk capacitor, so brightness should be capped in firmware to stay within USB power limits.
- The PCB folder contains the design files for an alternative top plate, where instead of 3D printing the top case, you can order it as FR4 (fiberglass) through a PCB provider. It's up to personal preference, as some prefer its sound. The white version may also match better with the 9600 Resin than the LEDO 6060 Resin. The price is about $22.10 to produce however. (Pro tip: Add your own custom silkscreen to personalize your own keyboard!)

| Keycap | Size |
|---|---|
| Backspace | 2u |
| Tab, Backslash | 1.5u |
| Caps Lock, Right Shift | 1.75u |
| Enter, Left Shift | 2.25u |
| Ctrl, Menu, Left Alt | 1.25u |
| Space | 6.25u |
| All remaining keys | 1u |

Many thanks to the creators of Marbastlib and kbplacer for making my life easier during the design process. Also, I would like to say thank you so much to the organizers of [Forge](https://forge.hackclub.com/) and those at the [HackClub](https://hackclub.com/) hq for this wonderful hardware exploration opportunity!




