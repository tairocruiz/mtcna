# Routing Fundamentals

## What is Routing?

**Routing** is the process of determining the best path for data packets to travel from a source to a destination across interconnected networks. Routers are the devices responsible for making routing decisions and forwarding packets between different networks.

## Router Functions and Components

### **Core Router Functions**

#### **1. Packet Forwarding**
- **Function:** Move packets from incoming interfaces to outgoing interfaces
- **Process:** Examine packet headers, consult routing table, forward to next hop
- **Decision:** Based on destination IP address and routing table entries

#### **2. Path Determination**
- **Function:** Determine the best route to destination networks
- **Methods:** Static routes, dynamic routing protocols, default routes
- **Criteria:** Administrative distance, metrics, path cost

#### **3. Network Interconnection**
- **Function:** Connect different networks and subnets
- **Capability:** Route between different IP address ranges
- **Isolation:** Separate broadcast and collision domains

### **Router Components**

#### **Hardware Components**
- **CPU:** Processes routing decisions and runs routing protocols
- **Memory:**
  - **RAM:** Running configuration and routing tables
  - **NVRAM:** Startup configuration
  - **Flash:** Operating system and configuration files
- **Interfaces:** Physical and logical connections to networks
- **Console Port:** Direct management access

#### **Software Components**
- **Operating System:** RouterOS (MikroTik), IOS (Cisco), etc.
- **Routing Protocols:** OSPF, RIP, BGP, etc.
- **Management Tools:** Web interface, CLI, SNMP

## Packet Forwarding Process

### **Step-by-Step Process**

#### **1. Packet Reception**
```
Incoming Packet → Interface → Buffer → Processing
```

#### **2. Header Analysis**
- **Source IP:** Where packet originated
- **Destination IP:** Where packet is going
- **Protocol:** TCP, UDP, ICMP, etc.
- **TTL:** Time to live (hop count)

#### **3. Routing Table Lookup**
```
Destination IP → Routing Table → Best Match → Next Hop
```

#### **4. Path Selection**
- **Longest Match:** Most specific route wins
- **Administrative Distance:** Lower is preferred
- **Metric:** Lower is preferred (within same protocol)

#### **5. Packet Forwarding**
```
Next Hop → Outgoing Interface → Network → Destination
```

### **Routing Table Structure**

#### **Key Fields**
- **Destination:** Network address and subnet mask
- **Next Hop:** IP address of next router
- **Interface:** Outgoing interface
- **Metric:** Cost to reach destination
- **Administrative Distance:** Trustworthiness of route source

#### **Example Routing Table**
```
Destination        Gateway         Interface    Metric  AD
192.168.1.0/24    -              ether1       0       0
10.0.0.0/8        192.168.1.1    ether1       1       1
0.0.0.0/0         192.168.1.1    ether1       1       1
```

## Routing vs Switching

### **Key Differences**

#### **Layer of Operation**
- **Switching:** Layer 2 (Data Link Layer)
- **Routing:** Layer 3 (Network Layer)

#### **Addressing**
- **Switching:** Uses MAC addresses
- **Routing:** Uses IP addresses

#### **Scope**
- **Switching:** Within same network/broadcast domain
- **Routing:** Between different networks

#### **Function**
- **Switching:** Frame forwarding within LAN
- **Routing:** Packet forwarding between networks

### **Comparison Table**

| Aspect | Switching | Routing |
|--------|-----------|---------|
| **Layer** | Layer 2 | Layer 3 |
| **Address** | MAC Address | IP Address |
| **Scope** | Local Network | Inter-network |
| **Protocol** | Ethernet | IP |
| **Device** | Switch | Router |
| **Table** | MAC Table | Routing Table |
| **Decision** | Frame-based | Packet-based |

## Routing Types

### **1. Static Routing**
- **Definition:** Manually configured routes
- **Advantages:** Predictable, secure, low overhead
- **Disadvantages:** Manual maintenance, no fault tolerance
- **Use Cases:** Small networks, stub networks, security requirements

### **2. Dynamic Routing**
- **Definition:** Automatically learned routes
- **Advantages:** Automatic updates, fault tolerance, scalability
- **Disadvantages:** Protocol overhead, complexity
- **Use Cases:** Large networks, redundant paths

### **3. Default Routing**
- **Definition:** Route of last resort
- **Purpose:** Handle unknown destinations
- **Configuration:** 0.0.0.0/0 route
- **Use Cases:** Internet connectivity, stub networks

## Routing Metrics

### **Common Metrics**

#### **Hop Count**
- **Definition:** Number of routers to destination
- **Protocol:** RIP
- **Range:** 0-15 (RIP), 0-255 (general)
- **Preference:** Lower is better

#### **Bandwidth**
- **Definition:** Link capacity in bits per second
- **Protocol:** OSPF, EIGRP
- **Calculation:** 10^8 / bandwidth
- **Example:** 100 Mbps = 1, 10 Mbps = 10

#### **Delay**
- **Definition:** Time to traverse link
- **Protocol:** EIGRP
- **Unit:** Microseconds
- **Preference:** Lower is better

#### **Reliability**
- **Definition:** Error rate of link
- **Protocol:** EIGRP
- **Range:** 0-255 (255 = 100% reliable)
- **Preference:** Higher is better

#### **Load**
- **Definition:** Current utilization of link
- **Protocol:** EIGRP
- **Range:** 0-255
- **Preference:** Lower is better

#### **Cost**
- **Definition:** Composite metric
- **Protocol:** OSPF, EIGRP
- **Calculation:** Varies by protocol
- **Preference:** Lower is better

## Administrative Distance

### **Purpose**
Administrative Distance (AD) determines the trustworthiness of route sources. Lower values are preferred.

### **Common AD Values**

| Route Source | Administrative Distance |
|--------------|------------------------|
| **Connected Route** | 0 |
| **Static Route** | 1 |
| **EIGRP Summary** | 5 |
| **External BGP** | 20 |
| **Internal EIGRP** | 90 |
| **IGRP** | 100 |
| **OSPF** | 110 |
| **IS-IS** | 115 |
| **RIP** | 120 |
| **External EIGRP** | 170 |
| **Internal BGP** | 200 |
| **Unknown** | 255 |

### **Route Selection Process**

#### **1. Longest Match**
- Most specific route wins
- Example: 192.168.1.0/24 beats 192.168.0.0/16

#### **2. Administrative Distance**
- Lower AD wins
- Example: Static (AD=1) beats OSPF (AD=110)

#### **3. Metric**
- Lower metric wins (within same protocol)
- Example: OSPF cost 10 beats OSPF cost 20

## Routing Convergence

### **Definition**
The time it takes for all routers to have consistent routing information after a network change.

### **Convergence Factors**

#### **1. Detection Time**
- Time to detect network failure
- Depends on: Interface monitoring, protocol timers

#### **2. Propagation Time**
- Time for routing updates to spread
- Depends on: Protocol type, network size

#### **3. Calculation Time**
- Time to recalculate routes
- Depends on: Algorithm complexity, router performance

### **Fast Convergence Features**

#### **1. Fast Reroute**
- Pre-computed backup paths
- Immediate failover capability

#### **2. Bidirectional Forwarding Detection (BFD)**
- Fast link failure detection
- Sub-second detection times

#### **3. Loop-Free Alternate (LFA)**
- Pre-computed loop-free backup paths
- No routing loops during convergence

---

## Summary

Routing is the fundamental process that enables internetwork communication. Understanding routing fundamentals, including packet forwarding, routing tables, metrics, and convergence, is essential for network design and troubleshooting. The choice between static and dynamic routing depends on network requirements, size, and management preferences. 