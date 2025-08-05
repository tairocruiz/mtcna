# Subnetting Concepts and Calculations

## 🎯 Overview
Subnetting is the process of dividing a network into smaller, more manageable networks. Understanding subnetting is crucial for network design, IP address allocation, and efficient network management.

## 📋 What is Subnetting?

### Definition
Subnetting is the practice of dividing a single network into multiple smaller networks (subnets) by borrowing bits from the host portion of an IP address to create additional network bits.

### Purpose
```
Network Management:
- Improve network performance
- Reduce broadcast domains
- Enhance security through segmentation
- Simplify troubleshooting

IP Address Conservation:
- Efficient use of IP addresses
- Reduce address waste
- Support hierarchical addressing
- Enable route summarization
```

---

## 🔢 Subnet Mask Fundamentals

### What is a Subnet Mask?
```
Definition: 32-bit number that identifies which portion of an IP address belongs to the network and which belongs to the host
Purpose: Determines the network address and host range
Format: Same as IP address (dotted decimal notation)
Example: 255.255.255.0 for a /24 network
```

### Subnet Mask Structure
```
Binary Representation:
Network Bits: 1s (left side)
Host Bits: 0s (right side)

Example - /24 subnet mask:
11111111.11111111.11111111.00000000
255.255.255.0
```

### Common Subnet Masks
```
/8   = 255.0.0.0       (Class A default)
/16  = 255.255.0.0     (Class B default)
/24  = 255.255.255.0   (Class C default)
/25  = 255.255.255.128 (128 hosts)
/26  = 255.255.255.192 (64 hosts)
/27  = 255.255.255.224 (32 hosts)
/28  = 255.255.255.240 (16 hosts)
/29  = 255.255.255.248 (8 hosts)
/30  = 255.255.255.252 (4 hosts)
/31  = 255.255.255.254 (2 hosts)
/32  = 255.255.255.255 (1 host)
```

---

## 🏗️ Subnetting Components

### Network Address
```
Definition: First address in a subnet (all host bits = 0)
Purpose: Identifies the subnet
Calculation: IP address AND subnet mask
Example: 192.168.1.0/24
```

### Broadcast Address
```
Definition: Last address in a subnet (all host bits = 1)
Purpose: Sends traffic to all hosts in the subnet
Calculation: Network address + (2^host_bits - 1)
Example: 192.168.1.255/24
```

### Valid Host Range
```
Definition: Usable IP addresses in a subnet
Range: Network address + 1 to Broadcast address - 1
Example: 192.168.1.1 to 192.168.1.254
```

### Number of Hosts
```
Formula: 2^host_bits - 2
Subtract 2: Network address and broadcast address
Example: /24 = 2^8 - 2 = 256 - 2 = 254 hosts
```

---

## 🔄 Subnetting Calculation Process

### Step 1: Determine Network Requirements
```
Identify:
- Number of subnets needed
- Hosts per subnet
- Network address range
- Growth requirements
```

### Step 2: Calculate Subnet Bits
```
Formula: 2^subnet_bits >= number_of_subnets
Example: Need 6 subnets
2^3 = 8 >= 6 (use 3 subnet bits)
```

### Step 3: Calculate Host Bits
```
Formula: Total bits - network bits - subnet bits = host bits
Example: 32 - 24 - 3 = 5 host bits
```

### Step 4: Determine Subnet Mask
```
Convert host bits to subnet mask
Example: 5 host bits = /27 = 255.255.255.224
```

### Step 5: Calculate Subnet Ranges
```
Network Address: Base + (subnet_number × subnet_size)
Broadcast Address: Network + (2^host_bits - 1)
Host Range: Network + 1 to Broadcast - 1
```

---

## 📊 Subnetting Examples

### Example 1: Class C Network (/24)
```
Network: 192.168.1.0/24
Subnet Mask: 255.255.255.0
Host Bits: 8
Number of Hosts: 2^8 - 2 = 254

Network Address: 192.168.1.0
Broadcast Address: 192.168.1.255
Valid Host Range: 192.168.1.1 - 192.168.1.254
```

