# Quiz: IP Addressing and Subnetting

## 📝 Instructions
- **Time Limit:** 30 minutes
- **Total Questions:** 25 (20 Multiple Choice, 5 Short Answer)
- **Passing Score:** 70% (18/25 correct)
- **Calculator:** Allowed for calculations
- **Notes:** Not allowed during quiz

---

## 🔢 Multiple Choice Questions (20 points)

### **Question 1** (1 point)
What is the binary representation of the decimal number 192?
- A) 11000000
- B) 10101010
- C) 11110000
- D) 10000000

### **Question 2** (1 point)
Which of the following is a valid Class A private IP address range?
- A) 192.168.0.0 - 192.168.255.255
- B) 172.16.0.0 - 172.31.255.255
- C) 10.0.0.0 - 10.255.255.255
- D) 169.254.0.0 - 169.254.255.255

### **Question 3** (1 point)
What is the subnet mask for a /26 network?
- A) 255.255.255.192
- B) 255.255.255.128
- C) 255.255.255.224
- D) 255.255.255.240

### **Question 4** (1 point)
How many usable host addresses are available in a /28 subnet?
- A) 14
- B) 16
- C) 30
- D) 32

### **Question 5** (1 point)
What is the network address for 192.168.1.15/26?
- A) 192.168.1.0
- B) 192.168.1.64
- C) 192.168.1.128
- D) 192.168.1.192

### **Question 6** (1 point)
What is the broadcast address for 192.168.1.0/25?
- A) 192.168.1.127
- B) 192.168.1.128
- C) 192.168.1.255
- D) 192.168.1.0

### **Question 7** (1 point)
Which CIDR notation represents the subnet mask 255.255.255.240?
- A) /26
- B) /27
- C) /28
- D) /29

### **Question 8** (1 point)
What is the first usable host address in subnet 172.16.1.0/24?
- A) 172.16.1.0
- B) 172.16.1.1
- C) 172.16.1.255
- D) 172.16.0.1

### **Question 9** (1 point)
How many subnets can be created from a /24 network using a /26 mask?
- A) 2
- B) 4
- C) 6
- D) 8

### **Question 10** (1 point)
What is the magic number for a /27 subnet?
- A) 32
- B) 64
- C) 128
- D) 256

### **Question 11** (1 point)
Which of the following is the correct valid host range for 192.168.1.0/26?
- A) 192.168.1.0 - 192.168.1.63
- B) 192.168.1.1 - 192.168.1.62
- C) 192.168.1.0 - 192.168.1.62
- D) 192.168.1.1 - 192.168.1.63

### **Question 12** (1 point)
What is the purpose of VLSM?
- A) To increase network speed
- B) To improve address utilization
- C) To reduce routing table size
- D) To enhance security

### **Question 13** (1 point)
Which of the following represents route summarization?
- A) 192.168.1.0/24, 192.168.2.0/24, 192.168.3.0/24 → 192.168.0.0/22
- B) 192.168.1.0/24 → 192.168.1.0/25, 192.168.1.128/25
- C) 192.168.1.0/24 → 192.168.1.0/26, 192.168.1.64/26
- D) 192.168.1.0/24 → 192.168.1.0/27, 192.168.1.32/27

### **Question 14** (1 point)
What is the binary representation of the subnet mask 255.255.255.224?
- A) 11111111.11111111.11111111.11100000
- B) 11111111.11111111.11111111.11000000
- C) 11111111.11111111.11111111.10000000
- D) 11111111.11111111.11111111.00000000

### **Question 15** (1 point)
How many bits are borrowed to create 8 subnets from a /24 network?
- A) 2 bits
- B) 3 bits
- C) 4 bits
- D) 5 bits

### **Question 16** (1 point)
What is the last usable host address in subnet 10.0.1.0/25?
- A) 10.0.1.126
- B) 10.0.1.127
- C) 10.0.1.128
- D) 10.0.1.255

### **Question 17** (1 point)
Which subnet mask provides the most host addresses?
- A) /24
- B) /25
- C) /26
- D) /27

### **Question 18** (1 point)
What is the network address for 172.16.5.10/16?
- A) 172.16.0.0
- B) 172.16.5.0
- C) 172.0.0.0
- D) 172.16.5.10

### **Question 19** (1 point)
How many hosts can be accommodated in a /29 subnet?
- A) 6
- B) 8
- C) 14
- D) 16

### **Question 20** (1 point)
What is the purpose of the broadcast address?
- A) To identify the network
- B) To send traffic to all hosts in the subnet
- C) To route traffic between networks
- D) To identify the gateway

---

## ✍️ Short Answer Questions (5 points)

### **Question 21** (1 point)
Explain the difference between a network address and a broadcast address.

### **Question 22** (1 point)
Describe the process of calculating the number of usable hosts in a subnet.

### **Question 23** (1 point)
What are the benefits of using VLSM over fixed-length subnetting?

### **Question 24** (1 point)
Explain how route summarization works and its benefits.

