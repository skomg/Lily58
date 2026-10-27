# One Lily58 Pro with Choc v1 hot-swap sockets

Prepared from repository revision `58c6497`, using the original `Pro` design.
Your choices: one complete keyboard, Choc v1 hot-swap sockets, hand soldering,
and matching top and bottom FR4 plates. The FR4 sandwich case is confirmed;
no 3D printed case is included.

**Order status (2026-10-16):** the user confirms all three batches delivered, five pieces each.
The cart prices below are historical estimates, not the final invoice.
For all current component requirements, deliveries and assembly statuses, see
[BUILD_BOM.md](BUILD_BOM.md). The component and assembly examples below describe the original wired build;
they are not a verified wireless conversion. Follow the BOM's controller and power-isolation checks.

## What the PCB order supplies

A PCB is the board containing the copper wiring. A bare PCB order supplies that
board with its holes, solder pads and printed labels. You buy and solder the
electronic components separately. Hot-swap sockets let you change switches later;
the sockets themselves still need soldering.

This PCB is reversible. Use two copies, assembling one as the left half and the
other as the right half. A batch of five boards gives you the two needed boards
and three spares. The `Pro_V2` directory describes a different design and specifies
Choc v2 support; these files come from `Pro/PCB`.

If you build two complete keyboards instead, they need four electronic PCBs,
four top plates and four bottom plates. Five of each is sufficient, with one
spare of each item. Each item is one reversible half; flip it over to use it
for the other hand. The front/back upload previews do not represent two pieces.
Two keyboards require twice the electronic components listed below.

## How the plates relate to a case

FR4 is fiberglass-reinforced epoxy, the material used for these plates and the
electronic PCB. The top and bottom plates are mechanical parts. The top plate
locates and supports the switches; the bottom plate shields the underside.
Spacers and screws join them into an open-sided sandwich case.

| Case construction | FR4 top plate | FR4 bottom plate | 3D printed parts |
| --- | --- | --- | --- |
| Standard sandwich | Keep | Keep | None required |
| Printed tray with separate switch plate | Usually keep | Usually replaced | Left and right trays |
| Printed enclosure with integrated switch plate | Replaced if designed for Choc v1 | Replaced | All parts specified by that design |

The actual case design determines which plates and fasteners are needed. A
3D printed case does not replace the electronic PCB, switches or other electronics.
Choose the case before paying to avoid buying redundant plates.

The repository contains flat case/plate drawings but no STL, STEP, 3MF or OpenSCAD
case model. A separately sourced case must match the original Lily58 Pro outline,
Choc v1 hot-swap socket clearance, switch height, controller and USB connector,
TRRS ports, and any OLEDs or covers.

