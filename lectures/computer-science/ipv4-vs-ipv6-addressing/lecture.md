# IPv4 vs IPv6 Addressing

IPv4, or Internet Protocol version 4, uses a 32-bit addressing scheme which gives us 4,294,967,296 (2^32) unique addresses. These addresses are represented in dotted-decimal notation, which is divided into four octets. For example, `192.168.1.1`.

Contrarily, IPv6, or Internet Protocol version 6, uses a 128-bit addressing scheme. This allows for 3.4 x 10^38 (2^128) unique addresses. Addresses are represented in hexadecimal and separated by colons, for example, `2001:0db8:85a3:0000:0000:8a2e:0370:7334`.

Here's how a typical IPv4 and IPv6 address looks programmatically in Python:

```python
import socket

ipv4_address = socket.inet_ntop(socket.AF_INET, b'\xC0\xA8\x01\x01') # '192.168.1.1'
ipv6_address = socket.inet_ntop(socket.AF_INET6, b'\x20\x01\x0d\xb8\x85\xa3\x00\x00\x00\x00\x8a\x2e\x03\x70\x73\x34') # '2001:db8:85a3::8a2e:370:7334'
```

While IPv4 uses both unicast and broadcast addressing, IPv6 employs unicast, anycast, and multicast addressing. Broadcast addressing doesn't exist in IPv6. Instead, a link-local scope all-nodes multicast address is used.

IPv4 includes options such as security, source routing, and record route, which can be variable in length. But, these are not present in the IPv6 header. IPv6 includes a fixed header that is more efficient for routing.

IPv4 utilizes a checksum that needs to be recalculated by the router at each hop, increasing the computational load. IPv6 doesn't include a header checksum, reducing the processing load on routers.

IPv6 has built-in support for IPsec (IP security protocols), whereas IPsec support in IPv4 is optional.

IPv6's vast address space allows for hierarchical, structured address allocation, which simplifies routing when compared to the more random, less structured address allocation of IPv4. This results in smaller routing tables for IPv6.