# Lab 02: Routing Table Analysis

## 🎯 Lab Objectives
By the end of this lab, you will be able to:
- Analyze routing table structure and components
- Understand route selection process and criteria
- Interpret routing table output and fields
- Troubleshoot routing issues using table analysis
- Understand administrative distance and metrics

---

## 📋 Prerequisites
- MikroTik RouterOS device or GNS3/EVE-NG with RouterOS
- Completion of Lab 01: Static Route Configuration
- Basic understanding of IP addressing and routing concepts

---

## 🏗️ Lab Topology

```
                    Internet
                       |
                    [Router1]
                   192.168.1.1
                       |
                   192.168.1.0/24
                       |
    ┌─────────────────┼─────────────────┐
    │                 │                 │
[Router2]         [Router3]         [Router4]
192.168.2.1      192.168.3.1      192.168.4.1
    │                 │                 │
192.168.2.0/24   192.168.3.0/24   192.168.4.0/24
    │                 │                 │
[PC1]            [PC2]            [PC3]
192.168.2.10    192.168.3.10     192.168.4.10
```

## 📝 Lab Configuration

### **Step 1: Configure Network with Multiple Route Sources**

#### **Router1 Configuration**
```bash
# Basic interface configuration
/interface ethernet set ether1 name=WAN
/interface ethernet set ether2 name=LAN1
/interface ethernet set ether3 name=LAN2
/interface ethernet set ether4 name=LAN3

# IP configuration
/ip address add address=203.0.113.1/24 interface=WAN
/ip address add address=192.168.1.1/24 interface=LAN1
/ip address add address=192.168.1.2/24 interface=LAN2
/ip address add address=192.168.1.3/24 interface=LAN3

# Enable interfaces
/interface enable WAN
/interface enable LAN1
/interface enable LAN2
/interface enable LAN3

# Static routes
/ip route add dst-address=192.168.2.0/24 gateway=192.168.1.10 distance=1 comment="Static Route"
/ip route add dst-address=192.168.3.0/24 gateway=192.168.1.20 distance=1 comment="Static Route"
/ip route add dst-address=192.168.4.0/24 gateway=192.168.1.30 distance=1 comment="Static Route"

# Default route
/ip route add dst-address=0.0.0.0/0 gateway=203.0.113.254 distance=1 comment="Internet Default"
```

#### **Router2 Configuration**
```bash
# Basic interface configuration
/interface ethernet set ether1 name=UPLINK
/interface ethernet set ether2 name=LAN

# IP configuration
/ip address add address=192.168.1.10/24 interface=UPLINK
/ip address add address=192.168.2.1/24 interface=LAN

# Enable interfaces
/interface enable UPLINK
/interface enable LAN

# Static routes with different distances
/ip route add dst-address=192.168.3.0/24 gateway=192.168.1.20 distance=1 comment="Primary Route"
/ip route add dst-address=192.168.3.0/24 gateway=192.168.1.30 distance=10 comment="Backup Route"
/ip route add dst-address=192.168.4.0/24 gateway=192.168.1.30 distance=1 comment="Direct Route"

# Default route
/ip route add dst-address=0.0.0.0/0 gateway=192.168.1.1 distance=1 comment="Default Route"
```

### **Step 2: Analyze Routing Table Structure**

#### **View Basic Routing Table**
```bash
# Display routing table
/ip route print

# Expected output format:
# DST-ADDRESS        GATEWAY         DISTANCE  INTERFACE
# 0.0.0.0/0         203.0.113.254   1         WAN
# 192.168.1.0/24    -               0         LAN1
# 192.168.2.0/24    192.168.1.10    1         LAN1
```

#### **View Detailed Routing Table**
```bash
# Display detailed routing table
/ip route print detail

# Expected output includes:
# - DST-ADDRESS: Destination network
# - GATEWAY: Next-hop IP address
# - DISTANCE: Administrative distance
# - INTERFACE: Outgoing interface
# - COMMENT: Route description
# - ACTIVE: Route status
# - DYNAMIC: Whether route is dynamic
```

### **Step 3: Analyze Route Selection Process**

