# MAC Addressing and ARP

## 🎯 Overview
MAC (Media Access Control) addresses are unique identifiers assigned to network interfaces. The Address Resolution Protocol (ARP) maps IP addresses to MAC addresses, enabling communication on Ethernet networks.

## 📋 MAC Address Fundamentals

### What is a MAC Address?
```
Definition: 48-bit unique identifier for network interfaces
Format: XX:XX:XX:XX:XX:XX (hexadecimal)
Scope: Local network (Layer 2)
Uniqueness: Globally unique (in theory)
Assignment: IEEE assigns OUI, manufacturer assigns rest
```

### MAC Address Structure
```
┌─────────────────┬─────────────────────────────────┐
│   OUI (24 bits) │    NIC Specific (24 bits)      │
│  Manufacturer   │      Serial Number             │
└─────────────────┴─────────────────────────────────┘
```

### MAC Address Format
```
Binary: 10101010 10101010 10101010 10101010 10101010 10101010
Hex:    AA:AA:AA:AA:AA:AA
Colon:  AA:AA:AA:AA:AA:AA
Hyphen: AA-AA-AA-AA-AA-AA
Dot:    AAAA.AAAA.AAAA
```

---

## 🏷️ MAC Address Types

### Unicast Addresses
```
Definition: Addresses assigned to specific network interfaces
First Bit: 0 (I/G bit = 0)
Use: Point-to-point communication
Example: 00:1B:44:11:3A:B7
```

### Multicast Addresses
```
Definition: Addresses for group communication
First Bit: 1 (I/G bit = 1)
Use: One-to-many communication
Examples:
- 01:00:5E:XX:XX:XX (IPv4 multicast)
- 33:33:XX:XX:XX:XX (IPv6 multicast)
```

### Broadcast Addresses
```
Definition: Address for all devices on network
Value: FF:FF:FF:FF:FF:FF
Use: Send to all devices
Scope: Local broadcast domain
```

### Special MAC Addresses
```
Null Address: 00:00:00:00:00:00
Broadcast: FF:FF:FF:FF:FF:FF
Locally Administered: Second bit = 1
Universally Administered: Second bit = 0
```

---

## 🏭 OUI (Organizationally Unique Identifier)

### OUI Structure
```
Purpose: Identifies manufacturer of network interface
Length: 24 bits (3 bytes)
Assignment: IEEE Registration Authority
Database: Publicly available MAC address database
```

### Common OUIs
```
Cisco: 00:1B:44, 00:1C:58, 00:40:96
Intel: 00:1B:21, 00:1C:C0, 00:1E:67
Apple: 00:1C:B3, 00:1E:C2, 00:25:00
Dell: 00:1B:44, 00:1C:58, 00:1E:67
```

### OUI Lookup
```
Online Databases: IEEE MAC address database
Tools: Wireshark, network scanners
Purpose: Identify device manufacturers
Security: Track devices on network
```

---

## 🔄 Address Resolution Protocol (ARP)

### What is ARP?
```
Purpose: Map IP addresses to MAC addresses
Layer: Network layer (Layer 3)
Operation: Request/response protocol
Scope: Local network only
```

### ARP Operation
```
1. Host A wants to send packet to Host B (IP known)
2. Host A checks ARP cache for Host B's MAC
3. If not found, Host A sends ARP request
4. Host B responds with its MAC address
5. Host A updates ARP cache and sends packet
```

### ARP Packet Structure
```
┌─────────┬─────────┬─────────┬─────────┬─────────┬─────────┐
│ Hardware│ Protocol│ Hw Addr │ Proto   │ Sender  │ Sender  │
│  Type   │  Type   │  Length │ Addr    │ Hw Addr │ Proto   │
│  (2B)   │  (2B)   │  (1B)   │ Length  │  (6B)   │ Addr    │
│         │         │         │  (1B)   │         │  (4B)   │
└─────────┴─────────┴─────────┴─────────┴─────────┴─────────┘
┌─────────┬─────────┬─────────┬─────────┬─────────┬─────────┐
│ Target  │ Target  │ Target  │ Target  │ Target  │ Target  │
│ Hw Addr │ Proto   │ Hw Addr │ Proto   │ Hw Addr │ Proto   │
│  (6B)   │ Addr    │  (6B)   │ Addr    │  (6B)   │ Addr    │
│         │  (4B)   │         │  (4B)   │         │  (4B)   │
└─────────┴─────────┴─────────┴─────────┴─────────┴─────────┘
```

