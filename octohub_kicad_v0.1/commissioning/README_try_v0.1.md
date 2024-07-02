# Commisioning

Serial 1. Remove R212 (failed to add R208)


`sudo dmesg --follow`

```
[  962.101187] usb 3-1: new high-speed USB device number 28 using xhci_hcd
[  962.228270] usb 3-1: New USB device found, idVendor=0424, idProduct=2514, bcdDevice= b.b3
[  962.228276] usb 3-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[  962.229811] hub 3-1:1.0: USB hub found
[  962.229854] hub 3-1:1.0: 4 ports detected
```


`sudo uhubctl`

```
Current status for hub 3-5.3 [0424:2514, USB 2.00, 4 ports, ppps]
  Port 1: 0103 power enable connect [2e8a:0003 Raspberry Pi RP2 Boot E0C9125B0D9B]
  Port 2: 0103 power enable connect [2e8a:0005 MicroPython Board in FS mode 4150325537323318]
  Port 3: 0100 power
  Port 4: 0100 power
```

```bash
uhubctl -l 3-5.3 --action=on
Current status for hub 3-5.3 [0424:2514, USB 2.00, 4 ports, ppps]
  Port 1: 0000 off
  Port 2: 0000 off
  Port 3: 0000 off
  Port 4: 0000 off
Sent power on request
New status for hub 3-5.3 [0424:2514, USB 2.00, 4 ports, ppps]
  Port 1: 0100 power
  Port 2: 0100 power
  Port 3: 0100 power
  Port 4: 0100 power
```


`lsusb -v`

```
Bus 003 Device 025: ID 0424:2514 Microchip Technology, Inc. (formerly SMSC) USB 2.0 Hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 [unknown]
  bDeviceProtocol         2 TT per port
  bMaxPacketSize0        64
  idVendor           0x0424 Microchip Technology, Inc. (formerly SMSC)
  idProduct          0x2514 USB 2.0 Hub
  bcdDevice            b.b3
  iManufacturer           0 
  iProduct                0 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength       0x0029
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered         <=========================
      Remote Wakeup
    MaxPower                2mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 [unknown]
      bInterfaceProtocol      1 Single TT
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0001  1x 1 bytes
        bInterval              12
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       1
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 [unknown]
      bInterfaceProtocol      2 TT per port
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0001  1x 1 bytes
        bInterval              12
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             4
  wHubCharacteristic 0x000d
    Per-port power switching
    Compound device
    Per-port overcurrent protection
    TT think time 8 FS bits
  bPwrOn2PwrGood       50 * 2 milli seconds
  bHubContrCurrent      1 milli Ampere
  DeviceRemovable    0x02
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0100 power
   Port 3: 0000.0100 power
   Port 4: 0000.0100 power
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 [unknown]
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0001
  Self Powered         <=========================
```