#### **Test Route Selection with Multiple Routes**
```bash
# Add multiple routes to same destination with different distances
/ip route add dst-address=192.168.5.0/24 gateway=192.168.1.10 distance=1 comment="Primary Route"
/ip route add dst-address=192.168.5.0/24 gateway=192.168.1.20 distance=5 comment="Backup Route 1"
/ip route add dst-address=192.168.5.0/24 gateway=192.168.1.30 distance=10 comment="Backup Route 2"

# View routes to specific destination
/ip route print where dst-address=192.168.5.0/24

# Check which route is active
/ip route print where dst-address=192.168.5.0/24 and active=yes
```

#### **Test Equal-Cost Routes**
```bash
# Add equal-cost routes (same distance)
/ip route add dst-address=192.168.6.0/24 gateway=192.168.1.10 distance=1 comment="ECMP Route 1"
/ip route add dst-address=192.168.6.0/24 gateway=192.168.1.20 distance=1 comment="ECMP Route 2"

# View equal-cost routes
/ip route print where dst-address=192.168.6.0/24
```

### **Step 4: Analyze Route Types and Sources**

#### **Connected Routes**
```bash
# View connected routes (distance=0)
/ip route print where distance=0

# Expected: Routes for directly connected networks
# 192.168.1.0/24, 192.168.2.0/24, etc.
```

#### **Static Routes**
```bash
# View static routes (distance=1)
/ip route print where distance=1

# View static routes with comments
/ip route print where distance=1 and comment~"Static"
```

#### **Default Routes**
```bash
# View default routes
/ip route print where dst-address=0.0.0.0/0

# Check default route status
/ip route print where dst-address=0.0.0.0/0 and active=yes
```

### **Step 5: Analyze Route Metrics and Preferences**

#### **Route Distance Analysis**
```bash
# View routes by distance
/ip route print where distance=1
/ip route print where distance=5
/ip route print where distance=10

# Count routes by distance
/ip route print count-only where distance=1
/ip route print count-only where distance=5
/ip route print count-only where distance=10
```

#### **Route Preference Analysis**
```bash
# Add routes with different preferences
/ip route add dst-address=192.168.7.0/24 gateway=192.168.1.10 preference=100 comment="Preferred Route"
/ip route add dst-address=192.168.7.0/24 gateway=192.168.1.20 preference=200 comment="Alternative Route"

# View routes by preference
/ip route print where preference=100
/ip route print where preference=200
```

### **Step 6: Troubleshoot Routing Issues**

#### **Identify Inactive Routes**
```bash
# View inactive routes
/ip route print where active=no

# Check why routes are inactive
/ip route print detail where active=no
```

#### **Identify Route Conflicts**
```bash
# Find routes to same destination
/ip route print where dst-address=192.168.3.0/24

# Analyze route selection for specific destination
/ip route print detail where dst-address=192.168.3.0/24
```

#### **Check Gateway Reachability**
```bash
# Test gateway connectivity
/ping 192.168.1.10
/ping 192.168.1.20
/ping 192.168.1.30

# Check interface status
/interface print
```

### **Step 7: Advanced Routing Table Analysis**

#### **Route Summarization Analysis**
```bash
# Add specific routes
/ip route add dst-address=192.168.10.0/24 gateway=192.168.1.10
/ip route add dst-address=192.168.11.0/24 gateway=192.168.1.10
/ip route add dst-address=192.168.12.0/24 gateway=192.168.1.10
/ip route add dst-address=192.168.13.0/24 gateway=192.168.1.10

# Add summary route
/ip route add dst-address=192.168.8.0/22 gateway=192.168.1.10 distance=5 comment="Summary Route"

# Analyze route overlap
/ip route print where dst-address~"192.168.1"
```

#### **Route Filtering Analysis**
```bash
# Add routes with specific patterns
/ip route add dst-address=10.1.1.0/24 gateway=192.168.1.10 comment="Internal Route"
/ip route add dst-address=10.1.2.0/24 gateway=192.168.1.10 comment="Internal Route"
/ip route add dst-address=172.16.1.0/24 gateway=192.168.1.20 comment="External Route"

# Filter routes by pattern
/ip route print where dst-address~"10.1"
/ip route print where dst-address~"172.16"
/ip route print where comment~"Internal"
```

