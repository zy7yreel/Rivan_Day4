
Subnetting
- IPv4
- IPv6

- Find Host & Subnet

##

Static Routing
- Default
- Floating

Dynamic Routing
- IGP
  - Link State
    - OSPF
    - IS-IS
  - Distance Vector
    - RIP
    - EIGRP
- EGP
  - BGP


##

OSI

Layer 7
Layer 6
Layer 5
Layer 4
Layer 3
- IPv4 Header vs IPv6 Header

- Version IPv4 or IPv6
- Internet Header Length - identifies the length of the header in 4-byte increments
- Total Length of the entire packet with L3 and L4 headers
- Identification Field (16 bits) - Which fragment it belongs to? (Packets are fragmented when the size is larger than 
MTU)
- Flags (IPv4) - Fragment and reassemble the larger packets
  - Bit 0 : Reserved
  - Bit 1: Don't Fragment bit
  - Bit 2: More Fragments bit
- Fragment offset - indicates numbering of fragment
- Time-to-live : Default 64
- Protocol - 6 TCP & 17 UDP & 1 ICMP & 89 OSPF(For encapsulated IPv4 Payload)
- Source IP
- Destination IP




Layer 2
- (Ethernet Header)
- Flow control
- Collisions
- Input & Output Errors
- Ethernet Frame
- SFD (1 byte) 10101011 - marks the start of frame data
- Destination MAC (6 bytes)
- Source Mac (6 bytes)
- Ether Type/Length (2 bytes) - Identify Network Protocol (IPv4 0x0800, IPv6 0x86DD, ARP (0x0806))
  Ethernet II - IEEE 802.3 - 
    - Value changes:
      - If 1500 (0x05DC) or less, it is the length of the payload
      - If 1536 (0x0600) or greater, it functions as an EtherType Field
- Payload/Packet (Varies, 46-1500 bytes)

- FCS (Trailer, 4 bytes) A CRC Check for error detecture and data integrity

- MAC Address : Org Unique Identifier : Network Interface Controller

Layer 1
- Bits
- Device Specs
- Cables
- Media
- Preamble (7 bytes: 10101010 * 7) Alternating 1s and 0s (synchronize for reciever clocks)
