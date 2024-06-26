# Commisioning

Serial 1: Remove R1106 (CFG_SEL[1])

Now the hub is self-powered!

## CFG_SEL[1], pin 25

Currently: `0 self powererd`
New: `1 bus powered`


## Error in schematic: Plug 3

Schematic `hub4-1`, `chip_downstream`.

Reversed `PRT_D_P3` and `PRT_D_M3`