---

## 🔍 Verification Commands

### **Basic Routing Table Commands**
```bash
# View all routes
/ip route print

# View active routes only
/ip route print where active=yes

# View routes with comments
/ip route print detail

# Count total routes
/ip route print count-only
```

### **Route Analysis Commands**
```bash
# View routes by distance
/ip route print where distance=0
/ip route print where distance=1
/ip route print where distance=5

# View routes by destination
/ip route print where dst-address=192.168.2.0/24

# View routes by gateway
/ip route print where gateway=192.168.1.10

# View routes by interface
/ip route print where interface=LAN1
```

### **Troubleshooting Commands**
```bash
# Check route status
/ip route print where active=no

# Check gateway reachability
/ping 192.168.1.10

# Check interface status
/interface print

# Monitor route changes
/ip route monitor
```

---

## 📝 Lab Questions

### **Question 1: Routing Table Structure**
1. What are the main fields in a routing table?
2. What does the "DST-ADDRESS" field represent?
3. What is the difference between "GATEWAY" and "INTERFACE" fields?

### **Question 2: Route Selection**
1. How does RouterOS select the best route to a destination?
2. What is the significance of the "DISTANCE" field?
3. What happens when multiple routes have the same distance?

### **Question 3: Administrative Distance**
1. What is administrative distance and why is it important?
2. Which route source has the lowest administrative distance?
3. How does administrative distance affect route selection?

### **Question 4: Route Types**
1. What is a connected route and how is it identified?
2. What is the difference between static and dynamic routes?
3. When would you use a default route?

### **Question 5: Troubleshooting**
1. How can you identify why a route is inactive?
2. What steps would you take to troubleshoot routing issues?
3. How can you verify gateway reachability?

---

## 🎯 Expected Results

### **After Step 2:**
- Routing table should show connected, static, and default routes
- All routes should be properly formatted with correct fields
- Active routes should be marked appropriately

### **After Step 3:**
- Route selection should follow administrative distance rules
- Lower distance routes should be preferred
- Equal-cost routes should both be active

### **After Step 4:**
- Connected routes should have distance=0
- Static routes should have distance=1
- Default routes should be properly configured

### **After Step 5:**
- Routes should be properly categorized by distance
- Preference settings should affect route selection
- Route metrics should be correctly displayed

### **After Step 6:**
- Inactive routes should be identified
- Route conflicts should be resolved
- Gateway reachability should be verified

---

## 🚨 Troubleshooting Tips

### **Common Issues**

#### **1. Routes Not Active**
- **Check:** Gateway reachability and interface status
- **Solution:** Verify IP configuration and connectivity

#### **2. Route Selection Issues**
- **Check:** Administrative distance and metrics
- **Solution:** Ensure proper route priorities

#### **3. Missing Routes**
- **Check:** Route configuration and syntax
- **Solution:** Verify route commands and parameters

#### **4. Route Conflicts**
- **Check:** Multiple routes to same destination
- **Solution:** Review route selection criteria

---

## 📚 Additional Exercises

### **Exercise 1: Route Analysis**
Analyze the routing table and answer:
1. How many routes are in the table?
2. Which routes are connected vs static?
3. What is the default route gateway?

### **Exercise 2: Route Selection Simulation**
Create scenarios to test:
1. Route selection with different distances
2. Equal-cost multipath routing
3. Route preference settings

### **Exercise 3: Troubleshooting Practice**
Practice troubleshooting:
1. Inactive route identification
2. Gateway reachability testing
3. Route conflict resolution

---

## ✅ Lab Completion Checklist

- [ ] Network configuration completed
- [ ] Multiple route sources configured
- [ ] Routing table structure analyzed
- [ ] Route selection process tested
- [ ] Route types and sources identified
- [ ] Route metrics and preferences analyzed
- [ ] Troubleshooting scenarios completed
- [ ] Lab questions answered
- [ ] Advanced analysis exercises completed 