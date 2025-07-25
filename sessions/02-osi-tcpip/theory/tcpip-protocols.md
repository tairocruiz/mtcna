# TCP/IP Protocol Suite

## What is TCP/IP?

**TCP/IP (Transmission Control Protocol/Internet Protocol)** is the fundamental communication protocol suite that enables the Internet and most modern networks. It was developed by the U.S. Department of Defense in the 1970s and has become the standard for network communication.

## TCP/IP vs OSI Model

### **Key Differences:**
- **OSI:** 7 layers, theoretical model
- **TCP/IP:** 4 layers, practical implementation
- **OSI:** More detailed layer separation
- **TCP/IP:** Simplified, internet-focused

### **Mapping:**
```
OSI Model          TCP/IP Model
┌─────────────┐    ┌─────────────┐
│ Application │    │ Application │
│ Presentation│    │             │
│ Session     │    │             │
├─────────────┤    ├─────────────┤
│ Transport   │    │ Transport   │
├─────────────┤    ├─────────────┤
│ Network     │    │ Internet    │
├─────────────┤    ├─────────────┤
│ Data Link   │    │ Network     │
│ Physical    │    │ Access      │
└─────────────┘    └─────────────┘
```

## TCP/IP Layers

### **Layer 4: Application Layer**
**Purpose:** Provides network services to applications

**Key Protocols:**

#### **HTTP (Hypertext Transfer Protocol)**
- **Port:** 80 (HTTP), 443 (HTTPS)
- **Purpose:** Web browsing and data transfer
- **Features:** Request-response model, stateless
- **Example:** `GET /index.html HTTP/1.1`

#### **FTP (File Transfer Protocol)**
- **Port:** 21 (control), 20 (data)
- **Purpose:** File upload/download
- **Features:** Separate control and data connections
- **Modes:** Active and passive

#### **SMTP (Simple Mail Transfer Protocol)**
- **Port:** 25, 587 (SMTP), 110 (POP3), 143 (IMAP)
- **Purpose:** Email transmission
- **Features:** Text-based protocol, store-and-forward

#### **DNS (Domain Name System)**
- **Port:** 53 (UDP/TCP)
- **Purpose:** Name resolution (domain to IP)
- **Features:** Hierarchical, distributed database
- **Example:** `www.google.com` → `142.250.190.36`

#### **DHCP (Dynamic Host Configuration Protocol)**
- **Port:** 67 (server), 68 (client)
- **Purpose:** Automatic IP address assignment
- **Features:** Lease-based addressing, option configuration

#### **SNMP (Simple Network Management Protocol)**
- **Port:** 161 (UDP), 162 (trap)
- **Purpose:** Network device management
- **Features:** Get/Set operations, trap notifications

### **Layer 3: Transport Layer**
**Purpose:** Ensures reliable data delivery between applications

#### **TCP (Transmission Control Protocol)**
**Characteristics:**
- **Connection-oriented:** Three-way handshake
- **Reliable:** Acknowledgments and retransmission
- **Ordered:** Sequence numbers ensure correct order
- **Flow control:** Window size management
- **Error checking:** Checksum validation

**TCP Header Fields:**
- **Source Port (16 bits):** Sending application port
- **Destination Port (16 bits):** Receiving application port
- **Sequence Number (32 bits):** Data byte position
- **Acknowledgment Number (32 bits):** Next expected byte
- **Flags:** SYN, ACK, FIN, RST, PSH, URG
- **Window Size (16 bits):** Available buffer space
- **Checksum (16 bits):** Error detection

**TCP Connection States:**
1. **CLOSED:** No connection
2. **LISTEN:** Server waiting for connection
3. **SYN_SENT:** Client sent SYN
4. **SYN_RECEIVED:** Server received SYN
5. **ESTABLISHED:** Connection active
6. **FIN_WAIT:** Connection termination initiated
7. **CLOSE_WAIT:** Received FIN, waiting to close
8. **CLOSING:** Both sides closing simultaneously
9. **TIME_WAIT:** Waiting for final ACK
10. **CLOSED:** Connection terminated

#### **UDP (User Datagram Protocol)**
**Characteristics:**
- **Connectionless:** No handshake required
- **Unreliable:** No acknowledgments or retransmission
- **Unordered:** No sequence numbers
- **Lightweight:** Minimal overhead
- **Fast:** No connection establishment

