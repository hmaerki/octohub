# Commisioning

Serial 1. Remove R213 R214

Serial 1. Remove C205(100n) lost
Serial 1. Remove C214(100n) and replace C209(1n)

Serial 2. Remove C209(1n) destroyed pad

## Connect

| status | LED |
| - | - |
| on | green Power LED
| on (1s)/off (0.1s)/on | white LED 1
| on | white LED 3-4
| off | white LED 5-8

`sudo dmesg --follow`

```
[  962.101187] usb 3-1: new high-speed USB device number 28 using xhci_hcd
[  962.228270] usb 3-1: New USB device found, idVendor=0424, idProduct=2514, bcdDevice= b.b3
[  962.228276] usb 3-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[  962.229811] hub 3-1:1.0: USB hub found
[  962.229854] hub 3-1:1.0: 4 ports detected
```

`lsusb -tv`

```
/:  Bus 003.Port 001: Dev 001, Class=root_hub, Driver=xhci_hcd/12p, 480M
    ID 1d6b:0002 Linux Foundation 2.0 root hub
    |__ Port 001: Dev 028, If 0, Class=Hub, Driver=hub/4p, 480M
        ID 0424:2514 Microchip Technology, Inc. (formerly SMSC) USB 2.0 Hub
```

`sudo uhubctl`

```
Current status for hub 3-1 [0424:2514, USB 2.00, 4 ports, ppps]
  Port 1: 0100 power
  Port 2: 0100 power
  Port 3: 0100 power
  Port 4: 0100 power
```

```bash
sudo uhubctl --location 3-1 --action off
sudo uhubctl --location 3-1 --port 1 --action cycle
sudo uhubctl --location 3-1 --port 2 --action cycle
sudo uhubctl --location 3-1 --action on
```



