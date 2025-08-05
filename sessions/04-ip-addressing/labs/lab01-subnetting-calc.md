# Lab 01: Subnetting Calculations

## 🎯 Objective
Learn to perform subnetting calculations manually and using tools. Develop skills in determining network addresses, broadcast addresses, valid host ranges, and subnet masks for various network requirements.

## 🛠️ Prerequisites
- Basic understanding of binary and decimal number systems
- Knowledge of IP addressing fundamentals
- Calculator (optional but recommended)
- Subnetting tools (optional)

## 📋 Lab Overview
This lab will help you:
1. Convert between binary and decimal numbers
2. Calculate subnet masks and CIDR notation
3. Determine network and broadcast addresses
4. Calculate valid host ranges
5. Perform subnetting for various network sizes

---

## Part 1: Binary and Decimal Conversion

### Step 1: Binary to Decimal Conversion
**Practice converting binary numbers to decimal:**

#### **Exercise 1: Basic Conversions**
```
Convert the following binary numbers to decimal:

1. 11000000 = ________
2. 11100000 = ________
3. 11110000 = ________
4. 11111000 = ________
5. 11111100 = ________
6. 11111110 = ________
7. 11111111 = ________
8. 10000000 = ________
```

#### **Exercise 2: IP Address Conversion**
```
Convert the following IP addresses to binary:

1. 192.168.1.0 = ________
2. 255.255.255.0 = ________
3. 255.255.255.128 = ________
4. 255.255.255.192 = ________
5. 255.255.255.224 = ________
6. 255.255.255.240 = ________
7. 255.255.255.248 = ________
8. 255.255.255.252 = ________
```

### Step 2: Decimal to Binary Conversion
**Practice converting decimal numbers to binary:**

#### **Exercise 3: Reverse Conversions**
```
Convert the following decimal numbers to binary:

1. 192 = ________
2. 224 = ________
3. 240 = ________
4. 248 = ________
5. 252 = ________
6. 254 = ________
7. 255 = ________
8. 128 = ________
```

#### **Exercise 4: Subnet Mask Conversion**
```
Convert the following subnet masks to binary:

1. 255.0.0.0 = ________
2. 255.255.0.0 = ________
3. 255.255.255.0 = ________
4. 255.255.255.128 = ________
5. 255.255.255.192 = ________
6. 255.255.255.224 = ________
7. 255.255.255.240 = ________
8. 255.255.255.248 = ________
```

---

## Part 2: Subnet Mask Calculations

### Step 1: CIDR to Subnet Mask
**Convert CIDR notation to subnet masks:**

#### **Exercise 5: CIDR Conversions**
```
Convert the following CIDR notations to subnet masks:

1. /8 = ________
2. /16 = ________
3. /24 = ________
4. /25 = ________
5. /26 = ________
6. /27 = ________
7. /28 = ________
8. /29 = ________
9. /30 = ________
10. /32 = ________
```

#### **Exercise 6: Subnet Mask to CIDR**
```
Convert the following subnet masks to CIDR notation:

1. 255.0.0.0 = ________
2. 255.255.0.0 = ________
3. 255.255.255.0 = ________
4. 255.255.255.128 = ________
5. 255.255.255.192 = ________
6. 255.255.255.224 = ________
7. 255.255.255.240 = ________
8. 255.255.255.248 = ________
9. 255.255.255.252 = ________
10. 255.255.255.255 = ________
```

### Step 2: Magic Numbers
**Learn and use magic numbers for quick calculations:**

#### **Exercise 7: Magic Number Calculations**
```
Calculate the magic number for each subnet mask:

1. /25 (255.255.255.128) = ________
2. /26 (255.255.255.192) = ________
3. /27 (255.255.255.224) = ________
4. /28 (255.255.255.240) = ________
5. /29 (255.255.255.248) = ________
6. /30 (255.255.255.252) = ________
```

#### **Exercise 8: Subnet Ranges**
```
Using magic numbers, find the subnet ranges for 192.168.1.0/26:

Subnet 0: ________ to ________
Subnet 1: ________ to ________
Subnet 2: ________ to ________
Subnet 3: ________ to ________
```

---

## Part 3: Network Address Calculations

### Step 1: AND Operations
**Perform AND operations to find network addresses:**

#### **Exercise 9: Network Address Calculation**
```
Calculate the network address for each IP/subnet combination:

1. 192.168.1.15 / 255.255.255.0 = ________
2. 192.168.1.45 / 255.255.255.192 = ________
3. 192.168.1.100 / 255.255.255.224 = ________
4. 192.168.1.200 / 255.255.255.240 = ________
5. 172.16.5.10 / 255.255.0.0 = ________
6. 10.0.15.25 / 255.0.0.0 = ________
```

