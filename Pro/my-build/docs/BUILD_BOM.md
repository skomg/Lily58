# Lily58 Pro assembly BOM and status

Updated: **2026-11-15**. This is the single record for parts, deliveries and assembly status.

Quantities cover **one complete keyboard: two halves, 58 keys**, using the original Lily58 Pro PCBs, Choc v1 hot-swap switches and the delivered FR4 sandwich plates. The build includes **wireless operation, two OLED displays with protective covers, and fully wired backup with Bluetooth disabled**. The wired backup still needs a verified design.

Track parts installed in the keyboard and its connection cables. Tools, soldering supplies, computer/BLE equipment and screws are excluded from tracking.

**— means unreported, not zero.** Ordered and Delivered record purchases and receipts; neither confirms compatibility. Mark parts Installed or Tested only after the corresponding work is confirmed.

| Status | Meaning |
| --- | --- |
| Needs selection | Required part; exact model, dimensions or variant remains undecided. |
| Planned | Specification identified; purchase or ownership unreported. |
| Needs design | Conditional parts or wiring await a verified design; quantities are not a shopping instruction. |
| Ordered / Shipped | Purchase / dispatch confirmed. |
| Delivered | Received; fitting and testing remain outstanding. |
| Installed / Tested | Fitted / verified in the assembled keyboard. |

## Boards and plates

| Part | Needed | Ordered | Delivered | Status | Specification / next check |
| --- | --- | --- | --- | --- | --- |
| Main PCB, Lily58 Pro | 2 | 5 | 5 | Delivered | Bare PCBs, 1.6 mm, two copper layers; three spares after this build. |
| Top switch plate | 2 | 5 | 5 | Delivered | Choc order: 1.2 mm FR4; three spares. |
| Bottom plate | 2 | 5 | 5 | Delivered | 1.6 mm FR4; three spares. |

All three batches were ordered in black with white silkscreen and LeadFree HASL. Each piece is one reversible half; arrange two as a left/right pair before assembly. Delivery does not confirm physical fit. Manufacturing checks and their limits are recorded in the [review](prod_files/REVIEW.md); the main PCB did not pass a clean full DRC.

## Keys and controllers

| Part | Needed | Ordered | Delivered | Status | Specification / next check |
| --- | --- | --- | --- | --- | --- |
| Choc v1 switches | 58 | 90 | 90 | Delivered | Kailh Choc 1350, **Kh-1350D02**, previously selected **brown** variant. 32 spares. Inspect the received variant and fit. Choc v2 is a different system. |
| Choc v1 hot-swap sockets | 58 | 110 | 110 | Delivered | Kailh listing: **CPG151101S11 For Outemu Cherry MX Switches**; user previously confirmed **Type B for low-profile chocolate (Choc)**. 52 spares. The generic listing title does not describe the selected variant; verify the actual footprint. Use the Choc pads at SW1–SW29 per half. |
| Choc v1 keycaps | 58 usable caps | — | — | Needs selection | Choc v1 two-slot stems. All 1U is a supported option; verify legends, layout coverage and physical fit. Ordinary MX-stem caps do not fit. |
| Switching diodes | 58 | 500 | 500 | Delivered | **1N4148W**; corrected quantity confirmed by the user. 442 spares. Verify **SOD-123** package: the earlier listing also called it 1206. Fit 29 per half at D1–D29, matching the cathode marking. |
| Wireless controllers | 2 identical | 2 | 2 | Delivered | **nRF52840 nice!nano V2.0-compatible Pro Micro boards**, previously selected with **pins on three sides**. User confirms labelled **B+/B− pads**, first positions from the USB-C end. Verify the remaining pinout, charger and ZMK target; the listing does not certify original nice!nano specifications or fully wired backup support. |
| Removable controller socket/pin kits | 2 complete kits | — | — | Needs selection | Four 1×12 socket strips and 48 matching pins total, 2.54 mm pitch, for U1 on each half. Check supplied controller pins before buying extras. PCB drills are nominally **0.8128 mm**; pitch alone does not establish fit. Choose height with batteries, OLEDs and covers together. |
| Reset buttons | 2 | 100 | 100 | Delivered | **Two-pin DIP tact switches, 3×6×5 mm**, white buttons. 98 spares. Verify normally open operation, TVBP06/RSW1 footprint with **6.5 mm pin-centre spacing**, 1.3 mm drills and cover clearance; body dimensions alone do not confirm fit. |

