# Plugins used

* https://github.com/bennymeg/JLC-Plugin-for-KiCad

  JLC PCB Plug-in for KiCad

  Fill Symbol Field `JLC Part`

* https://github.com/MitjaNemec/ReplicateLayout

## Protype Baord

### Precondition

...

## Hierarchical sheet

* https://forum.kicad.info/t/variables-in-hierarchical-sheet-labels/41978

In pcb, place all relais footprints (silkscreen) correctly.

Select first pcb, `Tools -> External Plugins -> Replicate Layout`

## Replicate Layout

* Reference Layout `pcb_octohub_cip.kicad_sch`: `chip_upstream`
  * Reference footprint: USB Chip
  * UR201 `+` spawns the top left corner

* Reference Layout `pcb_octohub_plug.kicad_sch`: `hub4-1/plug_A`
  * Reference footprint: Plug
  * UR1201 is the plug label
  * UR1202 `+` spawns the top left corner

* Reference Layout `pcb_octohub_hub4.kicad_sch`: `hub4-1`
  * Reference footprint: UR1001 `+`
  * UR1001 `+` spawns the top left corner

## Production

### In schematics

Menu `Inspect -> Electrical Rule Chacker`, button `Run ERC`, No violatons

### Increment version number

Update in all sheets

### In pcb - final check and final commit

Menu `Tools -> Update PCB from Schematic`, only one error `Error: Multiple footprings found for 'PB101'`

Menu `Tools -> Cleanup Tracks & Vias`, select all,  `Build Changes`, No violatons

Menu `Inspect -> Design Rules Chacker`, check `Refill all zones`, button `Run DRC . No errors, no warnings.

Delete all files in directory `production`.

Icon `Fabricaton Toolkit`, Options empty, check `Apply automatic translatons`, UNcheck `Exluce DNP components`.

Rename production folder and add version number

### Print schematics

Schematics, Menu `File -> Print`, check 'Print drawing sheet - Color`, `Print`, `All Pages`, `Pirnt to File`.

Move `~/Documents/output.pdf` to `hardware/octoprobe_kicad_v1/production_v2.0/schematics.pdf`

### Upload to JLCPCB

See: octohub_kicad_v0.2/production_v0.2/README_production_v0.2.md