### **Question 25** (1 point)
Describe the steps involved in designing a VLSM scheme for a network.

---

## 📋 Answer Key

### **Multiple Choice Answers:**
1. A) 11000000
2. C) 10.0.0.0 - 10.255.255.255
3. A) 255.255.255.192
4. A) 14
5. A) 192.168.1.0
6. A) 192.168.1.127
7. C) /28
8. B) 172.16.1.1
9. B) 4
10. A) 32
11. B) 192.168.1.1 - 192.168.1.62
12. B) To improve address utilization
13. A) 192.168.1.0/24, 192.168.2.0/24, 192.168.3.0/24 → 192.168.0.0/22
14. A) 11111111.11111111.11111111.11100000
15. B) 3 bits
16. A) 10.0.1.126
17. A) /24
18. A) 172.16.0.0
19. A) 6
20. B) To send traffic to all hosts in the subnet

### **Short Answer Sample Responses:**

#### **Question 21:**
**Network Address:** The first address in a subnet where all host bits are set to 0. It identifies the subnet and is not usable for hosts.

**Broadcast Address:** The last address in a subnet where all host bits are set to 1. It is used to send traffic to all hosts in the subnet and is not usable for hosts.

#### **Question 22:**
**Process:**
1. Determine the number of host bits in the subnet mask
2. Calculate 2^host_bits
3. Subtract 2 (for network and broadcast addresses)
4. Result is the number of usable host addresses

**Example:** /26 subnet has 6 host bits
2^6 = 64
64 - 2 = 62 usable hosts

#### **Question 23:**
**Benefits of VLSM:**
- **Efficient Address Usage:** Minimizes IP address waste by matching subnet size to actual needs
- **Flexibility:** Allows different subnet sizes within the same network
- **Scalability:** Supports hierarchical addressing and growth
- **Route Summarization:** Enables efficient routing table management
- **Cost Savings:** Reduces the need for additional IP address blocks

#### **Question 24:**
**Route Summarization Process:**
1. Identify routes that can be combined
2. Find the common network bits
3. Determine the summary mask
4. Verify no routes fall outside the summary range
5. Implement the summary route

**Benefits:**
- **Smaller Routing Tables:** Reduces memory usage and processing
- **Faster Convergence:** Fewer routes to process during updates
- **Reduced Bandwidth:** Fewer route advertisements
- **Improved Stability:** Less routing update traffic
- **Better Scalability:** Supports larger networks

#### **Question 25:**
**VLSM Design Steps:**
1. **Requirements Analysis:** Identify all network segments and host requirements
2. **Sort by Size:** Order subnets from largest to smallest
3. **Allocate Subnets:** Start with largest subnets and use smallest possible masks
4. **Verify Allocation:** Ensure no overlapping subnets and efficient address usage
5. **Document Plan:** Create addressing documentation and management strategy
6. **Plan for Growth:** Reserve address space for future expansion

---

## 📊 Scoring Guide

### **Total Points: 25**
- **Multiple Choice:** 20 points (1 point each)
- **Short Answer:** 5 points (1 point each)

### **Grade Scale:**
- **90-100% (23-25 points):** Excellent understanding
- **80-89% (20-22 points):** Good understanding
- **70-79% (18-19 points):** Satisfactory understanding
- **60-69% (15-17 points):** Needs improvement
- **Below 60% (<15 points):** Requires review

### **Performance Analysis:**
- **Questions 1-5:** Binary/decimal conversion and basic concepts
- **Questions 6-10:** Subnet mask and CIDR notation
- **Questions 11-15:** Network and broadcast address calculations
- **Questions 16-20:** Subnetting and VLSM concepts
- **Questions 21-25:** Conceptual understanding and application

---

## 🔍 Review Topics

If you scored below 70%, review these topics:

### **Binary and Decimal Conversion:**
- Binary to decimal conversion methods
- Decimal to binary conversion methods
- IP address binary representation
- Subnet mask binary representation

### **Subnet Mask and CIDR:**
- Subnet mask calculation
- CIDR notation understanding
- Magic numbers and shortcuts
- Common subnet mask values

### **Network Address Calculations:**
- Network address determination
- Broadcast address calculation
- Valid host range identification
- AND operation process

### **Subnetting Concepts:**
- Subnetting process and methodology
- Host calculation formulas
- Subnet allocation strategies
- VLSM principles and benefits

### **Advanced Concepts:**
- Route summarization techniques
- Hierarchical addressing design
- Growth planning strategies
- Network documentation requirements

---

## 📚 Additional Resources

### **Recommended Reading:**
- IP addressing fundamentals documentation
- Subnetting calculation guides
- VLSM design best practices
- Network design principles

### **Practice Tools:**
- Subnetting calculators and simulators
- Binary conversion practice tools
- Network design software
- Online practice exercises

### **Study Materials:**
- Subnetting cheat sheets
- Binary/decimal conversion tables
- Magic number reference guides
- Network design templates

---

**Next Session:** [Session 05: Routing Fundamentals](../05-routing-basics/) 