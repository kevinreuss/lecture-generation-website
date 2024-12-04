# Network Address Translation (NAT)

Network Address Translation (NAT) is a method used to remap one IP address space into another by modifying network address information in the IP header of packets while they are in transit across a traffic routing device.

## NAT Types

Three types of NAT are:

1. **Static NAT**: Maps unregistered IP addresses to registered IP addresses on one-to-one basis. Particularly useful when a device needs to be accessible from outside the network.

2. **Dynamic NAT**: Maps unregistered IP addresses to registered IP addresses from a pool of registered IP addresses. 

3. **Port Address Translation (PAT)**: Allows many devices on a local network to be mapped to a single registered IP address by using different ports.

## NAT Operation

NAT operates on a router, typically connecting two networks together, and translates the private (not globally unique) addresses in the internal network into legal addresses before packets are forwarded to another network.

Consider the following example:

```bash
Private IP: 192.168.0.10
Public IP: 203.0.113.0
```

A device on the private network with IP 192.168.0.10 will appear to the public internet as 203.0.113.0.

## NAT Table

NAT uses a NAT table for keeping track of related address pairs and the translations performed.

An example NAT table after a device with private IP 192.168.0.10 sends a packet might look like:

| Private IP    | Public IP   |
| ------------- | ----------- |
| 192.168.0.10  | 203.0.113.0 |

This table helps the NAT router to keep track of all outgoing traffic and ensure that when the response is returned, it can direct it to the correct device.

## NAT Limitations 

NAT can cause complications for protocols that require the initiator of communication to receive the responses, such as FTP and VoIP applications, due to the change in original IP. 

In conclusion, understanding NAT is crucial for network design and troubleshooting, as it plays an integral role in conserving public IP addresses and improving network security.