### Example 2: Subnetting Class C (/26)
```
Network: 192.168.1.0/26
Subnet Mask: 255.255.255.192
Host Bits: 6
Number of Hosts: 2^6 - 2 = 62

Subnet 0:
- Network: 192.168.1.0
- Broadcast: 192.168.1.63
- Hosts: 192.168.1.1 - 192.168.1.62

Subnet 1:
- Network: 192.168.1.64
- Broadcast: 192.168.1.127
- Hosts: 192.168.1.65 - 192.168.1.126

Subnet 2:
- Network: 192.168.1.128
- Broadcast: 192.168.1.191
- Hosts: 192.168.1.129 - 192.168.1.190

Subnet 3:
- Network: 192.168.1.192
- Broadcast: 192.168.1.255
- Hosts: 192.168.1.193 - 192.168.1.254
```

### Example 3: Subnetting Class B (/26)
```
Network: 172.16.0.0/26
Subnet Mask: 255.255.255.192
Host Bits: 6
Number of Hosts: 2^6 - 2 = 62

Subnet 0:
- Network: 172.16.0.0
- Broadcast: 172.16.0.63
- Hosts: 172.16.0.1 - 172.16.0.62

Subnet 1:
- Network: 172.16.0.64
- Broadcast: 172.16.0.127
- Hosts: 172.16.0.65 - 172.16.0.126

... (continues for all subnets)
```

---

## 🔧 Binary to Decimal Conversion

### Quick Conversion Table
```
Binary    | Decimal
----------|---------
00000000  | 0
10000000  | 128
11000000  | 192
11100000  | 224
11110000  | 240
11111000  | 248
11111100  | 252
11111110  | 254
11111111  | 255
```

### Conversion Method
```
Step 1: Write binary number
Step 2: Assign powers of 2 (right to left)
Step 3: Multiply each bit by its power
Step 4: Sum the results

Example: 11000000
128 + 64 + 0 + 0 + 0 + 0 + 0 + 0 = 192
```

### Decimal to Binary Conversion
```
Step 1: Start with decimal number
Step 2: Divide by 2, record remainder
Step 3: Continue until quotient is 0
Step 4: Read remainders in reverse order

Example: 192 to binary
192 ÷ 2 = 96 remainder 0
96 ÷ 2 = 48 remainder 0
48 ÷ 2 = 24 remainder 0
24 ÷ 2 = 12 remainder 0
12 ÷ 2 = 6 remainder 0
6 ÷ 2 = 3 remainder 0
3 ÷ 2 = 1 remainder 1
1 ÷ 2 = 0 remainder 1
Result: 11000000
```

---

## 🎯 CIDR Notation

### What is CIDR?
```
Definition: Classless Inter-Domain Routing
Purpose: Specify subnet mask using bit count
Format: IP_address/bit_count
Example: 192.168.1.0/24
```

### CIDR to Subnet Mask
```
/24 = 255.255.255.0
/25 = 255.255.255.128
/26 = 255.255.255.192
/27 = 255.255.255.224
/28 = 255.255.255.240
/29 = 255.255.255.248
/30 = 255.255.255.252
```

### Subnet Mask to CIDR
```
Count the number of 1s in binary
Example: 255.255.255.192
11111111.11111111.11111111.11000000
Count 1s: 26
Result: /26
```

---

## 📈 Subnetting Formulas

### Key Formulas
```
Number of Subnets: 2^subnet_bits
Number of Hosts: 2^host_bits - 2
Subnet Size: 2^host_bits
Network Address: IP AND subnet_mask
Broadcast Address: Network + (2^host_bits - 1)
First Host: Network + 1
Last Host: Broadcast - 1
```

### Magic Numbers
```
/25 = 128
/26 = 64
/27 = 32
/28 = 16
/29 = 8
/30 = 4
/31 = 2
/32 = 1
```

