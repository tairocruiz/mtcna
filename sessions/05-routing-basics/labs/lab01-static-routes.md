# Lab 01: Static Route Configuration

## 🎯 Lab Objectives
By the end of this lab, you will be able to:
- Configure basic static routes in RouterOS
- Implement default routes for internet connectivity
- Configure floating static routes for redundancy
- Verify and troubleshoot static route configuration
- Understand route selection and administrative distance

---

## 📋 Prerequisites
- MikroTik RouterOS device or GNS3/EVE-NG with RouterOS
- Basic understanding of IP addressing
- Familiarity with RouterOS CLI

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

### **Step 1: Basic Network Configuration**

#### **Router1 Configuration**
```bash
# Configure interfaces
/interface ethernet set ether1 name=WAN
/interface ethernet set ether2 name=LAN1
/interface ethernet set ether3 name=LAN2
/interface ethernet set ether4 name=LAN3

# Configure IP addresses
/ip address add address=203.0.113.1/24 interface=WAN
/ip address add address=192.168.1.1/24 interface=LAN1
/ip address add address=192.168.1.2/24 interface=LAN2
/ip address add address=192.168.1.3/24 interface=LAN3

# Enable interfaces
/interface enable WAN
/interface enable LAN1
/interface enable LAN2
/interface enable LAN3
```

#### **Router2 Configuration**
```bash
# Configure interfaces
/interface ethernet set ether1 name=UPLINK
/interface ethernet set ether2 name=LAN

# Configure IP addresses
/ip address add address=192.168.1.10/24 interface=UPLINK
/ip address add address=192.168.2.1/24 interface=LAN

# Enable interfaces
/interface enable UPLINK
/interface enable LAN
```

#### **Router3 Configuration**
```bash
# Configure interfaces
/interface ethernet set ether1 name=UPLINK
/interface ethernet set ether2 name=LAN

# Configure IP addresses
/ip address add address=192.168.1.20/24 interface=UPLINK
/ip address add address=192.168.3.1/24 interface=LAN

# Enable interfaces
/interface enable UPLINK
/interface enable LAN
```

#### **Router4 Configuration**
```bash
# Configure interfaces
/interface ethernet set ether1 name=UPLINK
/interface ethernet set ether2 name=LAN

# Configure IP addresses
/ip address add address=192.168.1.30/24 interface=UPLINK
/ip address add address=192.168.4.1/24 interface=LAN

# Enable interfaces
/interface enable UPLINK
/interface enable LAN
```

### **Step 2: Configure Static Routes**

#### **Router1 - Default Route to Internet**
```bash
# Add default route to internet
/ip route add dst-address=0.0.0.0/0 gateway=203.0.113.254 comment="Internet Default Route"

# Add routes to branch networks
/ip route add dst-address=192.168.2.0/24 gateway=192.168.1.10 comment="Router2 Network"
/ip route add dst-address=192.168.3.0/24 gateway=192.168.1.20 comment="Router3 Network"
/ip route add dst-address=192.168.4.0/24 gateway=192.168.1.30 comment="Router4 Network"
```

#### **Router2 - Routes to Other Networks**
```bash
# Add default route to Router1
/ip route add dst-address=0.0.0.0/0 gateway=192.168.1.1 comment="Default Route to Router1"

# Add routes to other branch networks
/ip route add dst-address=192.168.3.0/24 gateway=192.168.1.20 comment="Router3 Network"
/ip route add dst-address=192.168.4.0/24 gateway=192.168.1.30 comment="Router4 Network"
```

#### **Router3 - Routes to Other Networks**
```bash
# Add default route to Router1
/ip route add dst-address=0.0.0.0/0 gateway=192.168.1.1 comment="Default Route to Router1"

# Add routes to other branch networks
/ip route add dst-address=192.168.2.0/24 gateway=192.168.1.10 comment="Router2 Network"
/ip route add dst-address=192.168.4.0/24 gateway=192.168.1.30 comment="Router4 Network"
```

#### **Router4 - Routes to Other Networks**
```bash
# Add default route to Router1
/ip route add dst-address=0.0.0.0/0 gateway=192.168.1.1 comment="Default Route to Router1"

# Add routes to other branch networks
/ip route add dst-address=192.168.2.0/24 gateway=192.168.1.10 comment="Router2 Network"
/ip route add dst-address=192.168.3.0/24 gateway=192.168.1.20 comment="Router3 Network"
```

### **Step 3: Verify Configuration**

#### **Check Routing Tables**
```bash
# View all routes
/ip route print

# View active routes only
/ip route print where active=yes

# View routes with comments
/ip route print detail
```

#### **Test Connectivity**
```bash
# Test connectivity to internet
/ping 8.8.8.8

# Test connectivity between routers
/ping 192.168.2.1
/ping 192.168.3.1
/ping 192.168.4.1

# Test connectivity to branch networks
/ping 192.168.2.10
/ping 192.168.3.10
/ping 192.168.4.10
```

### **Step 4: Configure Floating Static Routes**

#### **Add Backup Links**
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

    ┌─────────────────┼─────────────────┐
    │                 │                 │
[Router2] ←→ [Router3] ←→ [Router4]
192.168.5.0/24   192.168.6.0/24
```

#### **Configure Backup Links**
```bash
# Router2 - Add backup interface to Router3
/interface ethernet set ether3 name=BACKUP
/ip address add address=192.168.5.1/24 interface=BACKUP
/interface enable BACKUP

