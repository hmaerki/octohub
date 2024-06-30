# Detection of Tentacles

## Precondition

Stlatus when the infrastrucutre is powered up / reset:
* USB Plug Infra RPI: On
* USB Plug Infra Boot: On
* USB Plug Dut: Off

## Query

`lsusb -tv`

Find criteria for tentacles: Hub with RP2 on first port.

As the Infra RP2 is in application mode, the serial number identifies the tentacle.

