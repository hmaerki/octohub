# Ideas


## 4 port hub versus 16 port hub

| 4 port | 16 port | Comment |
| :-: | :-: | - |
| | no usb configuration | uhubctl |
| simple| | Kicad project / jlcpcb order |
| more power | | upstream hub may support power |
| | simple, one pcb | Mechanics |
| flexible | | octoprobe arrangement |
| | plugs numbered from 1..16 | octoprobe arrangement |
| multipe power switches | | Power |

## Multiple power switches

* separate MT9700
* PRTPWR connects to MT9700
* MT9700 VIN: Experiment Plugs
* MT9700 VOUT: Experiment Plugs

According to datasheet
* VIN must be provided: 3V3 or 5V
* Max current: 2A

==> Goal: Switch

## Evaluate Relais

* Octoprobe
  * GAQY221S
  * https://wmsc.lcsc.com/wmsc/upload/file/pdf/v2/lcsc/2308151358_SUPSiC-GAQY221S_C7435105.pdf
  * USD 055

JLC search: `solid state relay MOS supsic`

| JLC |  USD | U Load R | Type | Datasheet |
| :-: | :-: | :-: | - | - |
| C393898 | 1.9 | 60V 1A 250m | TOSHIBA TLP3122(TP,F) | https://wmsc.lcsc.com/wmsc/upload/file/pdf/v2/lcsc/1912111437_TOSHIBA-TLP3122-TP-F_C393898.pdf |
| C19271987 | 0.6 | 60V 1.8A 70m | SUPSiC GAQY212GHA | https://wmsc.lcsc.com/wmsc/upload/file/pdf/v2/lcsc/2403241735_SUPSiC-GAQY212GHA_C19271987.pdf |
| C192C743510471987 | 0.74 | 40V 2.5A 60m | SUPSiC GAQY211G2S | https://wmsc.lcsc.com/wmsc/upload/file/pdf/v2/lcsc/2308151358_SUPSiC-GAQY211G2S_C7435104.pdf |
