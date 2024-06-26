# Power consumtion


## RP2

| Mode | USB power descriptor | eff. power |
| - | - | - |
| Tentacle programming mode | 500 mA | 21 mA |
| SEEED run mode | 250 mA | ? |

Conclusion

One Tentacle with 1 RP2 programming and 1 RP2 run will draw 750A.

## Bus Power via selfpowered

### Bus Power

Limit 100mA, 500mA with tricks

### Self powered

Requires addition connection.

#### USB3 Powerered

* Standard cables
* USB Hub may be used as power supply

#### Custom Power cables

Variant a) Standard 6.5 mm

Power routing - USB 3

* Each tentacle has 2 USB 3 female connectors.
* The first tentacle need to be connected to a USB 3 supply.
* The followiing tentacles may be looped using USB 3 female-female cables.

Power routing - Octobus

* Some connections are reserved for 5 V power.
