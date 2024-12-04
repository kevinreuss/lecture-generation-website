# Data Link Layer Protocols

Data Link Layer protocols are responsible for data transmission between nodes on the same network segment. These protocols define how devices identify and communicate with each other on the physical layer.

## Ethernet

Ethernet is the most commonly used Data Link Layer protocol. It uses a MAC (Media Access Control) address to identify devices and employs CSMA/CD (Carrier Sense Multiple Access with Collision Detection) mechanism for data transmission. 

Ethernet frames have a specific structure: preamble, destination MAC, source MAC, EtherType (specifies protocol type for the payload), payload, and Frame Check Sequence for error detection.

## PPP (Point-to-Point Protocol)

PPP is used for direct connections between two nodes. It provides a method for encapsulating multi-protocol packets over point-to-point links. PPP also uses a form of checksum for error checking.

## HDLC (High-Level Data Link Control)

HDLC is a bit-oriented synchronous Data Link Layer protocol developed by the ISO. HDLC provides both connection-oriented and connectionless service.

The frame structure of HDLC includes a Flag (indicates start and end of the frame), Address (destination address), Control (frame type and functions), Data, and FCS (Frame Check Sequence).

## IEEE 802.11 (Wireless LAN)

IEEE 802.11 is a set of Data Link Layer protocols that define the set of media access control (MAC) and physical layer (PHY) specifications for implementing wireless local area network (WLAN) communication in various frequencies.

The frame structure includes Frame Control, Duration, Address1, Address2, Address3, Sequence Control, Address4, Payload, and FCS. 

While there's no code involved in these protocols, understanding their frame structures and operation mechanisms is crucial. Each protocol has its use cases and understanding them allows you to make an informed decision while designing and troubleshooting network systems.