Controller installation rows differ between the left and right halves. Follow the build guide's outlined rows and verify orientation and power connections before fitting either controller. The sockets require soldering; the switches plug into them. Support sockets from below when inserting switches and check that switch pins are straight.

## Wireless power and internal wiring

| Part | Needed | Ordered | Delivered | Status | Specification / next check |
| --- | --- | --- | --- | --- | --- |
| Rechargeable batteries | 2 | 4 | — | Ordered | Ordered item #1: **4PCS/Lot 3.7V 110mAh 301230 Lithium Polymer Rechargeable Battery For Nice Nano' or Wireless Keyboard MP4 MP5 GPS PSP Bluetooth**, from [this listing](https://www.aliexpress.com/item/1005010032194346.html). One four-piece lot recorded; two needed, two spares after this build. Plug/wire-only variant and delivery remain unreported. Confirm protection circuit, maximum charging current against the actual controller, polarity and complete pack dimensions/clearance. Include OLED consumption in runtime estimates. Seller-specific specifications/photos could not be verified. |
| Battery disconnect/power switches (optional) | 2 if physical battery disconnect is chosen | — | — | Needs selection | A physical switch is optional; direct battery wiring can use firmware low-power states, which do not disconnect the battery. Recommended switch candidate: **C&K JS102011CQN**, maintained SPDT slide switch, three through-hole terminals, **0.3 A at 6 V DC**; see [manufacturer datasheet](https://www.ckswitches.com/media/1422/js.pdf). User selection and mechanical mounting remain pending. Use common plus one switched terminal in the battery-positive lead to controller B+; leave the third terminal unconnected and insulated. One per half, mounted separately because the original PCB has no power-switch footprint. Verify the actual charger current is within the switch and battery ratings. |
| Battery connector/pigtail pairs (optional) | 0 for direct wiring; 2 matched sets if removable | — | — | Needs design | A connector is **not electrically required**: battery factory-attached leads can be soldered through the power switch to controller B+/B−. A connector makes battery removal/replacement easier. If chosen, use matching **two-pin JST-PH, 2.0 mm pitch** parts; genuine **PHR-2-BK** is a black two-position PH housing. Seller variant equivalence remains unverified. Do not duplicate plugs supplied with the cells; verify measured polarity. |
| Insulated hookup wire | About 1–2 m total | — | — | Planned | Flexible stranded electronics wire, approximately 28 AWG for short low-current leads. Final gauge and length follow the harness and controller charge current. |
| Heat-shrink / terminal insulation | Enough for both harnesses | — | — | Planned | Insulate exposed joints and provide strain relief. |
| Battery insulation and retention | 2 sets | — | — | Needs selection | Nonconductive barrier and secure, noncompressing mount for each cell, clear of sharp solder pins and hardware. Measure the assembled stack before selecting cells. |

Use the actual controller manufacturer's battery instructions. On nice!nano, B+/B− pads are outside the normal 12-pin socket rows. Verify the clone's charging circuit before attaching cells; do not add another charger in parallel. See [nice!nano installation](https://nicekeyboards.com/docs/nice-nano/getting-started/) and [mounting/battery guidance](https://nicekeyboards.com/docs/nice-nano/).

### Battery connector placement and wiring

The original Lily58 Pro [schematic](../../Pro/PCB/Lily58_Pro.sch) and [PCB](../../Pro/PCB/Lily58_Pro.kicad_pcb) have **no dedicated battery connector footprint**. J1 is for LEDs, J2 is TRRS, and J3 is OLED. A battery connector cannot be installed in one of those locations as a substitute. The nRF52840 controller is a separate board; its battery-pad layout is not defined by the Lily58 files.

The user confirms that the received controllers have B+/B− labels at the first positions from the USB-C end. A battery with factory-attached insulated leads can be wired directly. The power switch in the positive lead below is optional; omit it for permanent direct wiring:

```text
Battery + --> power switch --> controller B+
Battery - -----------------> controller B-
```

A matching connector pair may be inserted in the two battery leads for easy removal; it is optional. With the switch shown above off, the battery is also disconnected from the onboard charger.

Without a switch or removable connector, the battery remains electrically connected. ZMK idle, deep sleep and soft off reduce consumption but do not physically disconnect it; deep sleep and soft off require configuration. Soft off can be woken with the reset button on each half. See [ZMK low-power states](https://zmk.dev/docs/features/low-power-states) and [power configuration](https://zmk.dev/docs/config/power). Use a cell with verified protection against excessive discharge; do not assume the clone's charger includes that function or deliberately drain the cell completely. See [battery protection guidance](https://learn.adafruit.com/li-ion-and-lipoly-batteries/protection-circuitry).

Solder with USB disconnected and any power switch off. Unplug the cell first if using a connector. Factory-attached leads on a wire-only battery remain live: insulate the unused lead and work on one lead at a time, preventing the leads from touching. Solder the supplied wires to the switch/controller, not directly to the pouch cell or its tabs. Insulate joints, provide strain relief and verify polarity before completing the circuit. Use the B+/B− labels rather than assumed left/right positions. Do not feed the cell into the Lily58 VCC rail.

For a genuine nice!nano, B+/B− are the extra top pads, one on each side, outside the normal 12-pin rows. The clone's charging current still requires confirmation against the selected cell's maximum charge current. A fixed PCB-mounted connector would need a compatible battery backpack or separate breakout; there is no stock battery-socket location on this Lily58 Pro. See the [controller pinout](https://nicekeyboards.com/docs/nice-nano/pinout-schematic/) and [JST PHR-2-BK identification](https://jst.de/produkt/3508/680859-00).

## OLED displays and covers

These are required for this build.

| Part | Needed | Ordered | Delivered | Status | Specification / next check |
| --- | --- | --- | --- | --- | --- |
| OLED display modules | 2 | 2 + 10 reported; item #8 matching pending | — | Ordered | Ordered descriptions for #7 and #8 both read **0.91 Inch 128x32 IIC I2C White / Blue OLED LCD Display DIY Module SSD1306 Driver IC DC 3.3V 5V for Arduino**: #7 is **2 pcs**, #8 is **10 pcs**. This would be 12 modules if both entries are OLEDs; confirm whether #8 is a separate OLED order or a copied description for another part. Selected white/blue colour is unreported. Verify actual pin order, dimensions, I²C address and operation/signal levels at **3.3 V** in both operating modes. |
| OLED pin headers | 2 × 1×4 | — | — | Needs selection | 2.54 mm pitch; may be supplied with the ordered displays, but inclusion is unconfirmed. The ordered female sockets below do not supply male headers. Match pin/socket dimensions and installed height. |
| OLED removable sockets | 2 × 1×4 | 30 | — | Ordered | Ordered item #3: **2.54mm Single Double Row Female Socket**, selected **1x4P**, **30 pcs**. Recorded as single-row 1×4 female OLED sockets; 28 spares after this build if compatible. Match J3 and the display headers; check pin fit, installed height, controller/battery clearance below and cover clearance above. |
| OLED/controller protective covers | 2, left/right-compatible | — | — | Needs selection | Original Lily58 Pro mounting pattern, typically acrylic. Delivered FR4 plates do **not** include these. Check USB, power-switch and antenna clearance. |
| Cover spacers | 4 | Quantity unreported | — | Ordered | Ordered item #2: **Female Hex Nylon Standoff Metric Thread Hexagonal Spacers Spacing Screw M2 Black White Motherboard Rack Column**, selected **M2, 10 mm body height**. Quantity and selected colour are unreported; verify thread/end style and dimensions. Matched to the cover-spacer requirement, separate from the delivered 4 mm plate spacers. Final height must clear the controller/socket/battery/OLED stack; do not assume 10 mm is sufficient. |
| External I²C pull-up resistors | Conditional: 0–4 total | — | — | Needs design | Inspect the modules' onboard pull-ups first. R1/R2 exist per half; choose value/package only if needed for the verified 3.3 V bus. Do not fit duplicates automatically. |

Bridge only the correct four OLED routing jumpers for each PCB's intended top face, then verify GND/VCC/SCL/SDA continuity to the actual module before connecting it. No plug-in jumper blocks are required. Enable display support for **both** halves and test their central/peripheral contents, blanking, sleep and wake. The [Lily58 shield definition](https://github.com/zmkfirmware/zmk/blob/main/app/boards/shields/lily58/lily58.dtsi), [display settings](https://zmk.dev/docs/config/displays) and [display support notes](https://zmk.dev/docs/features/displays) are references for firmware verification.

## Case parts

| Part | Needed | Ordered | Delivered | Status | Specification / next check |
| --- | --- | --- | --- | --- | --- |
| Plate spacers | 10 | 50 | 50 | Delivered | Black nylon hex **M2 female-to-female, 4 mm body height**, one confirmed 50-piece pack. 40 spares. Five per half; verify the hex body fits the main PCB's nominal **4.7 mm** mounting holes and clears batteries. Plate mounting holes are nominally 2.4 mm. Physical fit remains untested. |
| Adhesive rubber feet | 8 | 100 pcs + 5 pairs reported; item #6 matching pending | — | Ordered | Ordered descriptions for #5 and #6 both read **1000/100pcs Self-Adhesive Clear Door Stop Rubber Damper Buffer Cabinet Bumpers Silicone Furniture Dots Cushion Protective Pads**: #5 is **100 pcs**, #6 is **5 pairs**. Kept as separate reported order lines; confirm whether #6 is another bumper order or a copied description for a different part before combining quantities. Candidate feet: four per bottom plate. Verify pad diameter, height, adhesion and clearance for underside hardware. |

Plate spacers and cover spacers are separate requirements: **10 + 4**. Final mechanical fit depends on the complete controller/battery/display stack.

## USB connections and fully wired backup

| Part | Needed | Ordered | Delivered | Status | Specification / next check |
| --- | --- | --- | --- | --- | --- |
| Host/charging USB cables | 2 | — | — | Needs selection | Data-capable cables with controller-end connectors verified against the received boards and host ends matched to existing ports. Either cable should flash/test either half. Two cables alone do not provide wired inter-half communication. |
| Wired inter-half cable | 1 | 1 | — | Ordered | Ordered item #4: **3.5mm Thin Line Audio Cable Straight to Curved Connector for Portable Audio Equipment**, selected **Curved to Curved Connection**, **1 pc**. Plug pole/conductor count, length and contact mapping are unreported. Verify four-pole TRRS and straight-through electrical continuity for the stock wired reference; right-angle plug shape does not establish wiring. The fully wired backup design remains unresolved, and this cable is **not approved for connecting the battery-powered halves**. |
| Stock TRRS jacks | 2, conditional on backup design | 10 | 10 | Delivered | Received **PJ-320A**, four-pin 3.5 mm audio jacks. Eight spares if two are used. Verify through-hole mounting, locating posts, dimensions and contact mapping against **MJ-4PP-9 at J2**. Leave unused for the normal BLE split until the backup design is verified. |
| Backup-specific connectors, harness and power isolation | 1 complete two-half set; exact parts TBD | — | — | Needs design | Verify data pin allocation, connector pinout and separation of the two controllers' power systems before selecting parts. The internal hookup wire above does not resolve this design. |

**Fully wired backup remains required and unresolved.** USB to the computer while the halves communicate over BLE does not meet the requirement. The stock PCB and received controllers are not a verified dual-mode design. Resolve a compatible modification or manual wired conversion and its exact parts first; an extra controller pair is conditional on that choice.

Do not directly join independent battery or regulator outputs. For any approved TRRS arrangement, disconnect **both USB and battery power on both halves** before inserting or removing the cable. See the [nice!nano USB/TRRS guidance](https://nicekeyboards.com/docs/nice-nano/faq/) and [ZMK split transports](https://zmk.dev/docs/features/split-keyboards).

## Assembly status

No parts have been reported Tested. The user reported the two at-risk outer-column socket/diode pairs (number row and home row) soldered on one half; see [CHOC_DIODE_CLEARANCE.md](CHOC_DIODE_CLEARANCE.md). Test procedure and per-key results: [TESTING.md](TESTING.md).

- [ ] Confirm the ordered 10 mm spacer quantity and repeated bumper/OLED descriptions; verify ordered parts and any included male OLED headers.
- [ ] Select remaining keycaps, controller connections, power wiring and covers; verify the ordered batteries, OLEDs, sockets and cover spacers fit the full stack.
- [ ] Resolve the fully wired backup design and finalize its exact parts and wiring.
- [ ] Inspect the delivered parts and left/right PCB orientation; confirm controller USB operation, battery polarity/current ratings and absence of power shorts before attaching cells.
- [ ] Install and inspect diodes, hot-swap sockets, reset buttons and controller connections; test for power shorts.
- [ ] Install OLED connectors, verify routing jumpers, and configure matching left/right ZMK builds for the actual controllers with both displays enabled.
- [ ] Test all 58 keys, wireless operation, charging, USB output selection and both displays, including sleep/wake.
- [ ] Implement the verified wired backup and test **all 58 keys and both displays with Bluetooth disabled**.
- [ ] Fit plates, covers, keycaps and feet; update each part's Installed/Tested status after verification.

## Confirmed updates

| Date | Update |
| --- | --- |
| 2026-10-16 | User confirmed delivery of all three JLCPCB batches, five pieces each. Build scope includes wireless operation, two OLEDs/covers and fully wired backup with Bluetooth off. |
| 2026-10-16 | Selected **90 Kh-1350D02 brown switches**, **110 Type B Choc sockets** and **two nRF52840 boards with pins on three sides**; purchases recorded. |
| 2026-10-26 | Received **90 switches, 110 sockets, two controllers, 100 reset buttons, 10 PJ-320A jacks, 500 1N4148W diodes and 50 M2 plate spacers**. None marked Installed or Tested. |
| 2026-10-26 | User confirmed **500 diodes** replaces the earlier 100-piece record and **50 spacers with 4 mm body height** corrects the initial 25 mm / 10-piece description. No duplicate quantities counted. |
| 2026-10-26 | Consolidated the BOM and component status into this document. Removed the separate tracker and excluded tools, soldering supplies, host equipment and screw tracking. Current wireless/display requirements supersede the earlier ATmega32U4 wired baseline. |
| 2026-10-26 | User selected **3.7 V, 110 mAh, 301230 rechargeable LiPo batteries** and supplied the seller listing. Status is Planned, not Ordered or Delivered; two cells are required. Plug variant remains undecided. Documented the original PCB's lack of a battery connector footprint and the controller B+/B− pigtail approach; actual clone pads, charging current, battery protection and seller connector photos remain unverified. |
| 2026-10-26 | User confirmed labelled **B+/B− pads at the USB-C end** of the received controllers. Clarified that a battery with factory-attached wires can be soldered directly through a power switch; connectors are optional for serviceability. Connection method remains undecided; no new purchases or deliveries assumed. |
| 2026-10-27 | User reported new orders: **#1 four 3.7 V / 110 mAh / 301230 LiPo batteries (one four-piece lot); #2 M2 nylon hex standoffs, 10 mm height, quantity unreported; #3 thirty 2.54 mm 1×4 female sockets; #4 one 3.5 mm curved-to-curved audio cable; #5 one hundred adhesive bumper pads; #6 five pairs under the same bumper description; #7 two SSD1306 0.91-inch 128×32 I²C OLED modules; #8 ten pieces under the same OLED description**. Items #6/#8 retained separately pending description confirmation; no duplicate quantities discarded or silently combined. All are Ordered, with delivery unreported. Cable wiring and physical compatibility remain unverified. |
| 2026-11-15 | Found that on the number and home rows the diode pads sit beside the Choc socket pads. Most near-contacts are the same net and harmless; the outer-column keys on one half can short across their diode. User reported both at-risk pairs soldered on one half, with heavy rosin residue. Multimeter check pending. Added [CHOC_DIODE_CLEARANCE.md](CHOC_DIODE_CLEARANCE.md) and [TESTING.md](TESTING.md). |

## Assembly references

- [Original English build guide](../../Pro/Doc/buildguide_en.md): component placement and left/right assembly pictures. Use the controller and wiring checks above for this wireless build.
- [Main PCB](../../Pro/PCB/Lily58_Pro.kicad_pcb), [schematic](../../Pro/PCB/Lily58_Pro.sch) and [footprint library](../../Pro/PCB/Lily58_Pro-footprint.pretty/): electrical connections and dimensions. Embedded PCB footprints are authoritative if the library differs.
- [Top plate](../../Pro/Case/Lily58_Pro_TOP.kicad_pcb) and [bottom plate](../../Pro/Case/Lily58_Pro_BOTTOM.kicad_pcb): original plate geometry.
- [Choc socket/diode clearance](CHOC_DIODE_CLEARANCE.md): near-contacts on the number and home rows, and fixes.
- [Testing procedure and results](TESTING.md): multimeter stages and per-key results.
- [Order/export guide](ORDER_GUIDE.md) and [manufacturing review](prod_files/REVIEW.md): fabrication records and validation limits.

Exact product compatibility, battery runtime and physical assembly fit remain unverified.