#### **Exercise 10: Binary AND Operations**
```
Perform binary AND operations:

IP: 192.168.1.15 = 11000000.10101000.00000001.00001111
Mask: 255.255.255.0 = 11111111.11111111.11111111.00000000
Result: ________ = ________
```

### Step 2: Broadcast Address Calculations
**Calculate broadcast addresses:**

#### **Exercise 11: Broadcast Address Calculation**
```
Calculate the broadcast address for each network:

1. 192.168.1.0/24 = ________
2. 192.168.1.0/25 = ________
3. 192.168.1.0/26 = ________
4. 192.168.1.0/27 = ________
5. 192.168.1.0/28 = ________
6. 192.168.1.0/29 = ________
7. 192.168.1.0/30 = ________
```

#### **Exercise 12: Valid Host Ranges**
```
Calculate the valid host range for each subnet:

1. 192.168.1.0/24:
   - Network: ________
   - First Host: ________
   - Last Host: ________
   - Broadcast: ________

2. 192.168.1.0/26:
   - Network: ________
   - First Host: ________
   - Last Host: ________
   - Broadcast: ________

3. 192.168.1.0/27:
   - Network: ________
   - First Host: ________
   - Last Host: ________
   - Broadcast: ________
```

---

## Part 4: Subnetting Calculations

### Step 1: Basic Subnetting
**Subnet a network into smaller networks:**

#### **Exercise 13: Class C Subnetting**
```
Subnet 192.168.1.0/24 into 4 equal subnets:

Subnet 1:
- Network: ________
- Broadcast: ________
- Host Range: ________
- Number of Hosts: ________

Subnet 2:
- Network: ________
- Broadcast: ________
- Host Range: ________
- Number of Hosts: ________

Subnet 3:
- Network: ________
- Broadcast: ________
- Host Range: ________
- Number of Hosts: ________

Subnet 4:
- Network: ________
- Broadcast: ________
- Host Range: ________
- Number of Hosts: ________
```

#### **Exercise 14: Class B Subnetting**
```
Subnet 172.16.0.0/16 into 8 equal subnets:

Subnet 1:
- Network: ________
- Broadcast: ________
- Host Range: ________
- Number of Hosts: ________

Subnet 2:
- Network: ________
- Broadcast: ________
- Host Range: ________
- Number of Hosts: ________

(Continue for all 8 subnets)
```

### Step 2: Variable Subnetting
**Create subnets of different sizes:**

#### **Exercise 15: Variable Subnetting**
```
Subnet 192.168.1.0/24 to accommodate:
- Subnet A: 100 hosts
- Subnet B: 50 hosts
- Subnet C: 25 hosts
- Subnet D: 10 hosts

Subnet A (100 hosts):
- Network: ________
- Subnet Mask: ________
- Broadcast: ________
- Host Range: ________

Subnet B (50 hosts):
- Network: ________
- Subnet Mask: ________
- Broadcast: ________
- Host Range: ________

Subnet C (25 hosts):
- Network: ________
- Subnet Mask: ________
- Broadcast: ________
- Host Range: ________

Subnet D (10 hosts):
- Network: ________
- Subnet Mask: ________
- Broadcast: ________
- Host Range: ________
```

---

## Part 5: Advanced Subnetting

### Step 1: VLSM Calculations
**Perform Variable Length Subnet Masking:**

#### **Exercise 16: VLSM Design**
```
Design a VLSM scheme for 172.16.0.0/16 to accommodate:
- HQ: 500 hosts
- Branch 1: 200 hosts
- Branch 2: 100 hosts
- Branch 3: 50 hosts
- WAN links: 2 hosts each (5 links)

HQ (500 hosts):
- Network: ________
- Subnet Mask: ________
- Broadcast: ________
- Host Range: ________

Branch 1 (200 hosts):
- Network: ________
- Subnet Mask: ________
- Broadcast: ________
- Host Range: ________

Branch 2 (100 hosts):
- Network: ________
- Subnet Mask: ________
- Broadcast: ________
- Host Range: ________

Branch 3 (50 hosts):
- Network: ________
- Subnet Mask: ________
- Broadcast: ________
- Host Range: ________

WAN Links (2 hosts each):
- WAN 1: ________
- WAN 2: ________
- WAN 3: ________
- WAN 4: ________
- WAN 5: ________
```

### Step 2: Route Summarization
**Practice route summarization:**

#### **Exercise 17: Route Summarization**
```
Summarize the following routes:
- 192.168.1.0/24
- 192.168.2.0/24
- 192.168.3.0/24
- 192.168.4.0/24

Summary Route: ________
```

#### **Exercise 18: Complex Summarization**
```
Summarize the following routes:
- 10.1.0.0/24
- 10.1.1.0/24
- 10.1.2.0/24
- 10.1.3.0/24
- 10.1.4.0/24
- 10.1.5.0/24
- 10.1.6.0/24
- 10.1.7.0/24

Summary Route: ________
```