# Router3 - Add backup interfaces
/interface ethernet set ether3 name=BACKUP1
/interface ethernet set ether4 name=BACKUP2
/ip address add address=192.168.5.2/24 interface=BACKUP1
/ip address add address=192.168.6.1/24 interface=BACKUP2
/interface enable BACKUP1
/interface enable BACKUP2

# Router4 - Add backup interface to Router3
/interface ethernet set ether3 name=BACKUP
/ip address add address=192.168.6.2/24 interface=BACKUP
/interface enable BACKUP
```

#### **Configure Floating Static Routes**
```bash
# Router2 - Floating route to Router3 network via backup link
/ip route add dst-address=192.168.3.0/24 gateway=192.168.5.2 distance=10 comment="Backup Route to Router3"

# Router3 - Floating routes to other networks via backup links
/ip route add dst-address=192.168.2.0/24 gateway=192.168.5.1 distance=10 comment="Backup Route to Router2"
/ip route add dst-address=192.168.4.0/24 gateway=192.168.6.2 distance=10 comment="Backup Route to Router4"

# Router4 - Floating route to Router3 network via backup link
/ip route add dst-address=192.168.3.0/24 gateway=192.168.6.1 distance=10 comment="Backup Route to Router3"
```

### **Step 5: Test Redundancy**

#### **Simulate Primary Link Failure**
```bash
# Disable primary link on Router2
/interface disable UPLINK

# Check routing table
/ip route print where active=yes

# Test connectivity
/ping 192.168.3.1
/ping 192.168.3.10

# Re-enable primary link
/interface enable UPLINK
```

#### **Monitor Route Changes**
```bash
# Monitor routing table changes
/ip route monitor

# Check route distances
/ip route print where distance=1
/ip route print where distance=10
```

---

## 🔍 Verification Commands

### **Route Verification**
```bash
# View routing table
/ip route print

# View specific route
/ip route print where dst-address=192.168.2.0/24

# View routes by distance
/ip route print where distance=1

# View active routes only
/ip route print where active=yes
```

### **Connectivity Testing**
```bash
# Test basic connectivity
/ping 192.168.2.1
/ping 192.168.3.1
/ping 192.168.4.1

# Test end-to-end connectivity
/ping 192.168.2.10
/ping 192.168.3.10
/ping 192.168.4.10

# Test internet connectivity
/ping 8.8.8.8
```

### **Troubleshooting Commands**
```bash
# Check interface status
/interface print

# Check IP addresses
/ip address print

# Check route details
/ip route print detail

# Monitor route changes
/ip route monitor
```

---

## 📝 Lab Questions

### **Question 1: Route Selection**
1. What happens when you have two routes to the same destination with different distances?
2. Which route will be selected: a route with distance=1 or distance=10?
3. How does RouterOS handle equal-cost routes?

### **Question 2: Default Routes**
1. What is the purpose of a default route (0.0.0.0/0)?
2. When would you use a default route?
3. What happens if a default route becomes unavailable?

### **Question 3: Floating Static Routes**
1. What is the purpose of floating static routes?
2. How do you configure a floating static route?
3. When would a floating static route become active?

### **Question 4: Route Verification**
1. What command shows all routes in the routing table?
2. How do you check if a specific route is active?
3. What information does the `detail` parameter provide?

---

## 🎯 Expected Results

### **After Step 2:**
- All routers should have routes to all networks
- PC1 should be able to ping PC2 and PC3
- All routers should have internet connectivity

### **After Step 4:**
- Backup routes should be configured but inactive
- Primary routes should have distance=1
- Backup routes should have distance=10

### **After Step 5:**
- When primary link fails, backup route should become active
- Connectivity should be maintained via backup path
- When primary link is restored, traffic should return to primary path

---

## 🚨 Troubleshooting Tips

### **Common Issues**

#### **1. Routes Not Active**
- **Check:** Interface status and IP configuration
- **Solution:** Ensure interfaces are enabled and IP addresses are correct

#### **2. No Connectivity**
- **Check:** Routing table and gateway reachability
- **Solution:** Verify routes are configured and gateways are reachable

#### **3. Backup Routes Not Working**
- **Check:** Route distances and gateway reachability
- **Solution:** Ensure backup routes have higher distance and valid gateways

#### **4. Internet Connectivity Issues**
- **Check:** Default route configuration
- **Solution:** Verify default route points to correct gateway

---

## 📚 Additional Exercises

### **Exercise 1: Route Summarization**
Configure summary routes to reduce routing table size:
- Summarize 192.168.2.0/24, 192.168.3.0/24, 192.168.4.0/24 into 192.168.0.0/22

### **Exercise 2: Load Balancing**
Configure equal-cost multipath routing:
- Add multiple default routes with same distance
- Test load balancing between paths

### **Exercise 3: Route Filtering**
Configure route filters to control route distribution:
- Use route filters to prevent specific routes from being advertised
- Test route filtering functionality

---

## ✅ Lab Completion Checklist

- [ ] Basic network configuration completed
- [ ] Static routes configured on all routers
- [ ] Default routes configured for internet connectivity
- [ ] Floating static routes configured for redundancy
- [ ] All connectivity tests passed
- [ ] Route verification commands executed
- [ ] Lab questions answered
- [ ] Troubleshooting scenarios tested 