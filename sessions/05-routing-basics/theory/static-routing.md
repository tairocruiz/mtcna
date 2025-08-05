# Static Routing Configuration

## What is Static Routing?

**Static routing** is a routing method where routes are manually configured by network administrators. Unlike dynamic routing protocols, static routes do not automatically adapt to network changes and must be manually updated when the network topology changes.

## Static Route Types

### **1. Standard Static Routes**
- **Definition:** Routes to specific destination networks
- **Syntax:** `/ip route add dst-address=destination-network gateway=next-hop-ip`
- **Example:** `/ip route add dst-address=192.168.2.0/24 gateway=10.0.0.2`

### **2. Default Routes**
- **Definition:** Route of last resort for unknown destinations
- **Syntax:** `/ip route add dst-address=0.0.0.0/0 gateway=next-hop-ip`
- **Purpose:** Internet connectivity, stub networks
- **Example:** `/ip route add dst-address=0.0.0.0/0 gateway=192.168.1.1`

### **3. Summary Routes**
- **Definition:** Routes that encompass multiple subnets
- **Purpose:** Reduce routing table size
- **Example:** `192.168.0.0/16` summarizes `192.168.1.0/24`, `192.168.2.0/24`, etc.

### **4. Floating Static Routes**
- **Definition:** Backup routes with higher administrative distance
- **Purpose:** Provide redundancy
- **Example:** Primary route AD=1, backup route AD=10

## Static Route Configuration

### **Basic Static Route Syntax**

#### **RouterOS Syntax**
```bash
/ip route add dst-address=destination-network gateway=next-hop-ip
```

#### **Example Configurations**

**Standard Route:**
```bash
/ip route add dst-address=192.168.2.0/24 gateway=10.0.0.2
```

**Default Route:**
```bash
/ip route add dst-address=0.0.0.0/0 gateway=192.168.1.1
```

**Interface-based Route:**
```bash
/ip route add dst-address=192.168.2.0/24 gateway=ether2
```

### **Advanced Static Route Options**

#### **Distance (Administrative Distance)**
```bash
/ip route add dst-address=192.168.2.0/24 gateway=10.0.0.2 distance=5
```

#### **Preference (Route Priority)**
```bash
/ip route add dst-address=192.168.2.0/24 gateway=10.0.0.2 preference=100
```

#### **Comment for Documentation**
```bash
/ip route add dst-address=192.168.2.0/24 gateway=10.0.0.2 comment="Branch Office Route"
```

## Default Routes

### **Purpose and Use Cases**

#### **Internet Connectivity**
- **Scenario:** Router connects LAN to Internet
- **Configuration:** Default route points to ISP gateway
- **Example:** `0.0.0.0/0 → 203.0.113.1`

#### **Stub Networks**
- **Scenario:** Single path to external networks
- **Configuration:** All external traffic via default route
- **Example:** Small office with one Internet connection

#### **Hub-and-Spoke Topology**
- **Scenario:** Central router with multiple branch offices
- **Configuration:** Branches use default route to hub
- **Example:** Corporate network with central headquarters

### **Default Route Configuration**

#### **Basic Default Route**
```bash
/ip route add dst-address=0.0.0.0/0 gateway=192.168.1.1
```

#### **Multiple Default Routes (Load Balancing)**
```bash
/ip route add dst-address=0.0.0.0/0 gateway=192.168.1.1
/ip route add dst-address=0.0.0.0/0 gateway=192.168.1.2
```

#### **Default Route with Distance**
```bash
/ip route add dst-address=0.0.0.0/0 gateway=192.168.1.1 distance=1
```

## Summary Routes

### **Benefits of Route Summarization**

#### **1. Reduced Routing Table Size**
- Fewer entries in routing table
- Faster routing table lookups
- Lower memory usage

#### **2. Improved Convergence**
- Fewer routes to advertise
- Faster protocol convergence
- Reduced network overhead

#### **3. Simplified Management**
- Easier to manage fewer routes
- Reduced configuration complexity
- Better scalability

### **Route Summarization Examples**

