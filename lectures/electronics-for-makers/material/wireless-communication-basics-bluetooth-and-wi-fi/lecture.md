# Wireless Communication Basics: Bluetooth and Wi-Fi

## Bluetooth

Bluetooth works in the 2.4GHz ISM band, divided into 79 channels, each 1MHz wide. Bluetooth devices use Frequency Hopping Spread Spectrum (FHSS) to avoid interference, hopping to a new frequency after transmitting or receiving a packet.

Bluetooth operates in a master-slave configuration. The master can communicate with up to seven slaves in a piconet, with the master controlling the communication channel and clock. 

Consider below Python code to connect a device using PyBluez, a Python Bluetooth library:

```python
import bluetooth

target_name = "My Device"
target_address = None

nearby_devices = bluetooth.discover_devices()

for bdaddr in nearby_devices:
    if target_name == bluetooth.lookup_name( bdaddr ):
        target_address = bdaddr
        break

if target_address is not None:
    print(f"Found target Bluetooth device with address {target_address}")
else:
    print("Could not find target Bluetooth device nearby")
```

## Wi-Fi

Wi-Fi operates on 2.4 GHz (Wi-Fi 4 & Wi-Fi 6) and 5 GHz (Wi-Fi 5 & Wi-Fi 6) frequency bands. It uses Carrier Sense Multiple Access with Collision Avoidance (CSMA/CA) for channel access.

Wi-Fi has two modes of operation: Infrastructure and Ad-hoc. Infrastructure mode involves devices (stations) communicating through an Access Point (AP), whereas in Ad-hoc mode, devices communicate directly.

Wi-Fi security protocols include WEP, WPA, WPA2, and WPA3. WPA2, using AES for encryption, is currently the most secure.

Below is Python code using the Scapy library to sniff Wi-Fi packets:

```python
from scapy.all import *

def packet_handler(pkt) :
    if pkt.haslayer(Dot11) :
        if pkt.type == 0 and pkt.subtype == 8 :
            print(f"Detected a Beacon Frame from {pkt.addr2} with SSID {pkt.info}")

sniff(iface="mon0", prn = packet_handler)
```

Remember, only use such code ethically and within the boundaries of the law.