---

## Part 6: Practical Scenarios

### Step 1: Network Design
**Design addressing for real-world scenarios:**

#### **Scenario 1: Small Office**
```
Requirements:
- 1 network for 50 hosts
- 1 network for 25 hosts
- 1 network for 10 hosts
- 1 point-to-point link

Available Network: 192.168.1.0/24

Design your subnetting scheme:

Network 1 (50 hosts):
- Network: ________
- Subnet Mask: ________
- Host Range: ________

Network 2 (25 hosts):
- Network: ________
- Subnet Mask: ________
- Host Range: ________

Network 3 (10 hosts):
- Network: ________
- Subnet Mask: ________
- Host Range: ________

P2P Link:
- Network: ________
- Subnet Mask: ________
- Host Range: ________
```

#### **Scenario 2: Medium Business**
```
Requirements:
- 5 departments with 30 hosts each
- 1 server network with 10 hosts
- 1 guest network with 50 hosts
- 3 point-to-point links

Available Network: 172.16.0.0/16

Design your VLSM scheme:

Department Networks (30 hosts each):
- Dept 1: ________
- Dept 2: ________
- Dept 3: ________
- Dept 4: ________
- Dept 5: ________

Server Network (10 hosts):
- Network: ________

Guest Network (50 hosts):
- Network: ________

P2P Links (2 hosts each):
- P2P 1: ________
- P2P 2: ________
- P2P 3: ________
```

---

## 📊 Lab Results Template

Fill out this template with your findings:

```
=== SUBNETTING CALCULATIONS LAB ===

Date: ________
Student: ________

Part 1: Binary/Decimal Conversion
- Binary to Decimal Accuracy: ________%
- Decimal to Binary Accuracy: ________%
- IP Address Conversion Accuracy: ________%

Part 2: Subnet Mask Calculations
- CIDR to Subnet Mask Accuracy: ________%
- Subnet Mask to CIDR Accuracy: ________%
- Magic Number Calculations: ________%

Part 3: Network Address Calculations
- Network Address Accuracy: ________%
- Broadcast Address Accuracy: ________%
- Host Range Accuracy: ________%

Part 4: Basic Subnetting
- Class C Subnetting Accuracy: ________%
- Class B Subnetting Accuracy: ________%
- Variable Subnetting Accuracy: ________%

Part 5: Advanced Subnetting
- VLSM Design Accuracy: ________%
- Route Summarization Accuracy: ________%
- Complex Scenarios Accuracy: ________%

Part 6: Practical Scenarios
- Small Office Design: ________
- Medium Business Design: ________
- Overall Understanding: ________
```

---

## 🔍 Analysis Questions

1. **Binary Conversion:** What patterns did you notice when converting between binary and decimal?

2. **Magic Numbers:** How do magic numbers simplify subnetting calculations?

3. **VLSM Benefits:** What are the advantages of using VLSM over fixed-length subnetting?

4. **Route Summarization:** How does route summarization improve network performance?

5. **Practical Application:** How would you apply these skills in a real network design project?

---

## 🎓 Learning Outcomes

After completing this lab, you should understand:
- Binary and decimal number conversion
- Subnet mask and CIDR notation calculations
- Network and broadcast address determination
- Valid host range calculations
- Basic and advanced subnetting techniques
- VLSM design and implementation
- Route summarization methods

---

## 🛠️ Recommended Tools

### **Calculation Tools:**
- **Scientific Calculator:** Binary/decimal conversion
- **Subnet Calculator:** Online tools for verification
- **Spreadsheet Software:** Excel/Google Sheets for calculations
- **Network Design Software:** Professional tools

### **Practice Tools:**
- **Online Subnetting Practice:** Interactive exercises
- **Mobile Apps:** Subnetting calculators
- **Flashcards:** Binary/decimal conversion practice
- **Simulation Software:** Network design tools

### **Reference Materials:**
- **Subnetting Charts:** Quick reference guides
- **Binary Tables:** Conversion reference
- **Magic Number Tables:** Subnetting shortcuts
- **Practice Problems:** Additional exercises

---

## ⚠️ Important Notes

### **Best Practices:**
- **Practice regularly** to maintain skills
- **Use multiple methods** to verify calculations
- **Document your work** for future reference
- **Understand the concepts** rather than memorizing
- **Apply to real scenarios** for practical experience

### **Common Mistakes:**
- **Forgetting to subtract 2** for usable hosts
- **Incorrect binary conversion** leading to wrong addresses
- **Confusing network and broadcast** addresses
- **Not considering growth** in subnet design
- **Overlapping subnets** in VLSM design

---

**Next Lab:** [Lab 02: VLSM Design](./lab02-vlsm-design.md) 