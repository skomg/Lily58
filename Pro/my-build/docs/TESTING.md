# Testing procedure and results

Updated: **2026-11-18**. How each half is tested, and what has passed. Record a result only after measuring it. **— means not tested.**

## Tools

- Multimeter with **diode mode** and **continuity mode**. Test diodes in diode mode only; some meters beep on a healthy diode in continuity mode.
- Isopropyl alcohol (IPA), ideally 90% or stronger, and an old toothbrush for flux residue. Do not use water.

## Flux residue

Dried rosin flux is an insulator. It cannot cause a short, and any reading near 0 Ω or 0 V means metal is touching. Residue can stop a probe reaching copper and give a false open reading. Probe the pad behind the part on the other face, scratch through the residue, or clean with IPA. Clean before final assembly even with no-clean flux.

## Test stages

Run the stages in order on each half. Remove switches, or at least do not press them, until stage 5.

### 1. Visual check

Use a magnifier or phone macro photo. Look for solder bridges, dull or balled joints, sockets not sitting flat, and each diode stripe matching its printed bar.

### 2. Diode check, per key

Each diode pad continues through a plated hole to a bare pad on the other face, which is usually free of flux. Probe either face.

| Red probe | Black probe | Expected |
| --- | --- | --- |
| Unstriped end | Striped end | **0.5–0.7 V** |
| Striped end | Unstriped end | **OL** |

Measure a key with comfortable clearance first as a reference. On the face without the diode, the printed bar marks the striped end.

- **About 0.00 V or a beep both ways:** shorted. Look for a bridge from the striped end to the socket pad; see [CHOC_DIODE_CLEARANCE.md](CHOC_DIODE_CLEARANCE.md).
- **OL both ways:** open. Either the probe is not on copper, a joint is bad, or the diode is damaged.

### 3. Socket joint check, per key (continuity mode)

The socket tab that beeps to the diode's unstriped end is the **diode-side tab**; the other is the **column tab**.

1. **Diode-side tab ↔ diode unstriped end:** beep. This proves the diode-side joint.
2. **Column tab ↔ column tab of another soldered key in the same matrix column:** beep. This proves the column joint. Matrix columns are listed in the results table.
3. **Column tab ↔ diode-side tab, no switch:** no beep. A beep means a short across the socket, and the key will read as permanently pressed.

### 4. Power short check, before fitting the controller and before any battery

Continuity between the controller footprint's **GND** and **VCC** holes: **no beep.** In the KiCad footprint (U1), GND is pins 3, 4 and 23 and VCC is pin 21. Battery checks are stage 6.

### 5. Firmware key test

Flash the half, insert the switches, then press every key in a key tester, for example `evtest` on Linux or any keyboard-tester web page. Wireless, OLED and wired-backup tests are tracked in [BUILD_BOM.md](BUILD_BOM.md).

### 6. Battery, after stage 5 passes on USB alone

Wire the cell's red (+) lead to the controller's **B+** pad and black (−) to **B−**. Never wire it to VCC (U1 pin 21), which is the controller's 3.3 V output to the OLED. RAW (U1 pin 24) is unconnected on this PCB. Solder with USB unplugged and any power switch off. The cell's leads are live: solder one at a time and keep the other insulated. **Never insert the TRRS cable while a battery is connected.**

Before soldering:

| Check | Mode | Expected |
| --- | --- | --- |
| Cell, red probe on red lead | DC volts | **3.0–4.2 V**. Negative means the lead colours are swapped. Below 3.0 V, do not use the cell. |
| Controller B− ↔ a GND pin | Continuity | Beep |
| Controller B+ ↔ B− | Continuity | No beep |

After soldering, with USB unplugged:

1. **B+ ↔ B−** on the controller reads the cell voltage. On these clones the red charge LED blinks twice as the cell is attached, then stays off without USB. That is normal and is not a running indicator.
2. **On battery:** the left half pairs and types over Bluetooth, and the right half connects to the left.
3. **Charging:** plug in USB. The charge LED lights (red on these clones, orange on a genuine nice!nano) and the cell voltage climbs toward 4.2 V. A genuine nice!nano charges at 100 mA, about 0.9C for a 110 mAh cell. The clone's current is unverified, so check the cell on its first charge: warm is fine, hot means unplug.
4. **Level:** battery percentage appears in `upower -d`, in `bluetoothctl info <MAC>` and on the OLED. The right half's level also needs `CONFIG_ZMK_SPLIT_BLE_CENTRAL_BATTERY_LEVEL_FETCHING=y` and `CONFIG_ZMK_SPLIT_BLE_CENTRAL_BATTERY_LEVEL_PROXY=y`. A level stuck at 0 or never changing means the clone senses the battery differently from the genuine board, which uses P0.04.

## Results

Each half's cell reads **diode / sockets / keypress**, for stages 2, 3 and 5. Use ✓ for pass and ✗ for fail, and log every ✗ in the issues table. Columns run outer, pinky, ring, middle, index, inner.