[Karl's Lily58 case](https://www.thingiverse.com/thing:5422861) is one candidate:
its designer states support for Choc and Cherry hot-swap sockets and instructs
removal of the original bottom plate and spacers. It has palm rests and optional
tenting mounts. This session has not checked its CAD dimensions or physically
verified fit; the designer's compatibility statement is not a fit guarantee.

JLCPCB's [JLC3DP service](https://jlc3dp.com/) prints supplied 3D models in resin,
nylon and other plastics. Its [quote page](https://jlc3dp.com/3d-printing-quote)
accepts STL, STP, STEP, OBJ and 3MF. Gerber ZIPs cannot be used for a 3D case.
Upload each distinct left/right case part, select its required quantity and
material, then inspect the dimensions and quote. Case cost is not included in the
PCB/plate quotes. Confirm combined shipping availability in checkout.

## Files to upload

| File | What it makes | Pieces needed | Suggested batch | Thickness |
| --- | --- | ---: | ---: | ---: |
| `Lily58_Pro-JLCPCB.zip` | Electronic PCB, one reversible half | 2 | 5 | 1.6 mm |
| `Lily58_Pro_TOP-JLCPCB.zip` | Switch plate, one reversible half | 2 | 5 | 1.2 mm for Choc v1 |
| `Lily58_Pro_BOTTOM-JLCPCB.zip` | Bottom plate, one reversible half | 2 | 5 | 1.6 mm |

Each ZIP is a separate order item. Upload the ZIP intact; it contains seven
Gerber layers and separate plated and non-plated drill files. A Gerber describes
the copper, solder mask, labels or board outline; a drill file describes holes.
For a bare PCB order you do not need a bill of materials, a placement file, an
assembly service or a stencil. [JLCPCB's file requirements](https://jlcpcb.com/help/article/how-to-generate-gerber-and-drill-files-in-kicad-9)

The top plate thickness recommendation follows the Choc v1 switch's approximately
1.3 mm plate clip gap. Keep the electronic PCB at the source design's 1.6 mm.
The original plate files declare 1.6 mm; the 1.2 mm choice applies specifically to
the top switch plate. [Kailh mechanical drawing](https://raw.githubusercontent.com/keyboardio/keyswitch_documentation/master/datasheets/Kailh/CPG135001D02rev1_Brown.pdf)

### Where the thickness choices come from

All three original KiCad files have `(thickness 1.6)` on line 4:
`Pro/PCB/Lily58_Pro.kicad_pcb`, `Pro/Case/Lily58_Pro_TOP.kicad_pcb`, and
`Pro/Case/Lily58_Pro_BOTTOM.kicad_pcb`. The build guide specifies 4 mm spacers
for Choc switches but does not list PCB or plate thicknesses. These KiCad
settings establish the source configuration; they do not prove other thicknesses
are incompatible. The 1.2 mm top plate is this order's Choc-specific recommendation,
based on the switch clip geometry, rather than a thickness stated in that guide.

The bottom plate can be made at 1.2 mm using the same outline and holes. It is
mechanical protection and has no switch-clip thickness requirement, but thinner
FR4 will flex more. Check screw engagement and underside clearance for any changed
assembly. Keeping it at 1.6 mm gives a stiffer base.

The main PCB can be manufactured at 1.2 mm, but the repository does not validate
that version with the Choc sockets, switch pins and case spacing. A thinner board
also flexes more while inserting switches. Retain 1.6 mm for this first build;
changing it would need a mechanical fit check with the actual components.

## JLCPCB settings for the electronic PCB

| Setting | Selection |
| --- | --- |
| Product | Standard PCB/PCBA |
| Base material | FR-4 |
| Layers | 2 |
| Dimensions | Let the upload detect them; approximately 142.5 × 106.3 mm |
| PCB quantity | 5 individual halves |
| Product type | Industrial/Consumer electronics |
| Different designs | 1 |
| Delivery format | Single PCB |
| Thickness | 1.6 mm |
| PCB color / silkscreen | Green / white, or your preferred color |
| Material type | Standard FR4 TG135 |
| Surface finish | LeadFree HASL |
| Outer copper weight | 1 oz |
| Via covering | Tented |
| Minimum via hole size / diameter | 0.3 mm / (0.4 / 0.45 mm) |
| Outline tolerance | Regular ±0.2 mm |
| Confirm production file | Yes; check “Do not confirm automatically” in the dialog |
| Electrical test | Flying Probe Fully Test |
| Gold fingers / castellated holes / edge plating | No |
| Assembly / stencil | Off |

Use the same basic settings for the plates, changing the top plate thickness to
1.2 mm. Their dimensions may differ slightly; use each upload's detected size.
The top plate has many routed switch cutouts, so its price can differ from the
electronic PCB. JLCPCB may need to round internal cutout corners during routing;
review any proposed changes against the switch fit.

Suggested electronic-PCB remark:

> Lily58 Pro: overlapping MX/Choc socket holes are intentional. Please check hole-to-copper clearance and solder mask; send production files for approval before fabrication.

All three items were saved to the cart at C$19.54 each for five pieces,
before shipping, on September 30, 2026. The current cart has all three items
in black. Each quote includes production-file confirmation. The cart merchandise
total was C$58.62; checkout then recalculated it to C$58.72. Use the final checkout
amount. The factory can also adjust charges after reviewing the files.

Final cart check: all three items are selected, with quantity five each, FR4,
two layers, black solder mask, white silkscreen and LeadFree HASL. Thicknesses
are 1.6 mm main PCB, 1.2 mm top plate and 1.6 mm bottom plate. The saved details
for each item state that production will wait for manual confirmation.
The cart currently estimates C$66.50: C$58.62 merchandise plus C$22.09 shipping
less C$14.21 coupons. Verify the final checkout total and applicable taxes.

The top-plate remark requests preservation of all 29 switch cutouts and asks the
factory to flag routing or corner changes that could affect switch fit. The bottom
plate remark requests preservation of the outline and all five mounting holes.

After checking the preview and selections, save the item to your cart. Add any
required plates before checking out so shipping can be combined. Enter the actual
delivery address, compare shipping methods, and review the final total including
taxes and any import or brokerage charges shown by the chosen service. The bare
PCB total does not include the keyboard components below.

Checkout steps:

1. Select all three Lily58 items in the cart and click **Secure Checkout**.
2. Choose **Individual Customer**, enter your delivery details, and click **Save**.
   Click **Continue** to view shipping options.
3. Compare each shipping service's cost, delivery estimate and any listed import
   charges. Apply an eligible coupon in the payment section; the cart's coupon
   estimate may not carry into checkout automatically.
4. Review the three item names, quantities and thicknesses against the table above,
   then review the final total before submitting the order and paying.
5. After JLCPCB has reviewed the files, check its messages and production files.
   Resolve the manufacturing questions below before releasing fabrication.

## Checks performed and remaining manufacturing review

The original tracked design files are untouched. The exported electronic-PCB copy
removes 58 redundant 0.1 mm non-plated drill hits. The export script verifies that
each removed hole is completely inside a larger hole in the same footprint.
JLCPCB specifies a 0.50 mm minimum NPTH hole; the remaining smallest NPTH is 1.2 mm.
[JLCPCB capabilities](https://jlcpcb.com/capabilities/pcb-capabilities)

The exported plate copies join nearby outline endpoints, moving a point by at
most 0.023 mm, and omit 26 tiny collapsed top-plate segments. KiCad then confirms
closed outlines for all three files. The plates have zero DRC errors; their five
warnings each concern unavailable external footprint-library names. Their geometry
is embedded in the PCB files and exported Gerbers.

The electronic PCB has zero unconnected pads and a closed outline, but it does
**not** have a clean full design-rule check. The saved report contains 649 errors
and 358 warnings under KiCad 7's imported/default rules. Findings include the
combined switch-hole geometry, tight hole-to-copper distances, 0.05 mm via annular
rings, solder-mask openings, and jumper-pad geometry. Some thresholds differ from
JLCPCB's capabilities; the report still needs manufacturing review. A visible
preview or a calculated price is not factory acceptance of those findings.

Choose production-file confirmation, disable automatic confirmation, and resolve factory questions before approving
fabrication. In particular, do not silently accept changes that remove switch
holes or alter copper connections. The files have not been physically fabricated
or tested in this session. Full reports are saved beside this guide.

## Original wired component reference

These reference quantities follow the original [repository build guide](../../Pro/Doc/buildguide_en.md).
Use [BUILD_BOM.md](BUILD_BOM.md) for the selected wireless build and remaining purchases; this table does not track inventory.

| Component | Needed | What to look for |
| --- | ---: | --- |
| Choc v1 hot-swap sockets | 58; buy a few spares | Kailh PG1350 / Choc low-profile sockets |
| Switches | 58; a pack of 60 is convenient | Kailh Choc v1 / PG1350, with your preferred feel and force |
| Keycaps | 58 | Choc v1 stem compatibility; all 1U caps can work |
| Diodes | 58; buy spares | 1N4148W in SOD-123 package, as specified in the build guide |
| Microcontrollers | 2 | Pro Micro ATmega32U4, preferably a matched pair; verify compatible pinout |
| Controller headers or sockets | 2 controller sets | Compatible with the selected Pro Micro and case height |
| TRRS jacks | 2 | MJ-4PP-9 footprint compatibility |
| Reset buttons | 2 | Two-pin TVBP06 footprint, 6.5 mm pin spacing |
| Interconnect cable | 1 | 3.5 mm four-pole TRRS cable |
| USB data cable | 1 | Connector matching the chosen microcontroller |
| M2 plate spacers | 10 | 4 mm for Choc, per the build guide |
| M2 plate screws | 20 for the basic sandwich | Length matched to the spacers and plate thickness |
| Rubber feet | 8 | Four per bottom plate |
| OLED displays, optional | 2 | Compatible 4-pin I²C modules; verify pin order |
| OLED/controller covers, optional | 2 | Compatible Lily58 covers; require extra hardware |

The original guide lists 28 screws and four extra 10 mm spacers when its protective
covers are included. The two FR4 plate ZIPs do not supply those covers. Buy the
matching hardware with your chosen case or covers to avoid guessing screw lengths.

The connectors for Choc and MX switches are different. The standard Lily58 Pro
layout uses its original key spacing, so choose a keycap set that suits that layout
as well as the Choc v1 stems. Hot-swap installation does not require switch soldering.

## First soldering and assembly sequence

Have a temperature-controlled soldering iron, a small chisel tip, flux, solder,
tweezers, solder wick and a multimeter. Practice on spare material first. Use a
stable work surface and ventilation for the soldering fumes.

1. Pick two boards and label their intended front and back. Arrange them as a
   left/right pair before soldering. The reversible boards need components on
   opposite physical surfaces; assembling both the same way creates two of one hand.
2. Solder 29 diodes per half on its underside. Match the diode's cathode band to
   the cathode marking in the build-guide diagram. Check orientation before soldering.
3. Solder 29 **Choc** sockets per half on the underside, using the Choc socket pads
   shown in the guide. Secure both solder joints; support sockets from underneath
   when inserting switches so the force cannot peel a pad off the PCB.
4. Install the TRRS jack and reset button on the intended top of each half.
5. Add the controller headers/sockets. Follow the guide's pictured, outlined hole
   rows: the left and right controller connections differ. Test for a VCC-to-GND
   short before connecting USB power.
6. If fitting OLEDs, bridge only the four jumpers specified for the intended top
   surface, verify the display's pin order, and install its connector.
7. Program and test each controller/half. Use firmware for the actual controller;
   flash both halves. QMK's repository contains the Lily58 `rev1` directory and
   [current Lily58 documentation](https://github.com/qmk/qmk_firmware/tree/master/keyboards/lily58).
8. Fit the spacers, plates, switches and keycaps. Check that switch pins are straight
   before inserting them into the sockets. Attach the bottom plates and rubber feet.
9. With USB power disconnected, plug in the TRRS cable between halves, then connect
   USB and test every key. Disconnect USB before plugging or unplugging TRRS again;
   the connector can briefly short contacts during insertion.

The repository's photos are the main reference for component side, socket position,
diode orientation and controller hole selection. Its old firmware command should
be checked against the current QMK setup and the chosen controller.

## Re-exporting

`export.py` is the runnable check and export recipe. With an installed KiCad CLI:

```sh
python3 manufacturing/jlcpcb/export.py /usr/bin/kicad-cli
```

This session used KiCad 7.0.11 and temporary Ubuntu packages in `/tmp/lily58-kicad`;
it did not install KiCad system-wide. ZIP integrity, required layers, drill-file
presence and the absence of 0.1 mm drill hits are checked by the script. Full DRC
reports were generated separately with KiCad's `pcbnew` API.
