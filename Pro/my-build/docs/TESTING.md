# Testing procedure and results

Updated: **2026-11-15**. How each half is tested, and what has passed. Record a result only after measuring it. **— means not tested.**

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

Continuity between the controller footprint's **GND** and **VCC** holes: **no beep.** In the KiCad footprint (U1), GND is pins 3, 4 and 23 and VCC is pin 21. The BOM covers battery polarity and charging checks.

### 5. Firmware key test

Flash the half, insert the switches, then press every key in a key tester, for example `evtest` on Linux or any keyboard-tester web page. Wireless, OLED and wired-backup tests are tracked in [BUILD_BOM.md](BUILD_BOM.md).

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

| Half | Power short check (stage 4) |
| --- | --- |
| Left | — |
| Right | — |

## Issues log

| Date | Half | Key | Finding | Action | Retest |
| --- | --- | --- | --- | --- | --- |
| 2026-11-15 | Half with the at-risk keys; left/right label unconfirmed | SW6 / D6, SW18 / D18 | Socket and diode soldered on the same face. Heavy rosin residue covers the diodes. | Diode check pending; probe from the switch face. If shorted, clear the bridge or move the diode to the switch face. | — |
