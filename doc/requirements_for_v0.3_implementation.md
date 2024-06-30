# v0.3 Implementation

## RP2 Infra has to enable USB DUT

Requirements

When the PC powers on, all USB plugs will be powered. However, USB DUT should NOT be powered!

The RP2 should allow USB DUT

## RP2 boot button has to enabled by USB

Requirements

Whe the PC powers on, the RP2 should boot in application mode (QSPI_SS pulled up).

This is the sequence to bring the RP2 into programming mode

| USB Infra RP2 (Plug 1) | USB Infra boot (Plug 2) | Trigger | RP2
| - | - | - | -
| 1 | 1 | PC power on | (A) undefinded/application mode
| | | - | |
| 0 | 0 | | off: prepare for programming
| 1 | 0 | | programming mode
| | | - | |
| 0 | 1 | | off: prepare for application
| 1 | 0 | | application mode
| | | - | |

(A) What is the power up sequence? It might be delayed.


Reset infra:
`USB Infra boot` 1.
`USB Infra RP2` 0.

