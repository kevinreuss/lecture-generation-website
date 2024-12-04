# IP Protocol Implementation

The Internet Protocol (IP) is a core protocol that packets use to navigate the web. It's a network-layer protocol in the OSI model. There are two versions of IP in use today: IPv4 and IPv6.

## Packet Structure

Both IPv4 and IPv6 packets consist of a header and payload. The header contains information like the source and destination IP addresses, whereas the payload carries the actual data.

IPv4 headers are 20 to 60 bytes long, with each field having a specific purpose. For instance, the 'Version' field specifies the IP version, 'IHL' indicates the header length, and 'Total Length' denotes the total packet length. 

IPv6 headers are simpler and always 40 bytes. They have less information, making them easier to process. Key fields include 'Version' (set to 6), 'Traffic Class' (for QoS), and 'Flow Label' (for packet ordering).

## Routing

IP relies on routing tables to forward packets. A routing table contains a list of IP networks and next-hop associations. When a router receives a packet, it looks at the destination IP, searches its routing table, and sends the packet to the associated next hop.

Here's an example of a simple routing table:

| Destination     | Next Hop       |
|-----------------|----------------|
| 192.168.1.0/24  | Interface eth0 |
| 10.0.0.0/8      | 192.168.1.1    |
| 0.0.0.0/0       | 10.0.0.1       |

The first row represents a directly connected network. The second row is a static route, and the third row is the default route.

## Fragmentation and Reassembly

IP supports fragmentation and reassembly. If a packet is larger than the Maximum Transmission Unit (MTU) of the outgoing interface, the IP layer will fragment it into smaller packets. The destination host then reassembles these fragments back into the original packet.

Fragmentation is signaled by setting the 'More Fragments' flag in the IPv4 header and by the 'Fragment Offset' field. In IPv6, fragmentation is handled by the Fragment extension header.

Here's pseudo-code for a simple fragmentation process:

```python
if packet_size > MTU:
    fragments = fragment_packet(packet, MTU)
    for fragment in fragments:
        send_packet(fragment)
else:
    send_packet(packet)
```

In summary, implementing the IP protocol involves understanding packet structure, handling routing, and correctly managing fragmentation and reassembly.