### ARP Field Details
```
Hardware Type: 1 (Ethernet)
Protocol Type: 0x0800 (IPv4)
Hardware Address Length: 6 (MAC address length)
Protocol Address Length: 4 (IPv4 address length)
Operation: 1 (request), 2 (reply)
Sender/Target Addresses: MAC and IP addresses
```

---

## 📋 ARP Cache

### What is ARP Cache?
```
Definition: Table storing IP-to-MAC mappings
Location: Operating system memory
Purpose: Avoid repeated ARP requests
Timeout: Entries expire after specified time
```

### ARP Cache Structure
```
IP Address | MAC Address | Interface | Type | Age
192.168.1.1| 00:1B:44:11:3A:B7 | eth0 | dynamic | 120s
192.168.1.2| 00:1B:44:11:3A:B8 | eth0 | static | -
```

### ARP Cache Management
```
Dynamic Entries: Learned through ARP requests
Static Entries: Manually configured
Timeout: Automatic expiration (typically 2-20 minutes)
Flush: Manual cache clearing
```

### ARP Cache Commands
```
Windows:
arp -a: Display ARP cache
arp -d: Delete ARP cache
arp -s: Add static entry

Linux/macOS:
arp -a: Display ARP cache
arp -d: Delete ARP cache
arp -s: Add static entry

Cisco:
show arp: Display ARP table
clear arp-cache: Clear ARP cache
```

---

## 🔄 ARP Process Examples

### Normal ARP Process
```
Step 1: Host A (192.168.1.10) wants to send to Host B (192.168.1.20)
Step 2: Check ARP cache for 192.168.1.20
Step 3: Not found, send ARP request broadcast
Step 4: Host B receives request, sends ARP reply
Step 5: Host A receives reply, updates cache
Step 6: Send data packet to Host B
```

### ARP Request Packet
```
Ethernet Header:
- Destination: FF:FF:FF:FF:FF:FF (broadcast)
- Source: 00:1B:44:11:3A:B7 (Host A)
- Type: 0x0806 (ARP)

ARP Payload:
- Operation: 1 (request)
- Sender MAC: 00:1B:44:11:3A:B7
- Sender IP: 192.168.1.10
- Target MAC: 00:00:00:00:00:00 (unknown)
- Target IP: 192.168.1.20
```

### ARP Reply Packet
```
Ethernet Header:
- Destination: 00:1B:44:11:3A:B7 (Host A)
- Source: 00:1B:44:11:3A:B8 (Host B)
- Type: 0x0806 (ARP)

ARP Payload:
- Operation: 2 (reply)
- Sender MAC: 00:1B:44:11:3A:B8
- Sender IP: 192.168.1.20
- Target MAC: 00:1B:44:11:3A:B7
- Target IP: 192.168.1.10
```

---

## 🛡️ ARP Security

### ARP Vulnerabilities
```
ARP Spoofing: Attacker sends fake ARP replies
ARP Poisoning: Corrupting ARP cache with false entries
Man-in-the-Middle: Intercepting traffic between hosts
Denial of Service: Flooding with ARP requests
```

### ARP Spoofing Attack
```
1. Attacker sends fake ARP reply to Host A
2. Claims to be Host B (192.168.1.20)
3. Host A updates ARP cache with attacker's MAC
4. Traffic to Host B goes to attacker
5. Attacker can intercept, modify, or forward traffic
```

### Security Measures
```
Static ARP Entries: Manually configure critical mappings
ARP Monitoring: Track ARP traffic for anomalies
Dynamic ARP Inspection: Validate ARP messages
ARP Spoofing Detection: Monitor for suspicious ARP activity
```

### Prevention Techniques
```
Port Security: Limit MAC addresses per port
DHCP Snooping: Validate DHCP messages
Dynamic ARP Inspection: Validate ARP messages
Network Segmentation: Use VLANs to limit scope
Monitoring: Track ARP traffic patterns
```

---

## 🔧 ARP Configuration

