# IP Address Cheat Sheet

## 🎯 Overview
This cheat sheet provides quick reference for IP addressing, subnetting, and network calculations commonly used in networking.

## 📋 IP Address Classes

### **Class A**
```
Range: 1.0.0.0 - 126.255.255.255
Default Mask: 255.0.0.0 (/8)
Network Bits: 8
Host Bits: 24
Total Networks: 126
Hosts per Network: 16,777,214
Private Range: 10.0.0.0 - 10.255.255.255
```

### **Class B**
```
Range: 128.0.0.0 - 191.255.255.255
Default Mask: 255.255.0.0 (/16)
Network Bits: 16
Host Bits: 16
Total Networks: 16,384
Hosts per Network: 65,534
Private Range: 172.16.0.0 - 172.31.255.255
```

### **Class C**
```
Range: 192.0.0.0 - 223.255.255.255
Default Mask: 255.255.255.0 (/24)
Network Bits: 24
Host Bits: 8
Total Networks: 2,097,152
Hosts per Network: 254
Private Range: 192.168.0.0 - 192.168.255.255
```

### **Class D (Multicast)**
```
Range: 224.0.0.0 - 239.255.255.255
Purpose: Multicast addresses
No default mask
```

### **Class E (Reserved)**
```
Range: 240.0.0.0 - 255.255.255.255
Purpose: Reserved for future use
No default mask
```

---

## 🔢 Subnet Mask Reference

### **Common Subnet Masks**
```
/8   = 255.0.0.0         (Class A default)
/16  = 255.255.0.0       (Class B default)
/24  = 255.255.255.0     (Class C default)
/25  = 255.255.255.128   (128 hosts)
/26  = 255.255.255.192   (64 hosts)
/27  = 255.255.255.224   (32 hosts)
/28  = 255.255.255.240   (16 hosts)
/29  = 255.255.255.248   (8 hosts)
/30  = 255.255.255.252   (4 hosts)
/31  = 255.255.255.254   (2 hosts)
/32  = 255.255.255.255   (1 host)
```

### **Magic Numbers**
```
/25 = 128 (256 - 128)
/26 = 64  (256 - 192)
/27 = 32  (256 - 224)
/28 = 16  (256 - 240)
/29 = 8   (256 - 248)
/30 = 4   (256 - 252)
/31 = 2   (256 - 254)
/32 = 1   (256 - 255)
```

---

## 📊 Subnetting Quick Reference

### **Hosts per Subnet**
```
/24 = 254 hosts (256 - 2)
/25 = 126 hosts (128 - 2)
/26 = 62 hosts  (64 - 2)
/27 = 30 hosts  (32 - 2)
/28 = 14 hosts  (16 - 2)
/29 = 6 hosts   (8 - 2)
/30 = 2 hosts   (4 - 2)
/31 = 2 hosts   (2 - 0, special case)
/32 = 1 host    (1 - 0, special case)
```

### **Subnets per Network**
```
Class C (/24) divided by:
/25 = 2 subnets
/26 = 4 subnets
/27 = 8 subnets
/28 = 16 subnets
/29 = 32 subnets
/30 = 64 subnets

Class B (/16) divided by:
/17 = 2 subnets
/18 = 4 subnets
/19 = 8 subnets
/20 = 16 subnets
/21 = 32 subnets
/22 = 64 subnets
/23 = 128 subnets
/24 = 256 subnets
```

---

## 🔄 Binary to Decimal Conversion

### **Quick Conversion Table**
```
Binary    | Decimal | Binary    | Decimal
----------|---------|-----------|---------
00000000  | 0       | 10000000  | 128
00000001  | 1       | 10000001  | 129
00000010  | 2       | 10000010  | 130
00000100  | 4       | 10000100  | 132
00001000  | 8       | 10001000  | 136
00010000  | 16      | 10010000  | 144
00100000  | 32      | 10100000  | 160
01000000  | 64      | 11000000  | 192
```

### **Subnet Mask Binary**
```
/24 = 11111111.11111111.11111111.00000000
/25 = 11111111.11111111.11111111.10000000
/26 = 11111111.11111111.11111111.11000000
/27 = 11111111.11111111.11111111.11100000
/28 = 11111111.11111111.11111111.11110000
/29 = 11111111.11111111.11111111.11111000
/30 = 11111111.11111111.11111111.11111100
/31 = 11111111.11111111.11111111.11111110
/32 = 11111111.11111111.11111111.11111111
```

---

## 🏗️ Network Address Calculations

### **Quick Formulas**
```
Network Address = IP Address AND Subnet Mask
Broadcast Address = Network Address + (2^host_bits - 1)
First Host = Network Address + 1
Last Host = Broadcast Address - 1
Number of Hosts = 2^host_bits - 2
```

### **Common Network Addresses**
```
Class C (/24) Examples:
192.168.1.0/24:
- Network: 192.168.1.0
- Broadcast: 192.168.1.255
- Hosts: 192.168.1.1 - 192.168.1.254

192.168.1.0/25:
- Network: 192.168.1.0
- Broadcast: 192.168.1.127
- Hosts: 192.168.1.1 - 192.168.1.126

192.168.1.0/26:
- Network: 192.168.1.0
- Broadcast: 192.168.1.63
- Hosts: 192.168.1.1 - 192.168.1.62
```

---

