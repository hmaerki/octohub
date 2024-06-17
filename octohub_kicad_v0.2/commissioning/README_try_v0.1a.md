# Commisioning

## Connect

| status | LED |
| - | - |
| on | green Power LED
| on (1s)/off (0.1s)/on | white LED 1
| on | white LED 3-4
| off | white LED 5-8

`sudo dmesg --follow`

```
[ 4086.478036] usb 3-1: USB disconnect, device number 42
[ 4094.418796] usb 3-1: new high-speed USB device number 48 using xhci_hcd
[ 4094.546806] usb 3-1: New USB device found, idVendor=0424, idProduct=2514, bcdDevice= b.b3
[ 4094.546811] usb 3-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[ 4094.548094] hub 3-1:1.0: USB hub found
[ 4094.548130] hub 3-1:1.0: 4 ports detected
[ 4095.613963] usb 3-1-port1: Cannot enable. Maybe the USB cable is bad?
[ 4096.470757] usb 3-1-port1: Cannot enable. Maybe the USB cable is bad?
[ 4096.470877] usb 3-1-port1: attempt power cycle
[ 4097.637937] usb 3-1-port1: Cannot enable. Maybe the USB cable is bad?
[ 4098.493872] usb 3-1-port1: Cannot enable. Maybe the USB cable is bad?
[ 4098.494023] usb 3-1-port1: unable to enumerate USB device
```

`lsusb -tv`

```
/:  Bus 003.Port 001: Dev 001, Class=root_hub, Driver=xhci_hcd/12p, 480M
    ID 1d6b:0002 Linux Foundation 2.0 root hub
    |__ Port 001: Dev 048, If 0, Class=Hub, Driver=hub/4p, 480M
        ID 0424:2514 Microchip Technology, Inc. (formerly SMSC) USB 2.0 Hub
```

`sudo uhubctl`

```
Current status for hub 3-1 [0424:2514, USB 2.00, 4 ports, ppps]
  Port 1: 0101 power connect []
  Port 2: 0100 power
  Port 3: 0100 power
  Port 4: 0100 power
```

```
# Works after some flickering
uhubctl -l 3-5.2.1.2 --port 1 --action off
# Works fine
uhubctl -l 3-5.2.1.2 --port 2 --action off
uhubctl -l 3-5.2.1.2 --port 2 --action on
```

## Observations

* 5V: ok
* 3V3: ok
* U201 is detected via USB: position ok, most of the pions ok.
* TP201 (25MHZ): ok 0V
* R216 (XTALOUT): error 0V
* R201 (RESET_N): Reset after ~20ms

* RESET_N
```text
5.5.1 EXTERNAL HARDWARE RESET_N
A valid hardware reset is defined as assertion of RESET_N for a minimum of 1 us after all power supplies are within
operating range.
```

[sparcfun schematics](https://cdn.sparkfun.com/assets/6/f/1/5/b/Qwiic-USB_Hub.pdf): R5 (100k) - C8 (0.1uF)

octohub: R201 (100k) - C203 (0.1uF)

Tau is 10ms



* Crystal

```text
FIGURE 7-2: FORMULA TO FIND THE VALUE OF C1 AND C2
C1 = 2 x (CL – C0) – CS1
C2 = 2 x (CL – C0) – CS2

C1 = C2 = 18pF

```

https://wmsc.lcsc.com/wmsc/upload/file/pdf/v2/lcsc/2403291504_YXC-X322524MOB4SI_C70590.pdf

```text
C0 (shunt) = 3pF max
CL (load) = 12pF
CS (stray) = 2pF ???
CB (board) = 2pF ???
CXTAL (pin) = 2pF ???
```

```python
C0 = 3
CL = 12
CS = 2
CB = 2
CXTAL = 1

CS12 = CB + CXTAL
C1 = 2 * (CL - C0) - CS12
print(f"{C1=}")
# 15pF
```


* R216 (XTALOUT): error 0V

## ERROR (to be verified)

C209: 1nF

C9: 100nF https://github.com/sparkfunX/Qwiic_USB_Hub-USB2514B/blob/main/Hardware/Qwiic-USB_Hub.pdf