### Static ARP Entries
```
Purpose: Manually configure IP-to-MAC mappings
Use Cases: Critical servers, security requirements
Persistence: Survive reboots (if configured)
Management: Requires manual maintenance
```

### ARP Timeout Configuration
```
Default: 2-20 minutes (varies by OS)
Adjustment: Based on network stability
Short Timeout: More ARP requests, better security
Long Timeout: Fewer ARP requests, less overhead
```

### ARP Proxy
```
Purpose: Respond to ARP requests for other networks
Use Cases: Router interfaces, load balancers
Configuration: Enable on specific interfaces
Benefits: Reduce ARP traffic across networks
```

---

## 📊 ARP Troubleshooting

### Common ARP Issues
```
ARP Cache Corruption: Invalid entries in cache
ARP Timeout: Entries expiring too quickly
ARP Spoofing: Fake ARP responses
Network Congestion: ARP requests not reaching destination
```

### Troubleshooting Commands
```
Display ARP Cache:
- Windows: arp -a
- Linux: arp -a
- Cisco: show arp

Clear ARP Cache:
- Windows: arp -d
- Linux: arp -d
- Cisco: clear arp-cache

ARP Statistics:
- Linux: cat /proc/net/arp
- Cisco: show arp statistics
```

### Troubleshooting Steps
```
1. Check ARP Cache: Verify entries are correct
2. Clear ARP Cache: Remove potentially corrupted entries
3. Test Connectivity: Use ping to trigger ARP
4. Monitor ARP Traffic: Use packet capture tools
5. Check Network: Verify physical connectivity
6. Security Analysis: Look for ARP spoofing
```

---

## 🌐 ARP in Different Environments

### IPv4 ARP
```
Protocol: Standard ARP (RFC 826)
Address Length: 4 bytes (IPv4)
Hardware Type: 1 (Ethernet)
Operation: Request (1), Reply (2)
```

### IPv6 Neighbor Discovery
```
Protocol: Neighbor Discovery Protocol (NDP)
Address Length: 16 bytes (IPv6)
Messages: Neighbor Solicitation, Neighbor Advertisement
Features: Stateless address autoconfiguration
```

### Proxy ARP
```
Purpose: Router responds to ARP for remote networks
Configuration: Enable on router interfaces
Benefits: Transparent routing for hosts
Considerations: Security and performance impact
```

---

## 🔍 ARP Analysis Tools

### Packet Capture Tools
```
Wireshark: Detailed ARP packet analysis
tcpdump: Command-line packet capture
Network Monitor: Windows packet capture
Ethereal: Historical packet analyzer
```

### Network Scanners
```
Nmap: Network discovery and ARP scanning
Angry IP Scanner: Fast network scanning
Advanced IP Scanner: Windows network scanner
arp-scan: Linux ARP scanning tool
```

### Analysis Techniques
```
ARP Traffic Analysis: Monitor ARP request/reply patterns
MAC Address Tracking: Track device movements
Security Monitoring: Detect ARP spoofing attempts
Performance Analysis: Measure ARP response times
```

---

## 🎓 Summary

### Key Concepts
- **MAC Addresses:** Unique 48-bit identifiers for network interfaces
- **OUI:** Organizationally Unique Identifier identifies manufacturer
- **ARP:** Protocol that maps IP addresses to MAC addresses
- **ARP Cache:** Table storing IP-to-MAC mappings
- **Security:** ARP spoofing and protection measures

### MAC Address Types
- **Unicast:** Specific device addresses
- **Multicast:** Group communication addresses
- **Broadcast:** All devices address (FF:FF:FF:FF:FF:FF)
- **Special:** Null, locally administered addresses

### ARP Process
- **Request:** Broadcast to find MAC address
- **Reply:** Unicast response with MAC address
- **Cache:** Store mapping for future use
- **Timeout:** Automatic expiration of entries

### Security Considerations
- **ARP Spoofing:** Fake ARP responses
- **Protection:** Static entries, monitoring, validation
- **Detection:** Traffic analysis, anomaly detection
- **Prevention:** Network segmentation, security policies

### Best Practices
- **Monitoring:** Track ARP traffic patterns
- **Security:** Implement ARP protection measures
- **Documentation:** Maintain MAC address inventory
- **Troubleshooting:** Use appropriate tools and techniques 