## 🌐 Special IP Addresses

### **Private Addresses**
```
Class A Private: 10.0.0.0 - 10.255.255.255
Class B Private: 172.16.0.0 - 172.31.255.255
Class C Private: 192.168.0.0 - 192.168.255.255
```

### **Reserved Addresses**
```
Loopback: 127.0.0.0 - 127.255.255.255
Link Local: 169.254.0.0 - 169.254.255.255
Test Net: 192.0.2.0 - 192.0.2.255
Documentation: 203.0.113.0 - 203.0.113.255
```

### **Broadcast Addresses**
```
Limited Broadcast: 255.255.255.255
Network Broadcast: Last address in subnet
Directed Broadcast: Network address with all host bits = 1
```

---

## 🔧 VLSM Quick Reference

### **VLSM Allocation Order**
```
1. Allocate largest subnets first
2. Use smallest possible masks
3. Ensure no overlap
4. Document allocations
5. Reserve space for growth
```

### **Common VLSM Sizes**
```
Large Networks: /16, /17, /18, /19, /20
Medium Networks: /21, /22, /23, /24, /25
Small Networks: /26, /27, /28, /29
Point-to-Point: /30, /31
Single Host: /32
```

### **VLSM Example**
```
Network: 192.168.1.0/24
Requirements:
- 100 hosts: 192.168.1.0/25 (126 hosts)
- 50 hosts: 192.168.1.128/26 (62 hosts)
- 25 hosts: 192.168.1.192/27 (30 hosts)
- 10 hosts: 192.168.1.224/28 (14 hosts)
```

---

## 📈 Route Summarization

### **Summarization Rules**
```
1. Routes must be contiguous
2. All routes must share common bits
3. Summary mask covers all routes
4. No routes outside summary range
```

### **Common Summarization**
```
/24 routes → /22 summary:
- 192.168.0.0/24
- 192.168.1.0/24
- 192.168.2.0/24
- 192.168.3.0/24
Summary: 192.168.0.0/22

/24 routes → /20 summary:
- 192.168.0.0/24 to 192.168.15.0/24
Summary: 192.168.0.0/20
```

---

## 🛡️ Security Considerations

### **Network Segmentation**
```
DMZ Networks: Public-facing services
Trusted Networks: Internal resources
Untrusted Networks: External connections
Management Networks: Network devices only
```

### **Common Subnet Sizes**
```
DMZ: /24, /25, /26
Trusted: /24, /25, /26, /27
Management: /28, /29
Point-to-Point: /30
```

---

## 🔍 Troubleshooting Reference

### **Common Issues**
```
Overlapping Subnets: Routes conflict
Incorrect Mask: Wrong network boundaries
Broadcast Storms: Too many hosts per subnet
Routing Loops: Incorrect route summarization
```

### **Verification Commands**
```
Windows:
- ipconfig /all
- route print
- ping [address]

Linux:
- ifconfig
- ip addr
- route -n
- ping [address]

Cisco:
- show ip interface brief
- show ip route
- ping [address]
```

---

## 📊 Network Design Guidelines

### **Subnet Sizing**
```
Large Networks: /16 to /20
Medium Networks: /21 to /24
Small Networks: /25 to /27
Workgroups: /28 to /29
Point-to-Point: /30
Single Host: /32
```

### **Growth Planning**
```
Reserve 20-30% for growth
Plan for 3-5 year expansion
Consider technology changes
Document growth assumptions
```

### **Documentation**
```
Network diagrams
IP addressing plan
Subnet assignments
Device inventory
Change procedures
```

---

## 🎓 Quick Calculation Methods

### **Network Address (Quick Method)**
```
1. Convert IP to binary
2. Convert mask to binary
3. Perform AND operation
4. Convert result to decimal
```

### **Broadcast Address (Quick Method)**
```
1. Find network address
2. Add magic number - 1
3. Or set all host bits to 1
```

### **Number of Hosts (Quick Method)**
```
1. Count host bits in mask
2. Calculate 2^host_bits
3. Subtract 2 (network + broadcast)
```

### **Subnet Ranges (Quick Method)**
```
1. Start with 0
2. Add magic number for each subnet
3. Continue until network exhausted
```

---

## ⚠️ Important Notes

### **Best Practices**
- Always verify calculations
- Document subnet assignments
- Plan for growth
- Use consistent naming
- Implement security boundaries

### **Common Mistakes**
- Forgetting to subtract 2 for hosts
- Incorrect binary conversion
- Overlapping subnets
- Wrong subnet mask
- Confusing network/broadcast

### **Validation Checklist**
- [ ] Network address correct
- [ ] Broadcast address correct
- [ ] Host range valid
- [ ] No overlapping subnets
- [ ] Sufficient host capacity
- [ ] Growth space reserved

---

## 📚 Additional Resources

### **Online Tools**
- Subnet-calculator.com
- IPCalculator.com
- SolarWinds Subnet Calculator
- Cisco Subnet Calculator

### **Command Line Tools**
- ipcalc (Linux)
- sipcalc (Linux)
- PowerShell (Windows)
- Network Utility (macOS)

### **Mobile Apps**
- Subnet Calculator
- IP Calculator
- Network Tools
- Subnetting Practice

---

**Note:** This cheat sheet provides quick reference for common subnetting calculations. Always verify results and consider specific network requirements when designing addressing schemes. 