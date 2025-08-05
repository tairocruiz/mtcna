# Quiz: Ethernet and Switching

## 📝 Instructions
- **Time Limit:** 25 minutes
- **Total Questions:** 20 (15 Multiple Choice, 5 Short Answer)
- **Passing Score:** 70% (14/20 correct)
- **Calculator:** Allowed for subnetting questions
- **Notes:** Not allowed during quiz

---

## 🔢 Multiple Choice Questions (15 points)

### **Question 1** (1 point)
What is the purpose of the preamble in an Ethernet frame?
- A) Error detection
- B) Clock synchronization
- C) Address identification
- D) Data encapsulation

### **Question 2** (1 point)
Which field in an Ethernet frame contains the destination MAC address?
- A) First 6 bytes after SFD
- B) Last 6 bytes before FCS
- C) 2 bytes after Type field
- D) 4 bytes before Data field

### **Question 3** (1 point)
What is the maximum size of the data payload in a standard Ethernet frame?
- A) 46 bytes
- B) 1500 bytes
- C) 1518 bytes
- D) 1522 bytes

### **Question 4** (1 point)
Which MAC address type is used for one-to-many communication?
- A) Unicast
- B) Broadcast
- C) Multicast
- D) Anycast

### **Question 5** (1 point)
What does the OUI (Organizationally Unique Identifier) represent in a MAC address?
- A) Device serial number
- B) Manufacturer identifier
- C) Network address
- D) Protocol type

### **Question 6** (1 point)
Which switching method checks the entire frame for errors before forwarding?
- A) Cut-through
- B) Store-and-forward
- C) Fragment-free
- D) Fast-forward

### **Question 7** (1 point)
What is the purpose of the MAC address table in a switch?
- A) Store IP addresses
- B) Map MAC addresses to ports
- C) Route packets
- D) Filter traffic

### **Question 8** (1 point)
Which device creates separate collision domains?
- A) Hub
- B) Switch
- C) Repeater
- D) Bridge

### **Question 9** (1 point)
What is the broadcast address in Ethernet?
- A) 00:00:00:00:00:00
- B) FF:FF:FF:FF:FF:FF
- C) 01:00:5E:00:00:00
- D) 33:33:00:00:00:00

### **Question 10** (1 point)
Which protocol maps IP addresses to MAC addresses?
- A) DHCP
- B) DNS
- C) ARP
- D) RARP

### **Question 11** (1 point)
What is the purpose of VLANs?
- A) Increase network speed
- B) Logical network segmentation
- C) Reduce cable length
- D) Improve signal quality

### **Question 12** (1 point)
Which port type carries traffic for multiple VLANs?
- A) Access port
- B) Trunk port
- C) Hybrid port
- D) Native port

### **Question 13** (1 point)
What is the default native VLAN on most switches?
- A) VLAN 1
- B) VLAN 10
- C) VLAN 100
- D) VLAN 1000

### **Question 14** (1 point)
Which switching method has the lowest latency?
- A) Store-and-forward
- B) Cut-through
- C) Fragment-free
- D) Adaptive switching

### **Question 15** (1 point)
What is the purpose of CSMA/CD in Ethernet?
- A) Error detection
- B) Collision detection
- C) Address resolution
- D) Frame synchronization

---

## ✍️ Short Answer Questions (5 points)

### **Question 16** (1 point)
Explain the difference between a collision domain and a broadcast domain.

### **Question 17** (1 point)
Describe the three main switching methods and their advantages/disadvantages.

### **Question 18** (1 point)
What is the purpose of the FCS field in an Ethernet frame and how does it work?

### **Question 19** (1 point)
Explain how a switch learns MAC addresses and builds its address table.

### **Question 20** (1 point)
What are the benefits of using VLANs in a network design?

---

## 📋 Answer Key

