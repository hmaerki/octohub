# Commisioning

Serial 1. Remove R216

## Connect

| status | LED |
| - | - |
| on | green Power LED
| on (1s)/off (0.1s)/on | white LED 1
| on | white LED 3-4
| off | white LED 5-8

`sudo dmesg --follow`

```
[17211.868728] usb 3-1: new high-speed USB device number 105 using xhci_hcd
[17211.997940] usb 3-1: New USB device found, idVendor=0424, idProduct=2514, bcdDevice= b.b3
[17211.997950] usb 3-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[17212.003376] hub 3-1:1.0: USB hub found
[17212.003429] hub 3-1:1.0: 4 ports detected
[17212.286624] usb 3-1.1: new full-speed USB device number 106 using xhci_hcd
[17212.365613] usb 3-1.1: device descriptor read/64, error -32
[17212.551804] usb 3-1.1: device descriptor read/64, error -32
[17212.735758] usb 3-1.1: new full-speed USB device number 107 using xhci_hcd
[17212.814638] usb 3-1.1: device descriptor read/64, error -32
[17213.000828] usb 3-1.1: device descriptor read/64, error -32
[17213.106832] usb 3-1-port1: attempt power cycle
[17213.702627] usb 3-1.1: new full-speed USB device number 108 using xhci_hcd
[17213.702754] usb 3-1.1: Device not responding to setup address.
[17213.906874] usb 3-1.1: Device not responding to setup address.
[17214.114722] usb 3-1.1: device not accepting address 108, error -71
[17214.115010] usb 3-1.1: WARN: invalid context state for evaluate context command.
[17214.190564] usb 3-1.1: new full-speed USB device number 109 using xhci_hcd
[17214.191465] usb 3-1.1: Device not responding to setup address.
[17214.394974] usb 3-1.1: Device not responding to setup address.
[17214.602712] usb 3-1.1: device not accepting address 109, error -71
[17214.602999] usb 3-1.1: WARN: invalid context state for evaluate context command.
[17214.603137] usb 3-1-port1: unable to enumerate USB device
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


## Observations

* R216 (XTALOUT): error 0V

24MHz, 20samples/cycle

```python
20/24e6
0.8 us

