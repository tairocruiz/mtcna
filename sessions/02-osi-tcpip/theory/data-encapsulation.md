# Data Encapsulation Process

## What is Data Encapsulation?

**Data encapsulation** is the process of adding protocol headers and trailers to data as it moves down through the OSI model layers. Each layer adds its own control information to help with delivery, routing, and error detection.

## The Encapsulation Process

### **Step-by-Step Process:**

#### **1. Application Layer (Layer 7)**
**Input:** User data (e.g., "Hello World")
**Process:** Application adds application-specific headers
**Output:** Application PDU (Protocol Data Unit)

```
[Application Header] + [User Data]
```

#### **2. Presentation Layer (Layer 6)**
**Input:** Application PDU
**Process:** Adds formatting, encryption, compression headers
**Output:** Presentation PDU

```
[Presentation Header] + [Application Header] + [User Data]
```

#### **3. Session Layer (Layer 5)**
**Input:** Presentation PDU
**Process:** Adds session management headers
**Output:** Session PDU

```
[Session Header] + [Presentation Header] + [Application Header] + [User Data]
```

#### **4. Transport Layer (Layer 4)**
**Input:** Session PDU
**Process:** Adds transport headers (TCP/UDP)
**Output:** Segment (TCP) or Datagram (UDP)

```
[Transport Header] + [Session Header] + [Presentation Header] + [Application Header] + [User Data]
```

#### **5. Network Layer (Layer 3)**
**Input:** Transport PDU
**Process:** Adds network headers (IP)
**Output:** Packet

```
[Network Header] + [Transport Header] + [Session Header] + [Presentation Header] + [Application Header] + [User Data]
```

#### **6. Data Link Layer (Layer 2)**
**Input:** Network PDU
**Process:** Adds data link headers and trailers (Ethernet)
**Output:** Frame

```
[Data Link Header] + [Network Header] + [Transport Header] + [Session Header] + [Presentation Header] + [Application Header] + [User Data] + [Data Link Trailer]
```

#### **7. Physical Layer (Layer 1)**
**Input:** Data Link PDU
**Process:** Converts to bits and transmits
**Output:** Bits

## Real-World Example: HTTP Web Request

### **Complete Encapsulation Process:**

#### **Step 1: Application Layer**
```
HTTP Request:
GET /index.html HTTP/1.1
Host: www.example.com
User-Agent: Mozilla/5.0
```

#### **Step 2: Transport Layer (TCP)**
```
TCP Header:
Source Port: 49152
Destination Port: 80
Sequence Number: 1000
Acknowledgment Number: 0
Flags: SYN
Window Size: 65535
Checksum: 0x1234

[TCP Header] + [HTTP Request]
```

#### **Step 3: Network Layer (IP)**
```
IP Header:
Version: 4
Header Length: 5
Total Length: 60
TTL: 64
Protocol: TCP (6)
Source Address: 192.168.1.100
Destination Address: 93.184.216.34
Checksum: 0x5678

[IP Header] + [TCP Header] + [HTTP Request]
```

#### **Step 4: Data Link Layer (Ethernet)**
```
Ethernet Header:
Destination MAC: 00:11:22:33:44:55
Source MAC: AA:BB:CC:DD:EE:FF
Type: 0x0800 (IPv4)

Ethernet Trailer:
CRC: 0x9ABC

[Ethernet Header] + [IP Header] + [TCP Header] + [HTTP Request] + [Ethernet Trailer]
```

#### **Step 5: Physical Layer**
```
Transmitted as bits:
10101010 10101010 10101010 10101010...
```

## De-encapsulation Process

### **Reverse Process:**
1. **Physical Layer:** Receives bits, converts to frame
2. **Data Link Layer:** Removes Ethernet header/trailer, checks CRC
3. **Network Layer:** Removes IP header, checks destination
4. **Transport Layer:** Removes TCP/UDP header, reassembles if needed
5. **Session Layer:** Removes session header
6. **Presentation Layer:** Removes presentation header, decrypts if needed
7. **Application Layer:** Removes application header, delivers to application

## PDU Names by Layer

### **OSI Model PDU Names:**
- **Layer 7 (Application):** Data
- **Layer 6 (Presentation):** Data
- **Layer 5 (Session):** Data
- **Layer 4 (Transport):** Segment (TCP) / Datagram (UDP)
- **Layer 3 (Network):** Packet
- **Layer 2 (Data Link):** Frame
- **Layer 1 (Physical):** Bits

### **TCP/IP Model PDU Names:**
- **Application Layer:** Data
- **Transport Layer:** Segment (TCP) / Datagram (UDP)
- **Internet Layer:** Packet
- **Network Access Layer:** Frame

## Header Information at Each Layer

### **Application Layer Headers:**
- **HTTP:** Method, URL, headers, cookies
- **FTP:** Commands, file information
- **SMTP:** Email addresses, message headers
- **DNS:** Query type, domain name

### **Transport Layer Headers:**
- **TCP:** Ports, sequence numbers, flags, window size
- **UDP:** Ports, length, checksum

### **Network Layer Headers:**
- **IP:** Source/destination addresses, TTL, protocol
- **ICMP:** Type, code, checksum

### **Data Link Layer Headers:**
- **Ethernet:** MAC addresses, type, VLAN tags
- **Wi-Fi:** MAC addresses, frame control, sequence

## Practical Implications

### **Troubleshooting:**
- **Layer 1 issues:** Physical connectivity, cable problems
- **Layer 2 issues:** MAC addressing, switching problems
- **Layer 3 issues:** IP addressing, routing problems
- **Layer 4 issues:** Port connectivity, firewall rules
- **Layer 5-7 issues:** Application configuration, protocols

### **Security:**
- **Layer 2:** MAC filtering, VLANs
- **Layer 3:** IP filtering, routing security
- **Layer 4:** Port filtering, connection tracking
- **Layer 5-7:** Application security, encryption

### **Performance:**
- **Layer 1:** Bandwidth, signal quality
- **Layer 2:** Switching speed, collision domains
- **Layer 3:** Routing efficiency, path selection
- **Layer 4:** Connection management, flow control
- **Layer 5-7:** Application optimization, caching

## Common Encapsulation Scenarios

### **1. Web Browsing (HTTP over TCP/IP):**
```
HTTP Request → TCP Segment → IP Packet → Ethernet Frame → Bits
```

### **2. Email (SMTP over TCP/IP):**
```
SMTP Command → TCP Segment → IP Packet → Ethernet Frame → Bits
```

### **3. DNS Query (DNS over UDP/IP):**
```
DNS Query → UDP Datagram → IP Packet → Ethernet Frame → Bits
```

### **4. File Transfer (FTP over TCP/IP):**
```
FTP Command → TCP Segment → IP Packet → Ethernet Frame → Bits
```

---

## Summary

Data encapsulation is fundamental to network communication. Understanding how data is wrapped with protocol headers at each layer helps with troubleshooting, security implementation, and network design. Each layer adds specific information needed for proper delivery and processing of the data.

**Next:** [Quiz: OSI Model and TCP/IP](../quiz/osi-tcpip-quiz.md) 