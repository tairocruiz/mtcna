# Quiz: OSI Model and TCP/IP

## Instructions
- Choose the best answer for each question
- Some questions may have multiple correct answers
- Check your answers at the end

---

## Questions

### 1. How many layers does the OSI model have?
a) 4 layers
b) 5 layers
c) 7 layers
d) 8 layers

### 2. Which layer of the OSI model is responsible for logical addressing?
a) Physical Layer
b) Data Link Layer
c) Network Layer
d) Transport Layer

### 3. What is the PDU (Protocol Data Unit) name for the Transport layer?
a) Frame
b) Packet
c) Segment
d) Bits

### 4. Which protocol operates at the Transport layer?
a) IP
b) TCP
c) HTTP
d) Ethernet

### 15. What is the purpose of the checksum field in TCP?
a) To ensure data integrity
b) To route packets
c) To establish connections
d) To compress data

### 16. Which modern protocol is built on top of UDP and provides reliable, encrypted connections?
a) TCP
b) QUIC
c) SCTP
d) DCCP

### 5. What is the purpose of the Presentation layer?
a) To establish sessions between applications
b) To ensure data is readable by the receiving system
c) To provide network services to applications
d) To handle physical transmission

### 6. Which layer is responsible for MAC addressing?
a) Network Layer
b) Data Link Layer
c) Physical Layer
d) Transport Layer

### 7. What does TCP stand for?
a) Transmission Control Protocol
b) Transfer Control Protocol
c) Transport Control Protocol
d) Transfer Connection Protocol

### 8. Which of the following is a connectionless protocol?
a) TCP
b) UDP
c) HTTP
d) FTP

### 9. What port number is typically used for HTTP?
a) 21
b) 25
c) 80
d) 443

### 10. Which layer of the TCP/IP model corresponds to the OSI Network layer?
a) Application Layer
b) Transport Layer
c) Internet Layer
d) Network Access Layer

### 11. What is the purpose of the three-way handshake in TCP?
a) To establish a connection
b) To terminate a connection
c) To transfer data
d) To check network connectivity

### 12. Which protocol is used for name resolution?
a) HTTP
b) FTP
c) DNS
d) SMTP

### 13. What is the maximum value for the TTL field in an IP header?
a) 64
b) 128
c) 255
d) 1024

### 14. Which layer adds the Ethernet header and trailer?
a) Network Layer
b) Data Link Layer
c) Physical Layer
d) Transport Layer

### 15. What is the purpose of the checksum field in TCP?
a) To ensure data integrity
b) To route packets
c) To establish connections
d) To compress data

### 16. Which modern protocol is built on top of UDP and provides reliable, encrypted connections?
a) TCP
b) QUIC
c) SCTP
d) DCCP

### 17. Why can't you download a 1GB file in exactly 1 second on a 1Gbps connection?
a) Because of protocol overhead and headers
b) Because the file is compressed
c) Because of network congestion
d) Because of server limitations

### 18. What is the typical protocol overhead percentage for small HTTP requests?
a) 5-10%
b) 20-30%
c) 50-60%
d) 80-90%

---

## Short Answer Questions

### 16. List the seven layers of the OSI model from top to bottom.
```
1. _________________________________
2. _________________________________
3. _________________________________
4. _________________________________
5. _________________________________
6. _________________________________
7. _________________________________
```

### 17. Explain the difference between TCP and UDP.
```
TCP: _________________________________
_________________________________________

UDP: __________________________________
_________________________________________
```

### 18. What is data encapsulation and why is it important?
```
Encapsulation: _________________________
_________________________________________

Importance: ____________________________
_________________________________________
```

### 19. Name three protocols that operate at the Application layer.
```
1. _________________________________
2. _________________________________
3. _________________________________
```

### 20. What is the purpose of the TTL field in an IP header?
```
Purpose: _______________________________
_________________________________________
```

---

## Answer Key

### Multiple Choice Answers:
1. c) 7 layers
2. c) Network Layer
3. c) Segment
4. b) TCP
5. b) To ensure data is readable by the receiving system
6. b) Data Link Layer
7. a) Transmission Control Protocol
8. b) UDP
9. c) 80
10. c) Internet Layer
11. a) To establish a connection
12. c) DNS
13. c) 255
14. b) Data Link Layer
15. a) To ensure data integrity
16. b) QUIC
17. a) Because of protocol overhead and headers
18. d) 80-90%

### Short Answer Sample Answers:

**16. OSI Model Layers:**
1. Application Layer
2. Presentation Layer
3. Session Layer
4. Transport Layer
5. Network Layer
6. Data Link Layer
7. Physical Layer

**17. TCP vs UDP:**
- TCP: Connection-oriented, reliable, ordered delivery, flow control, error checking
- UDP: Connectionless, unreliable, unordered delivery, lightweight, fast

**18. Data Encapsulation:**
- Encapsulation: Process of adding protocol headers and trailers to data as it moves down through OSI layers
- Importance: Enables proper routing, error detection, and protocol-specific processing at each layer

**19. Application Layer Protocols:**
- HTTP, FTP, SMTP, DNS, DHCP, SNMP, Telnet, SSH

**20. TTL Purpose:**
- Prevents packets from circulating indefinitely in the network by limiting the number of hops a packet can traverse

---

## Scoring Guide
- **16-18 correct:** Excellent understanding
- **13-15 correct:** Good understanding, review missed topics
- **10-12 correct:** Fair understanding, additional study needed
- **Below 10:** Review all materials before proceeding

---

**Next:** [Session 03: Ethernet and Switching Concepts](../../03-ethernet-switching/) 