#### **Example 1: Class C Networks**
```
Original Routes:
192.168.1.0/24
192.168.2.0/24
192.168.3.0/24
192.168.4.0/24

Summary Route:
192.168.0.0/22 (encompasses all four networks)
```

#### **Example 2: Discontiguous Networks**
```
Original Routes:
192.168.1.0/24
192.168.3.0/24
192.168.5.0/24

Summary Route:
192.168.0.0/21 (encompasses all three networks)
```

### **Summary Route Configuration**

#### **RouterOS Configuration**
```bash
/ip route add dst-address=192.168.0.0/22 gateway=10.0.0.2
```

## Floating Static Routes

### **Purpose and Implementation**

#### **Primary Route**
```bash
/ip route add dst-address=192.168.2.0/24 gateway=10.0.0.2 distance=1
```

#### **Backup Route (Floating)**
```bash
/ip route add dst-address=192.168.2.0/24 gateway=10.0.0.6 distance=10
```

### **Floating Route Behavior**

#### **Normal Operation**
- Primary route (AD=1) is active
- Backup route (AD=10) is inactive
- Traffic uses primary path

#### **Failure Scenario**
- Primary route becomes unavailable
- Backup route becomes active
- Traffic automatically switches to backup

#### **Recovery Scenario**
- Primary route becomes available again
- Primary route becomes active (lower AD)
- Traffic switches back to primary

## Static Route Verification

### **RouterOS Commands**

#### **View Routing Table**
```bash
/ip route print
```

#### **View Specific Route**
```bash
/ip route print where dst-address=192.168.2.0/24
```

#### **Test Connectivity**
```bash
/ping 192.168.2.1
/traceroute 192.168.2.1
```

#### **Route Details**
```bash
/ip route print detail
```

### **Troubleshooting Commands**

#### **Check Route Status**
```bash
/ip route print where active=yes
```

#### **Check Route Distance**
```bash
/ip route print where distance=1
```

#### **Monitor Route Changes**
```bash
/ip route monitor
```

## Static Route Best Practices

### **1. Documentation**
- **Use Comments:** Document route purpose and destination
- **Maintain Records:** Keep route documentation updated
- **Label Routes:** Use descriptive comments

### **2. Security**
- **Validate Routes:** Ensure routes point to correct destinations
- **Limit Access:** Restrict route modification access
- **Monitor Changes:** Log route configuration changes

### **3. Redundancy**
- **Backup Routes:** Configure floating static routes
- **Multiple Paths:** Use ECMP when possible
- **Failover Testing:** Test backup route functionality

### **4. Performance**
- **Route Summarization:** Use summary routes where appropriate
- **Optimal Paths:** Choose best next-hop addresses
- **Load Balancing:** Use ECMP for equal-cost paths

### **5. Management**
- **Regular Review:** Periodically review and update routes
- **Change Control:** Follow change management procedures
- **Backup Configuration:** Maintain route configuration backups

## Common Static Route Scenarios

### **Scenario 1: Small Office Network**
```
Internet Router:
/ip route add dst-address=0.0.0.0/0 gateway=203.0.113.1

Internal Routes:
/ip route add dst-address=192.168.1.0/24 gateway=ether1
/ip route add dst-address=192.168.2.0/24 gateway=ether2
```

### **Scenario 2: Multi-Branch Network**
```
Headquarters Router:
/ip route add dst-address=192.168.10.0/24 gateway=10.0.0.10
/ip route add dst-address=192.168.20.0/24 gateway=10.0.0.20
/ip route add dst-address=192.168.30.0/24 gateway=10.0.0.30

Branch Router:
/ip route add dst-address=0.0.0.0/0 gateway=10.0.0.1
```

### **Scenario 3: Redundant Links**
```
Primary Route:
/ip route add dst-address=192.168.2.0/24 gateway=10.0.0.2 distance=1

Backup Route:
/ip route add dst-address=192.168.2.0/24 gateway=10.0.0.6 distance=10
```

---

## Summary

Static routing provides a simple and predictable method for configuring network routes. While it requires manual management, static routes offer security, predictability, and low overhead. Understanding static route types, configuration methods, and best practices is essential for effective network management and troubleshooting. 