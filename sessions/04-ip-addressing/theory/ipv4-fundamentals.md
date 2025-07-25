# IPv4 Addressing Fundamentals

## What is IPv4?

**IPv4 (Internet Protocol version 4)** is the fourth version of the Internet Protocol and the most widely used protocol for routing data across networks. It provides logical addressing for devices on a network.

## IPv4 Address Structure

### **32-Bit Address Format**
IPv4 addresses are 32-bit numbers divided into four 8-bit octets, separated by dots.

```
Example: 192.168.1.1
Binary:  11000000.10101000.00000001.00000001
```

### **Address Components**
- **Network Portion:** Identifies the network
- **Host Portion:** Identifies the specific device on the network
- **Subnet Mask:** Determines which part is network vs host

## Dotted Decimal Notation

### **Conversion Process**
Each octet represents a value from 0 to 255 (8 bits = 2^8 = 256 possible values)

```
Binary: 11000000.10101000.00000001.00000001
Octet 1: 11000000 = 192
Octet 2: 10101000 = 168
Octet 3: 00000001 = 1
Octet 4: 00000001 = 1
Result: 192.168.1.1
```

### **Common Conversions**
- **0:** 00000000
- **128:** 10000000
- **192:** 11000000
- **224:** 11100000
- **240:** 11110000
- **248:** 11111000
- **252:** 11111100
- **254:** 11111110
- **255:** 11111111

## Classful Addressing

### **Class A Addresses**
- **Range:** 1.0.0.0 to 126.255.255.255
- **First Bit:** 0
- **Default Mask:** 255.0.0.0 (/8)
- **Network Bits:** 8
- **Host Bits:** 24
- **Networks:** 126 (2^7 - 2)
- **Hosts per Network:** 16,777,214 (2^24 - 2)

### **Class B Addresses**
- **Range:** 128.0.0.0 to 191.255.255.255
- **First Bits:** 10
- **Default Mask:** 255.255.0.0 (/16)
- **Network Bits:** 16
- **Host Bits:** 16
- **Networks:** 16,384 (2^14)
- **Hosts per Network:** 65,534 (2^16 - 2)

### **Class C Addresses**
- **Range:** 192.0.0.0 to 223.255.255.255
- **First Bits:** 110
- **Default Mask:** 255.255.255.0 (/24)
- **Network Bits:** 24
- **Host Bits:** 8
- **Networks:** 2,097,152 (2^21)
- **Hosts per Network:** 254 (2^8 - 2)

### **Class D Addresses**
- **Range:** 224.0.0.0 to 239.255.255.255
- **Purpose:** Multicast addresses
- **Not used for host addressing**

### **Class E Addresses**
- **Range:** 240.0.0.0 to 255.255.255.255
- **Purpose:** Reserved for future use
- **Not used for host addressing**

## Special Addresses

### **Private Address Ranges**
- **Class A:** 10.0.0.0/8 (10.0.0.0 to 10.255.255.255)
- **Class B:** 172.16.0.0/12 (172.16.0.0 to 172.31.255.255)
- **Class C:** 192.168.0.0/16 (192.168.0.0 to 192.168.255.255)

### **Reserved Addresses**
- **Loopback:** 127.0.0.0/8 (127.0.0.1 for localhost)
- **Link-Local:** 169.254.0.0/16 (automatic private addressing)
- **Documentation:** 203.0.113.0/24 (example addresses)

### **Broadcast Addresses**
- **Network Broadcast:** Last address in network (e.g., 192.168.1.255)
- **Limited Broadcast:** 255.255.255.255 (all networks)

## Subnet Masks

### **Purpose**
Subnet masks determine which portion of an IP address belongs to the network and which belongs to the host.

### **Binary Representation**
- **1s:** Network portion
- **0s:** Host portion

### **Common Subnet Masks**
- **/8:** 255.0.0.0 (Class A default)
- **/16:** 255.255.0.0 (Class B default)
- **/24:** 255.255.255.0 (Class C default)
- **/25:** 255.255.255.128
- **/26:** 255.255.255.192
- **/27:** 255.255.255.224
- **/28:** 255.255.255.240
- **/29:** 255.255.255.248
- **/30:** 255.255.255.252

## CIDR Notation

### **What is CIDR?**
**CIDR (Classless Inter-Domain Routing)** is a method for allocating IP addresses and routing IP packets.

### **Format**
IP address followed by a slash and the number of network bits.

### **Examples**
- **192.168.1.0/24:** 24 network bits, 8 host bits
- **10.0.0.0/8:** 8 network bits, 24 host bits
- **172.16.0.0/16:** 16 network bits, 16 host bits

## Network Address Calculation

### **Process**
1. Convert IP address to binary
2. Convert subnet mask to binary
3. Perform AND operation
4. Convert result back to decimal

### **Example**
```
IP: 192.168.1.100
Mask: 255.255.255.0

IP Binary:     11000000.10101000.00000001.01100100
Mask Binary:   11111111.11111111.11111111.00000000
AND Result:    11000000.10101000.00000001.00000000
Network:       192.168.1.0
```

## Host Range Calculation

### **First Host Address**
Network address + 1

### **Last Host Address**
Broadcast address - 1

### **Broadcast Address**
Last address in the network

### **Example for 192.168.1.0/24**
- **Network:** 192.168.1.0
- **First Host:** 192.168.1.1
- **Last Host:** 192.168.1.254
- **Broadcast:** 192.168.1.255

## Number of Hosts

### **Formula**
Number of hosts = 2^(host bits) - 2

### **Examples**
- **/24:** 2^8 - 2 = 256 - 2 = 254 hosts
- **/25:** 2^7 - 2 = 128 - 2 = 126 hosts
- **/26:** 2^6 - 2 = 64 - 2 = 62 hosts
- **/27:** 2^5 - 2 = 32 - 2 = 30 hosts
- **/28:** 2^4 - 2 = 16 - 2 = 14 hosts
- **/29:** 2^3 - 2 = 8 - 2 = 6 hosts
- **/30:** 2^2 - 2 = 4 - 2 = 2 hosts

## Practical Examples

### **Example 1: 192.168.1.0/24**
- **Subnet Mask:** 255.255.255.0
- **Network:** 192.168.1.0
- **Host Range:** 192.168.1.1 - 192.168.1.254
- **Broadcast:** 192.168.1.255
- **Hosts:** 254

### **Example 2: 10.0.0.0/16**
- **Subnet Mask:** 255.255.0.0
- **Network:** 10.0.0.0
- **Host Range:** 10.0.0.1 - 10.0.255.254
- **Broadcast:** 10.0.255.255
- **Hosts:** 65,534

### **Example 3: 172.16.0.0/26**
- **Subnet Mask:** 255.255.255.192
- **Network:** 172.16.0.0
- **Host Range:** 172.16.0.1 - 172.16.0.62
- **Broadcast:** 172.16.0.63
- **Hosts:** 62

---

## Summary

Understanding IPv4 addressing is fundamental to networking. Key concepts include:
- 32-bit address structure with four octets
- Classful addressing (A, B, C, D, E)
- Subnet masks and CIDR notation
- Network address calculation
- Host range determination
- Private vs public address ranges

**Next:** [Subnetting Concepts and Calculations](./subnetting-concepts.md) 