**UDP Header Fields:**
- **Source Port (16 bits):** Sending application port
- **Destination Port (16 bits):** Receiving application port
- **Length (16 bits):** UDP header + data length
- **Checksum (16 bits):** Error detection (optional)

**UDP Use Cases:**
- **DNS queries:** Fast name resolution
- **DHCP:** Network configuration
- **Streaming media:** Real-time video/audio
- **Gaming:** Low-latency requirements
- **SNMP:** Network management

#### **QUIC (Quick UDP Internet Connections)**
**Characteristics:**
- **Transport Layer:** Built on top of UDP
- **Connection-oriented:** Reliable, ordered delivery
- **Multiplexed:** Multiple streams over single connection
- **Encrypted:** Built-in TLS 1.3 encryption
- **Low Latency:** Reduced connection establishment time

**QUIC Features:**
- **0-RTT Connection:** Faster than TCP handshake
- **Connection Migration:** Survives network changes
- **Stream Multiplexing:** Independent data streams
- **Forward Error Correction:** Built-in error recovery
- **Header Compression:** Reduced overhead

**QUIC Use Cases:**
- **HTTP/3:** Modern web protocol
- **Video streaming:** YouTube, Netflix
- **Gaming:** Low-latency applications
- **Mobile applications:** Better performance on mobile networks

### **Layer 2: Internet Layer**
**Purpose:** Provides logical addressing and routing

#### **IP (Internet Protocol)**
**IPv4 Header Fields:**
- **Version (4 bits):** IP version (4 for IPv4)
- **Header Length (4 bits):** Header size in 32-bit words
- **Type of Service (8 bits):** QoS marking
- **Total Length (16 bits):** Packet size in bytes
- **Identification (16 bits):** Fragment identification
- **Flags (3 bits):** Don't Fragment, More Fragments
- **Fragment Offset (13 bits):** Fragment position
- **Time to Live (8 bits):** Hop count limit
- **Protocol (8 bits):** Upper layer protocol (TCP=6, UDP=17)
- **Header Checksum (16 bits):** Header error detection
- **Source Address (32 bits):** Sender IP address
- **Destination Address (32 bits):** Receiver IP address
- **Options (variable):** Optional header fields

**IP Addressing:**
- **32-bit addresses:** 4 octets (e.g., 192.168.1.1)
- **Classful addressing:** A, B, C, D, E classes
- **Classless addressing:** CIDR notation (e.g., 192.168.1.0/24)
- **Private ranges:** 10.0.0.0/8, 172.16.0.0/12, 192.168.0.0/16

#### **ICMP (Internet Control Message Protocol)**
**Purpose:** Network diagnostics and error reporting

**Common ICMP Messages:**
- **Echo Request/Reply:** Ping functionality
- **Destination Unreachable:** Network/host/port unreachable
- **Time Exceeded:** TTL expired
- **Redirect:** Better route available
- **Source Quench:** Congestion control

#### **IGMP (Internet Group Management Protocol)**
**Purpose:** Multicast group management

**Functions:**
- **Join/Leave:** Multicast group membership
- **Query:** Router discovery of group members
- **Report:** Group membership responses

### **Layer 1: Network Access Layer**
**Purpose:** Physical transmission and media access

**Functions:**
- **Physical addressing:** MAC addresses
- **Media access control:** CSMA/CD, CSMA/CA
- **Error detection:** CRC checksums
- **Frame formatting:** Ethernet, Wi-Fi frames

**Common Technologies:**
- **Ethernet:** IEEE 802.3 standard
- **Wi-Fi:** IEEE 802.11 standard
- **PPP:** Point-to-Point Protocol
- **Frame Relay:** WAN technology

## Protocol Relationships

### **Common Protocol Stacks:**
1. **Web Browsing:** HTTP → TCP → IP → Ethernet
2. **Modern Web (HTTP/3):** HTTP/3 → QUIC → UDP → IP → Ethernet
3. **Email:** SMTP → TCP → IP → Ethernet
4. **File Transfer:** FTP → TCP → IP → Ethernet
5. **DNS Query:** DNS → UDP → IP → Ethernet
6. **Network Management:** SNMP → UDP → IP → Ethernet

---

## Summary

The TCP/IP protocol suite is the foundation of modern networking. Understanding the four layers and their protocols is essential for network design, troubleshooting, and management. Each layer has specific responsibilities that work together to provide reliable network communication.

**Next:** [Data Encapsulation Process](./data-encapsulation.md) 