### **Multiple Choice Answers:**
1. B) Clock synchronization
2. A) First 6 bytes after SFD
3. B) 1500 bytes
4. C) Multicast
5. B) Manufacturer identifier
6. B) Store-and-forward
7. B) Map MAC addresses to ports
8. B) Switch
9. B) FF:FF:FF:FF:FF:FF
10. C) ARP
11. B) Logical network segmentation
12. B) Trunk port
13. A) VLAN 1
14. B) Cut-through
15. B) Collision detection

### **Short Answer Sample Responses:**

#### **Question 16:**
**Collision Domain:** Area where collisions can occur. In traditional Ethernet, all devices on a shared medium (like a hub) are in the same collision domain. Switches create separate collision domains for each port.

**Broadcast Domain:** Area where broadcast frames are forwarded. All devices that receive broadcast frames are in the same broadcast domain. VLANs and routers create separate broadcast domains.

#### **Question 17:**
**Store-and-Forward:** Receives entire frame, checks for errors, then forwards. Advantages: Error detection, support for different speeds. Disadvantages: Higher latency, more processing.

**Cut-Through:** Reads destination address and starts forwarding immediately. Advantages: Lowest latency, fast processing. Disadvantages: No error filtering, bad frames forwarded.

**Fragment-Free:** Reads first 64 bytes (minimum frame size) before forwarding. Advantages: Fast forwarding, collision fragment filtering. Disadvantages: Limited error detection.

#### **Question 18:**
**FCS (Frame Check Sequence):** 4-byte field containing a CRC-32 checksum calculated over all fields except preamble and SFD. Used for error detection. If the calculated checksum doesn't match the received FCS, the frame is discarded.

#### **Question 19:**
Switch learns MAC addresses by examining the source MAC address of incoming frames. When a frame arrives on a port, the switch adds the source MAC address and port number to its address table. The table is used to forward future frames to the correct port. Entries age out after a specified time.

#### **Question 20:**
**Benefits of VLANs:**
- **Security:** Isolate traffic between different groups
- **Performance:** Reduce broadcast domains and improve network efficiency
- **Management:** Simplify network administration and troubleshooting
- **Flexibility:** Logical grouping independent of physical location
- **Scalability:** Easy to add/remove devices from VLANs

---

## 📊 Scoring Guide

### **Total Points: 20**
- **Multiple Choice:** 15 points (1 point each)
- **Short Answer:** 5 points (1 point each)

### **Grade Scale:**
- **90-100% (18-20 points):** Excellent understanding
- **80-89% (16-17 points):** Good understanding
- **70-79% (14-15 points):** Satisfactory understanding
- **60-69% (12-13 points):** Needs improvement
- **Below 60% (<12 points):** Requires review

### **Performance Analysis:**
- **Questions 1-5:** Ethernet fundamentals
- **Questions 6-10:** Switching concepts
- **Questions 11-15:** VLANs and advanced concepts
- **Questions 16-20:** Conceptual understanding

---

## 🔍 Review Topics

If you scored below 70%, review these topics:

### **Ethernet Fundamentals:**
- Frame structure and fields
- MAC addressing
- CSMA/CD operation
- Ethernet standards and speeds

### **Switching Concepts:**
- Switch operation and forwarding
- MAC address table learning
- Switching methods
- Collision and broadcast domains

### **VLANs:**
- VLAN configuration and management
- Trunk ports and tagging
- Inter-VLAN routing
- VLAN security

### **ARP and Addressing:**
- Address Resolution Protocol
- MAC address types
- ARP cache management
- Network addressing concepts

---

## 📚 Additional Resources

### **Recommended Reading:**
- Ethernet frame structure documentation
- Switch configuration guides
- VLAN design best practices
- Network troubleshooting guides

### **Practice Labs:**
- Switch configuration exercises
- VLAN setup and testing
- Network monitoring and analysis
- Troubleshooting scenarios

---

**Next Session:** [Session 04: IP Addressing and Subnetting](../04-ip-addressing/) 