| Key | Position | Matrix | Clearance note | Left half | Right half |
| --- | --- | --- | --- | --- | --- |
| SW1 / D1 | Number row, inner | row0 col5 | Close, same net | — / — / — | — / — / — |
| SW2 / D2 | Number row, index | row0 col4 | Close, same net | — / — / — | — / — / — |
| SW3 / D3 | Number row, middle | row0 col3 | Close, same net | — / — / — | — / — / — |
| SW4 / D4 | Number row, ring | row0 col2 | Close, same net | — / — / — | — / — / — |
| SW5 / D5 | Number row, pinky | row0 col1 | Close, same net | — / — / — | — / — / — |
| SW6 / D6 | Number row, outer | row0 col0 | **At risk: 0.25 mm, different nets** | — / — / — | — / — / — |
| SW7 / D7 | Top row, inner | row1 col5 | | — / — / — | — / — / — |
| SW8 / D8 | Top row, index | row1 col4 | | — / — / — | — / — / — |
| SW9 / D9 | Top row, middle | row1 col3 | | — / — / — | — / — / — |
| SW10 / D10 | Top row, ring | row1 col2 | | — / — / — | — / — / — |
| SW11 / D11 | Top row, pinky | row1 col1 | | — / — / — | — / — / — |
| SW12 / D12 | Top row, outer | row1 col0 | | — / — / — | — / — / — |
| SW13 / D13 | Home row, inner | row2 col5 | Close, same net | — / — / — | — / — / — |
| SW14 / D14 | Home row, index | row2 col4 | Close, same net | — / — / — | — / — / — |
| SW15 / D15 | Home row, middle | row2 col3 | Close, same net | — / — / — | — / — / — |
| SW16 / D16 | Home row, ring | row2 col2 | Close, same net | — / — / — | — / — / — |
| SW17 / D17 | Home row, pinky | row2 col1 | Close, same net | — / — / — | — / — / — |
| SW18 / D18 | Home row, outer | row2 col0 | **At risk: 0.25 mm, different nets** | — / — / — | — / — / — |
| SW19 / D19 | Bottom row, inner | row3 col5 | | — / — / — | — / — / — |
| SW20 / D20 | Bottom row, index | row3 col4 | | — / — / — | — / — / — |
| SW21 / D21 | Bottom row, middle | row3 col3 | | — / — / — | — / — / — |
| SW22 / D22 | Bottom row, ring | row3 col2 | | — / — / — | — / — / — |
| SW23 / D23 | Bottom row, pinky | row3 col1 | | — / — / — | — / — / — |
| SW24 / D24 | Bottom row, outer | row3 col0 | | — / — / — | — / — / — |
| SW25 / D25 | Extra inner key, between home and bottom rows | row4 col5 | | — / — / — | — / — / — |
| SW26 / D26 | Thumb 1, innermost, angled | row4 col4 | | — / — / — | — / — / — |
| SW27 / D27 | Thumb 2 | row4 col3 | | — / — / — | — / — / — |
| SW28 / D28 | Thumb 3 | row4 col2 | | — / — / — | — / — / — |
| SW29 / D29 | Thumb 4, outermost | row4 col1 | | — / — / — | — / — / — |

"Close, same net" applies only on the half whose sockets are on KiCad F.Cu, and "at risk" only on the half whose sockets are on B.Cu. See [CHOC_DIODE_CLEARANCE.md](CHOC_DIODE_CLEARANCE.md).

The battery cell reads **cell / on battery / charging / level**: the pre-solder checks, then steps 2, 3 and 4 of stage 6.

| Half | Power short check (stage 4) | Battery (stage 6) |
| --- | --- | --- |
| Left | — | — / — / — / — |
| Right | — | — / — / — / — |

### Controller bench tests, off the PCB

Each controller is tested before fitting by shorting a row pin to a column pin with a wire instead of pressing a switch, watching `evtest`. These results do not replace stages 5 and 6 on the assembled halves. Controller 1 runs the left firmware; mark it L.

| Controller | Firmware | Keys over USB | Keys over Bluetooth | On battery | Charging |
| --- | --- | --- | --- | --- | --- |
| 1 | ZMK v0.3 `lily58_left`, `nice_nano_v2` target | ✓ | ✓ on power-bank USB power | Runs; typing untested | — |
| 2 | Not flashed | — | — | — | — |

Controller 1, 2026-11-18:

- **Keys:** shorting P0.24 (row 0) to the column pins typed Esc and number keys.
- **Bluetooth:** paired, bonded and trusted with the Linux host. Powered from a 5 V power bank with no USB data, it reconnected and typed.
- **Battery:** a 3.7 V 110 mAh cell was wired temporarily through a breadboard to B+/B−, and measured 3.9 V at the controller. With USB unplugged it connected over Bluetooth and ZMK reported 66%, which matches 3.9 V, so the clone's battery sensing works.

## Issues log

| Date | Half | Key | Finding | Action | Retest |
| --- | --- | --- | --- | --- | --- |
| 2026-11-15 | Half with the at-risk keys; left/right label unconfirmed | SW6 / D6, SW18 / D18 | Socket and diode soldered on the same face. Heavy rosin residue covers the diodes. | Diode check pending; probe from the switch face. If shorted, clear the bridge or move the diode to the switch face. | — |