### Subnet Calculation Shortcut
```
Step 1: Find magic number (256 - last octet of subnet mask)
Step 2: Start with 0, increment by magic number
Step 3: Each increment is a new subnet

Example: /26 (255.255.255.192)
Magic number: 256 - 192 = 64
Subnets: 0, 64, 128, 192
```

---

## 🔍 Subnetting Verification

### Verification Steps
```
1. Check network address (all host bits = 0)
2. Check broadcast address (all host bits = 1)
3. Verify host range (network + 1 to broadcast - 1)
4. Confirm subnet mask is correct
5. Validate CIDR notation
```

### Common Mistakes
```
- Forgetting to subtract 2 for usable hosts
- Incorrect binary to decimal conversion
- Wrong subnet mask calculation
- Confusing network and broadcast addresses
- Incorrect CIDR notation
```

### Verification Tools
```
- Subnet calculators
- Binary calculators
- Network analysis tools
- Command line tools (ipcalc, etc.)
```

---

## 🏢 Practical Subnetting Scenarios

### Scenario 1: Small Office
```
Requirements:
- 1 network for 50 hosts
- 1 network for 25 hosts
- 1 network for 10 hosts

Solution:
- Use 192.168.1.0/24
- Subnet 1: 192.168.1.0/26 (62 hosts)
- Subnet 2: 192.168.1.64/27 (30 hosts)
- Subnet 3: 192.168.1.96/28 (14 hosts)
```

### Scenario 2: Medium Business
```
Requirements:
- 5 departments with 30 hosts each
- 1 server network with 10 hosts
- 1 guest network with 50 hosts

Solution:
- Use 172.16.0.0/16
- Department networks: /27 (30 hosts each)
- Server network: /28 (14 hosts)
- Guest network: /26 (62 hosts)
```

### Scenario 3: Large Enterprise
```
Requirements:
- 20 branch offices with 100 hosts each
- 1 headquarters with 500 hosts
- 1 data center with 200 hosts

Solution:
- Use 10.0.0.0/8
- Branch offices: /25 (126 hosts each)
- Headquarters: /23 (510 hosts)
- Data center: /24 (254 hosts)
```

---

## 🛠️ Subnetting Tools and Resources

### Online Calculators
```
- Subnet-calculator.com
- IPCalculator.com
- SolarWinds Subnet Calculator
- Cisco Subnet Calculator
```

### Command Line Tools
```
Linux:
- ipcalc
- sipcalc
- subnetcalc

Windows:
- PowerShell subnet functions
- Third-party calculators
```

### Mobile Apps
```
- Subnet Calculator
- IP Calculator
- Network Calculator
- Subnetting Practice
```

---

## 🎓 Summary

### Key Concepts
- **Subnetting:** Dividing networks into smaller networks
- **Subnet Mask:** Identifies network and host portions
- **Network Address:** First address in subnet
- **Broadcast Address:** Last address in subnet
- **Valid Host Range:** Usable addresses in subnet

### Calculation Process
1. **Determine requirements** (subnets, hosts)
2. **Calculate subnet bits** needed
3. **Calculate host bits** remaining
4. **Determine subnet mask**
5. **Calculate subnet ranges**

### Best Practices
- **Plan for growth** when designing subnets
- **Use consistent subnet sizes** when possible
- **Document subnet assignments** thoroughly
- **Verify calculations** before implementation
- **Consider security implications** of subnet design

### Common Subnet Sizes
- **/24:** 254 hosts (most common)
- **/25:** 126 hosts
- **/26:** 62 hosts
- **/27:** 30 hosts
- **/28:** 14 hosts
- **/29:** 6 hosts
- **/30:** 2 hosts (point-to-point links)

### Verification Checklist
- [ ] Network address is correct
- [ ] Broadcast address is correct
- [ ] Host range is valid
- [ ] Subnet mask matches CIDR
- [ ] Number of hosts is sufficient
- [ ] No overlapping subnets 