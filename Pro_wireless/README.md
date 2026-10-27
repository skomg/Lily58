# Lily58 Pro wireless power research

Research date: **2026-10-27**.

This document records the feasibility of adding a battery connector and a physical
on/off switch to the original Lily58 Pro. **Lily58 Pro v1.2** is a proposed revision
name, not an upstream release. No PCB modification or prototype has been made.

## Conclusion

Adding a battery connector and an on/off switch is a small electrical revision.
Making the components fit both sides of the reversible PCB while preserving
existing plates and covers is the more substantial work.

A focused revision of the original Pro PCB is reasonable. Allium58 provides an
MIT-licensed reference for the power circuit. Typeractive's complete wireless PCB
includes additional changes and should not be treated as interchangeable with
the original Lily58 Pro.

## Existing PCB

The inspected files are the [manufacturing PCB](../manufacturing/jlcpcb/Lily58_Pro.kicad_pcb),
the [original PCB](../Pro/PCB/Lily58_Pro.kicad_pcb), and the
[original schematic](../Pro/PCB/Lily58_Pro.sch). The screenshot supplied for this
research shows the battery connector, reset button, power switch, and controller
on a Typeractive Lily58 assembly.

The original Pro design has:

| Reference | Function |
| --- | --- |
| RSW1 | Momentary reset button connecting RESET to GND |
| J1 | LED connections |
| J2 | TRRS jack |
| J3 | OLED connector |
| U1 | Pro Micro-compatible controller footprint, including RAW at pad 24 |

There is no battery connector or battery-disconnect circuit. The reset button
restarts the controller while leaving its power connected; it cannot serve as an
on/off switch.

## What Typeractive changes

Typeractive documents the following changes to the Lily58:

- A physical power switch.
- A JST battery connector.
- Direct nice!view support without a bodge wire.
- Preassembled hotswap sockets, diodes, reset button, power switch, and battery connector.
- Tighter Choc spacing on its Choc PCB.

The spacing change means the Typeractive Choc PCB should not be assumed to fit
original Lily58 Pro plates and cases.

Source: [Typeractive Lily58 Wireless — Getting Started](https://docs.typeractive.xyz/build-guides/lily58-wireless/getting-started).

Public firmware and documentation were found in
[Typeractive's repositories](https://github.com/typeractivexyz), but no editable PCB
design was found there during this research. The original Lily58's open-source
status does not establish availability of a vendor's modified PCB source.

## Minimal power circuit

For a controller with a verified nice!nano v2-compatible power pinout:

```text
Battery + --> connector --> maintained slide switch --> controller BAT+
Battery - --> connector -----------------------------> controller GND
```

Genuine nice!nano v2 exposes BAT+ at the standard Pro Micro **RAW** position, in
addition to its dedicated battery-positive pad. The existing Lily58 Pro
controller footprint includes RAW as pad 24. A revision targeting this pinout can
therefore route the switched battery supply through the existing controller
socket connections without adding controller pins.

The nice!nano already contains the charger and power circuitry. The battery must
not be connected to the Lily58 VCC rail as a substitute for BAT+/RAW.

**The received controller clones still need verification:** confirm RAW-to-B+
continuity, battery ground, charging current, and compatibility with the selected
cell before adopting this circuit. Genuine nice!nano specifications do not certify
the clones.

With the switch in the battery-positive lead, switching off disconnects the
battery from the charger as well. USB can still power the controller. This switch
is a battery disconnect, not a disconnect for every possible power source.

Sources:

- [nice!nano pinout and schematic](https://nicekeyboards.com/docs/nice-nano/pinout-schematic/).
- [nice!nano mounting and battery guidance](https://nicekeyboards.com/docs/nice-nano/).
- [Existing build BOM and battery-wiring notes](../manufacturing/jlcpcb/BUILD_BOM.md).

## Open-source references

| Design | Power features and license | Relevance and limits |
| --- | --- | --- |
| [Allium58](https://github.com/beekeeb/Allium58) | Battery connector and slide switch; MIT licensed | Best main-PCB reference found. Published KiCad files currently cover the Gateron low-profile version; the README lists MX/Choc as WIP. |
| [sprod's Lily58 batteryboard](https://github.com/sprod/lily58_batteryboard) | Removable battery connection and switch; MIT licensed | Separate adapter board for an existing Lily58, rather than a replacement main PCB. Requires wiring, footprint, and mechanical verification. |
| [Lily58 Glow Enc Wireless](https://github.com/iasoren/Lily58-Glow-Enc-Wireless) | Battery switch and connection pads; MIT licensed | Experimental redesign explicitly marked WIP. Less suitable as a manufacturing starting point; not a confirmed connector-and-switch drop-in replacement. |

Allium58's actual published PCB connections were inspected: the battery connector
feeds a slide switch, which feeds the controller's RAW pin. This is directly
relevant to the proposed revision. Its
[license](https://github.com/beekeeb/Allium58/blob/main/LICENSE) includes the original
Lily58 attribution. Its published left and right GLP layouts are references for
the circuit, not a verified replacement for this build's reversible Choc v1 PCB.

**Aurora Lily58 is a separate licensing case.** It supports a battery switch and
has published schematics, but splitkb explicitly states that its modified design
is not open source. It should not be listed as an openly licensed PCB source for
this revision. See [Aurora Lily58 attribution](https://docs.splitkb.com/product-guides/aurora-series/attribution/aurora-lily58).

A clearly licensed, proven replacement preserving the original reversible Choc v1
PCB and adding only these two features was not confirmed during this research.

## Suggested scope for a proposed v1.2

1. Preserve the original switch positions, mounting holes, outline, and reversible assembly.
2. Add one specified battery connector and maintained slide-switch footprint, with correct polarity and assembly markings for both faces.
3. Route switched battery positive to the verified controller RAW/BAT+ connection and battery negative to GND.
4. Check connector access, switch travel, battery clearance, OLED covers, and controller removal on both halves.
5. Update the schematic, footprints, BOM, assembly instructions, and Gerbers; manufacture and test a prototype before proposing it upstream.

This should remain a two-layer PCB. The passive power additions should require no
firmware changes if the controller, matrix wiring, and existing firmware
configuration stay the same. Adding nice!view support or changing Choc spacing
would expand the scope.

The existing board's [saved DRC report](../manufacturing/jlcpcb/Lily58_Pro-drc.txt)
is not clean. Review inherited issues when validating the revision so that new
faults are not hidden among existing reports.

## Fully wired backup is a separate requirement

The [current build BOM](../manufacturing/jlcpcb/BUILD_BOM.md) also calls for fully
wired backup with Bluetooth disabled. Adding a battery switch does not establish
safe inter-half power sharing or wired communication.

ZMK documents experimental full-duplex wired split support requiring two data
wires, and warns against inserting or removing TRRS/TRS cables while either
controller is powered by USB or battery. A verified wired-backup design needs its
own electrical and firmware work.

Source: [ZMK split keyboard documentation](https://zmk.dev/docs/features/split-keyboards).

## Validation limits

This is a source-based feasibility review, not a fabrication-ready design.
Physical fit, connector polarity, clone pinout, charging behavior, and prototype
operation remain unverified. Existing manufactured boards can use an external
connector/switch harness or an adapter; integrated footprints require a new PCB
revision.
