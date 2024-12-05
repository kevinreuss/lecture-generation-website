# Introduction to RFID and NFC Modules

## RFID (Radio Frequency Identification)

RFID is a wireless system that uses electromagnetic fields for data transfer. It includes two key components:

1. **RFID Tag**: This is a small chip that stores data. Passive tags draw power from the RFID reader's electromagnetic field, while active tags have their own power source.

2. **RFID Reader**: This is a device that reads the information stored on the RFID tag.

RFID operates on low (125kHz), high (13.56MHz) and ultra-high frequencies (860-960MHz). The choice of frequency impacts the read range and data transfer speed.

### Example of RFID in Use

In logistics, RFID tags are attached to items. As the items pass by an RFID reader, information about the item (e.g., its identity, location, and status) is automatically logged.

## NFC (Near Field Communication)

NFC is a specialized subset within the family of RFID technology. The key distinction is that NFC operates at 13.56 MHz and at a maximum distance of about 10 cm.

NFC has three modes of operation:

1. **Reader/Writer mode**: The NFC device reads or writes data to NFC tags.

2. **Peer-to-peer mode**: Two NFC devices exchange data.

3. **Card emulation mode**: The NFC device behaves like an existing contactless card.

### Example of NFC in Use

NFC is commonly used for contactless payment systems. Consider this simplified example:

```python
class NFCDevice:
    def __init__(self, balance):
        self.balance = balance

    def pay(self, amount):
        if self.balance >= amount:
            self.balance -= amount
            return True
        return False

# Create a new NFC device with a balance of 100
myCard = NFCDevice(100)

# Make a payment
if myCard.pay(20):
    print("Payment successful")
else:
    print("Insufficient balance")
```

In this Python example, an NFC device (represented as a class) is used to make a payment. The `pay` method decreases the balance on the card if sufficient funds are available.

Please note that real NFC transactions involve complex security protocols, which are not represented in this simplified example.