# IP Addressing Core Concepts

## Introduction
This document covers fundamental concepts of IP addressing, including IPv4, IPv6, subnetting, and practical addressing schemes. Understanding these concepts is essential for network design, troubleshooting, and administration.

## IP Address Basics

### What is an IP Address?
An Internet Protocol (IP) address is a unique binary number assigned to a host for communication purposes. IP addresses enable devices to identify and communicate with each other on networks.

### Public vs. Private IP Addresses

| Public IP Addresses | Private IP Addresses |
|---------------------|----------------------|
| Unique globally | Not unique (can be reused in different networks) |
| Can communicate directly over the internet | Cannot communicate directly over the internet using their own IPs |
| Identify themselves by their own IPs | Identify themselves using a Proxy IP (NAT) |
| Must be purchased before use | Free to use within their designated ranges |

### Special Addresses
- **Network Address**: When all host bits are '0' (e.g., 128.111.0.0/16)
- **Broadcast Address**: When all host bits are '1' (e.g., 128.211.255.255/16)

## Subnetting

### Definition
Subnetting is the process of dividing a network into smaller subnetworks by borrowing bits from the host portion of an IP address to create additional network bits.

### Effects of Subnetting
- Increases the number of hosts in the overall network
- Reduces the number of entities in routing tables
- Increases the number of subnetworks
- Decreases the number of hosts per subnet

## Classful vs Classless Addressing

### Classful IP Addressing
- Allocates IP addresses according to five major classes (A, B, C, D, E)
- Less practical and useful in modern networking
- Network ID and host ID sizes are fixed based on class
- No flexibility in network/host ID boundaries

### Classless Addressing (CIDR)
- More flexible approach using Variable Length Subnet Masks (VLSM)
- Allows for efficient allocation of IP address space
- Represented with slash notation (e.g., /24, /16)

## IPv6

### Header Format
```
+-------------+-----------------+-----------------+
| Version     | Traffic Class   | Flow Label      |
| (4 bits)    | (8 bits)        | (20 bits)       |
+-------------+-----------------+-----------------+
| Payload Length               | Next Header      |
| (16 bits)                    | (8 bits)         |
+------------------------------+------------------+
| Hop Limit (8 bits)                             |
+------------------------------------------------+
| Source Address (128 bits)                      |
+------------------------------------------------+
| Destination Address (128 bits)                 |
+------------------------------------------------+
| Data                                           |
+------------------------------------------------+
```

### Key Fields
- **Version**: Identifies IP version (IPv6)
- **Traffic Class**: Differentiates packets with different delivery requirements
- **Flow Label**: Identifies packets belonging to the same flow
- **Payload Length**: Indicates bytes following the 40-byte header
- **Next Header**: Identifies extension headers that follow
- **Hop Limit**: Prevents packets from circulating indefinitely
- **Source/Destination Address**: 128-bit IPv6 addresses

### IPv6 Features
1. **Large Address Space**: 128-bit addresses (16 bytes)
2. **Simplified Header Format**: Only 7 fields for faster processing
3. **Better Support for Options**: Extended header support
4. **Enhanced Security**: Built-in authentication and privacy features
5. **Quality of Service**: Improved support for differentiated services

## IPv4 vs IPv6 Comparison

| IPv4 | IPv6 |
|------|------|
| 32-bit addresses | 128-bit addresses |
| Decimal notation with dots | Hexadecimal notation with colons |
| Limited payload capacity | Larger payload capacity |
| Complex router tasks | Simplified router processing |
| Divided into public/private IPs | No public/private division needed |

## Loopback Test
A loopback test sends a signal from a communication device and returns it to verify proper device operation. It can be performed using a special wrap-plug that returns output data as input data, simulating a complete communication circuit.

## Practical Subnetting Examples

### Example 1: Creating Multiple Subnets
**Given**: IP range 200.200.0.0/16, need at least 15 usable subnets

1. **IP Class**: Class C (though /16 is traditionally Class B)
2. **Suitable Subnets**: 30 usable subnets (2^5 - 2 = 30)
3. **IPs per Subnet**: 2046 usable addresses (2^11 - 2 = 2046)
4. **Subnet Mask for 41st Subnet**: 255.255.248.0
5. **Usable IP Range for Last Subnet**: 200.200.16.1 to 200.200.23.254

### Example 2: Subnetting for Specific Requirements
**Given**: 210.210.210.0/24, need subnets with minimum 15 usable IPs each

1. **Host Bits to Borrow**: 3 bits (creating 6 usable subnets with 30 hosts each)
2. **Network Address of Last Usable Subnet**: 210.210.210.192
3. **Second Usable IP of Last Subnet**: 210.210.210.194

### Example 3: Complex Subnetting Scenario
**Given**: 192.168.30.0/24, need at least 6 subnets with 30+ hosts each

1. **Broadcast Address of 2nd Subnet**: 192.168.30.95
2. **Subnet Mask for 3rd Subnet**: 255.255.255.224
3. **First Usable IP of 5th Subnet**: 192.168.30.161
4. **Last Usable IP of 4th Subnet**: 192.168.30.158

## Network Calculation Example

**Given**: IP 192.168.121.121 with subnet mask 255.255.248.0

1. **Network Address**: 192.168.120.0
2. **Broadcast Address**: 192.168.127.255
3. **Maximum Hosts**: 2046 (2^11 - 2)
4. **First Usable IP**: 192.168.120.1
5. **Last Usable IP**: 192.168.127.254

## Conversion Between IPv4 and IPv6
To convert IPv4 address 192.168.35.1/24 to IPv6:
1. Convert each octet to hexadecimal:
   - 192 → C0
   - 168 → A8
   - 35 → 23
   - 1 → 01
2. IPv6 equivalent: ::C0A8:2301

## Conclusion
Understanding IP addressing fundamentals, subnetting techniques, and the differences between IPv4 and IPv6 is crucial for network professionals. These concepts form the foundation of network design, implementation, and troubleshooting in modern networking environments.
