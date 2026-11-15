# Choc v1 socket and diode clearance

Updated: **2026-11-15**. Status: **both at-risk positions soldered on one half; multimeter check pending.**

The Lily58 Pro PCB is usable with Choc v1 hot-swap sockets. On two rows the diode pads sit right beside the Choc socket pads. Most of those near-contacts are harmless; two keys on one half can short across their diode.

## The issue

On the **number row and home row**, each diode footprint sits on the Choc side of its key, next to a Choc socket pad. On the other rows the diode sits on the MX side, far from the Choc pads.

Copper gaps measured from pad edges in [`Lily58_Pro.kicad_pcb`](../../PCB/Lily58_Pro.kicad_pcb). Solder mask is ignored, so the visible gap can look smaller.

| Keys (KiCad references) | KiCad F.Cu face | KiCad B.Cu face |
| --- | --- | --- |
| Number and home rows, all columns except the outer one (SW1–5 / D1–5, SW13–17 / D13–17) | **0.15–0.45 mm, same net** | 2.35–2.65 mm |
| Number and home rows, outer column (SW6 / D6, SW18 / D18) | 2.45 mm | **0.25 mm, different nets** |
| Top letter row, bottom row, extra inner key, thumbs (SW7–12, SW19–29) | ≈10–12 mm | ≈10–12 mm |

The PCB is reversible, so each half has its sockets on a different face. From the KiCad layout, the **left half** should have its sockets on F.Cu and the **right half** on B.Cu. Confirm this on the board with the stripe rule below; the reference labels are not printed on the PCB.

## Which near-contacts matter

- **Same net (harmless):** the pad next to the socket is the diode's **anode**, the end without the stripe. A PCB trace already joins it to that socket pad, so a solder bridge changes nothing.
- **Different nets (real short):** the pad next to the socket is the diode's **cathode**, the striped end, on the row line. A bridge bypasses the diode. The key still types, but some multi-key combinations can register keys that were not pressed (ghosting).

**Stripe rule:** look at the diode end closest to the socket pad. Unstriped end: ignore a bridge. Striped end: keep it clean and test it.

## Reports from other builders

- [Solder pads touching on Lily58 PCBs](https://www.reddit.com/r/ErgoMechKeyboards/comments/1woliwx/solder_pads_touching_on_lily58_pcbs/) (r/ErgoMechKeyboards, 2026-09): a diode pad touching a socket pad on both boards in the same spot. Top reply: "Entirely normal — they're connected in the schematic anyway." Another reply suggests soldering sockets before diodes.
- [Lily58 reversible PCB, diodes on opposing side to hotswap sockets](https://www.reddit.com/r/ErgoMechKeyboards/comments/1harj3e/): diodes fitted on the switch face. The fault turned out to be a short elsewhere; the diode direction is the same on both faces.
- [Lily58 Pro with MX and Choc sockets](https://www.reddit.com/r/MechanicalKeyboards/comments/ex1ljp/): "It's easy to avoid accidental solder bridges, and I didn't even need a flux pen."
- [kata0510/Lily58 issues](https://github.com/kata0510/Lily58/issues): no report of this clearance. [#31](https://github.com/kata0510/Lily58/issues/31) covers unrelated footprint-library problems.

## Solutions

1. **Test before changing anything.** Run the diode check in [TESTING.md](TESTING.md) on the two outer-column keys. If both pass, leave them as soldered.
2. **Clear a bridge in place.** Add flux, wipe the joint with a clean iron tip or solder wick, then retest.
3. **Move only those two diodes to the switch face** if a bridge keeps coming back.
   - **Electrically equivalent.** Each diode pad is a plated 0.4 mm through-hole pad with exposed copper on both faces. At D6 one pad's trace runs on each face, so the board already relies on those holes.
   - **Orientation.** Put the stripe at the printed bar on whichever face you use. The bar marks the same hole on both faces.
   - **The bare pad stays.** The cathode pad on the socket face remains 0.25 mm from the socket pad. Cover it with Kapton tape while soldering or reworking the socket.
   - **Tight fit.** The diode body ends about 0.2 mm outside the switch's bottom housing, estimated from the 13.8 mm Choc plate cutout. The gap under the plate should be about 2 mm against an SOD-123 height of about 1.1–1.35 mm. The exact gap is unverified, so dry-fit a switch and the plate first.
   - **Removing a fitted diode.** Flatten the leftover solder on its pads with wick before refitting it.
4. **Remaining keys:** soldering the socket before the diode is optional. It keeps the larger joint clear of the small part.

## Status log

| Date | Update |
| --- | --- |
| 2026-11-15 | Issue identified from the PCB file and builder reports. User reported both outer-column socket/diode pairs (number row and home row) soldered on the same face as their sockets. Heavy rosin flux residue covers the diodes; flux remover not yet ordered. Multimeter check pending; keep the diodes in place if it passes. |
