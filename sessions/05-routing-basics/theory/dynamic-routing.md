# Dynamic Routing Protocols

## What is Dynamic Routing?

**Dynamic routing** is a routing method where routers automatically learn and share routing information with each other using routing protocols. Unlike static routing, dynamic routing automatically adapts to network changes and provides fault tolerance.

## Routing Protocol Categories

### **1. Distance Vector Protocols**
- **Operation:** Routers share entire routing tables with neighbors
- **Algorithm:** Bellman-Ford algorithm
- **Updates:** Periodic updates (every 30-90 seconds)
- **Examples:** RIP, EIGRP (hybrid)

### **2. Link State Protocols**
- **Operation:** Routers share link state information with all routers
- **Algorithm:** Dijkstra's Shortest Path First (SPF)
- **Updates:** Event-driven updates
- **Examples:** OSPF, IS-IS

### **3. Path Vector Protocols**
- **Operation:** Routers share path information
- **Algorithm:** Path vector algorithm
- **Updates:** Event-driven updates
- **Examples:** BGP

## Distance Vector vs Link State

### **Distance Vector Characteristics**

#### **Advantages**
- **Simple:** Easy to understand and configure
- **Low Overhead:** Minimal CPU and memory usage
- **Scalable:** Works well in small networks
- **Predictable:** Simple metric calculations

#### **Disadvantages**
- **Slow Convergence:** Takes time to detect and respond to changes
- **Count-to-Infinity:** Can cause routing loops
- **Limited Information:** Only knows distance and direction
- **Split Horizon:** Prevents some loops but limits information

#### **Operation**
```
Router A → Router B: "I can reach 192.168.1.0/24 in 2 hops"
Router B → Router C: "I can reach 192.168.1.0/24 in 3 hops"
```

### **Link State Characteristics**

#### **Advantages**
- **Fast Convergence:** Quickly detects and responds to changes
- **Loop-Free:** No routing loops due to SPF algorithm
- **Detailed Information:** Knows entire network topology
- **Hierarchical:** Supports area-based design

#### **Disadvantages**
- **Complex:** More difficult to understand and configure
- **High Overhead:** More CPU and memory usage
- **Resource Intensive:** Requires more processing power
- **Complex Troubleshooting:** More difficult to debug

#### **Operation**
```
Router A → All Routers: "My links are: A-B (cost=10), A-C (cost=5)"
Router B → All Routers: "My links are: B-A (cost=10), B-C (cost=15)"
Router C → All Routers: "My links are: C-A (cost=5), C-B (cost=15)"
```

## Common Routing Protocols

### **1. RIP (Routing Information Protocol)**

#### **Characteristics**
- **Type:** Distance Vector
- **Metric:** Hop count (max 15 hops)
- **Updates:** Every 30 seconds
- **Administrative Distance:** 120
- **Version:** RIPv1, RIPv2

#### **RIPv1 vs RIPv2**
| Feature | RIPv1 | RIPv2 |
|---------|-------|-------|
| **Subnet Masks** | No | Yes |
| **Authentication** | No | Yes |
| **Multicast Updates** | No | Yes |
| **VLSM Support** | No | Yes |

#### **RIP Configuration (RouterOS)**
```bash
# Enable RIP
/routing rip instance add name=rip-instance

# Add networks
/routing rip interface add interface=ether1
/routing rip interface add interface=ether2

# Start RIP
/routing rip instance enable rip-instance
```

### **2. OSPF (Open Shortest Path First)**

#### **Characteristics**
- **Type:** Link State
- **Metric:** Cost (bandwidth-based)
- **Updates:** Event-driven
- **Administrative Distance:** 110
- **Areas:** Hierarchical design

#### **OSPF Areas**
- **Backbone Area (Area 0):** Central area connecting all other areas
- **Regular Areas:** Connect to backbone area
- **Stub Areas:** Don't receive external routes
- **Totally Stubby Areas:** Only default route from backbone

#### **OSPF Configuration (RouterOS)**
```bash
# Enable OSPF
/routing ospf instance add name=ospf-instance

# Add networks
/routing ospf network add network=192.168.1.0/24 area=backbone
/routing ospf network add network=192.168.2.0/24 area=backbone

# Start OSPF
/routing ospf instance enable ospf-instance
```

### **3. EIGRP (Enhanced Interior Gateway Routing Protocol)**

#### **Characteristics**
- **Type:** Advanced Distance Vector (hybrid)
- **Metric:** Composite (bandwidth, delay, reliability, load)
- **Updates:** Event-driven with periodic updates
- **Administrative Distance:** 90 (internal), 170 (external)
- **Features:** Fast convergence, load balancing

#### **EIGRP Features**
- **DUAL Algorithm:** Diffusing Update Algorithm
- **Successor Routes:** Best path to destination
- **Feasible Successors:** Backup paths
- **Query Process:** Route recomputation

#### **EIGRP Configuration (RouterOS)**
```bash
# Enable EIGRP
/routing eigrp instance add name=eigrp-instance as=100

# Add networks
/routing eigrp network add network=192.168.1.0/24
/routing eigrp network add network=192.168.2.0/24

# Start EIGRP
/routing eigrp instance enable eigrp-instance
```

### **4. BGP (Border Gateway Protocol)**

#### **Characteristics**
- **Type:** Path Vector
- **Metric:** Multiple attributes (AS_PATH, LOCAL_PREF, etc.)
- **Updates:** Event-driven
- **Administrative Distance:** 20 (external), 200 (internal)
- **Purpose:** Inter-domain routing

#### **BGP Types**
- **External BGP (eBGP):** Between different autonomous systems
- **Internal BGP (iBGP):** Within same autonomous system

#### **BGP Configuration (RouterOS)**
```bash
# Enable BGP
/routing bgp instance add name=bgp-instance as=65000

# Add peers
/routing bgp peer add name=peer1 remote-address=203.0.113.1 remote-as=65001

# Start BGP
/routing bgp instance enable bgp-instance
```

## Routing Convergence

### **Definition**
**Convergence** is the time it takes for all routers in a network to have consistent routing information after a topology change.

### **Convergence Phases**

#### **1. Detection Phase**
- **Time:** Seconds to minutes
- **Process:** Routers detect topology changes
- **Methods:** Interface monitoring, protocol timers

#### **2. Information Exchange Phase**
- **Time:** Seconds
- **Process:** Routers share updated information
- **Methods:** Routing protocol updates

#### **3. Route Calculation Phase**
- **Time:** Milliseconds to seconds
- **Process:** Routers recalculate routes
- **Methods:** Routing algorithms (SPF, DUAL, etc.)

#### **4. Route Installation Phase**
- **Time:** Milliseconds
- **Process:** New routes installed in routing table
- **Methods:** Route selection process

### **Convergence Optimization**

#### **Fast Convergence Features**
- **BFD (Bidirectional Forwarding Detection):** Sub-second failure detection
- **Fast Reroute:** Pre-computed backup paths
- **Loop-Free Alternate (LFA):** Immediate failover
- **Graceful Restart:** Maintain forwarding during restart

#### **Protocol-Specific Optimizations**
- **RIP:** Triggered updates, split horizon
- **OSPF:** LSA flooding, SPF optimization
- **EIGRP:** DUAL algorithm, feasible successors
- **BGP:** Route reflectors, confederations

## Route Redistribution

### **Definition**
**Route redistribution** is the process of sharing routes learned by one routing protocol with another routing protocol.

### **Redistribution Types**

#### **1. One-Way Redistribution**
- **Definition:** Routes flow in one direction only
- **Example:** Static routes redistributed into OSPF
- **Use Case:** Connecting static routes to dynamic network

#### **2. Two-Way Redistribution**
- **Definition:** Routes flow in both directions
- **Example:** OSPF routes redistributed into RIP, and vice versa
- **Use Case:** Connecting different routing domains

#### **3. Mutual Redistribution**
- **Definition:** Multiple protocols share routes bidirectionally
- **Example:** OSPF, RIP, and static routes all redistributed
- **Use Case:** Complex multi-protocol networks

### **Redistribution Configuration**

#### **RouterOS Redistribution**
```bash
# Redistribute static routes into OSPF
/routing ospf instance set ospf-instance redistribute-static=yes

# Redistribute OSPF routes into RIP
/routing rip instance set rip-instance redistribute-ospf=yes

# Redistribute connected routes into BGP
/routing bgp instance set bgp-instance redistribute-connected=yes
```

### **Redistribution Best Practices**

#### **1. Avoid Routing Loops**
- **Use Route Tags:** Mark redistributed routes
- **Filter Routes:** Prevent unwanted redistribution
- **Set Metrics:** Assign appropriate metrics
- **Use Distribute Lists:** Control route distribution

#### **2. Manage Administrative Distance**
- **Set Appropriate AD:** Prevent route conflicts
- **Use Route Maps:** Control redistribution
- **Monitor Routes:** Verify redistribution

#### **3. Plan Redistribution Points**
- **Single Point:** Redistribute at one router
- **Multiple Points:** Use consistent policies
- **Documentation:** Document redistribution policies

## Routing Protocol Selection

### **Factors to Consider**

#### **1. Network Size**
- **Small Networks (< 50 routers):** RIP, OSPF
- **Medium Networks (50-200 routers):** OSPF, EIGRP
- **Large Networks (> 200 routers):** OSPF, BGP

#### **2. Convergence Requirements**
- **Fast Convergence:** OSPF, EIGRP
- **Slow Convergence:** RIP
- **Very Fast:** BFD with any protocol

#### **3. Resource Constraints**
- **Low CPU/Memory:** RIP, static routing
- **High CPU/Memory:** OSPF, BGP
- **Balanced:** EIGRP

#### **4. Administrative Overhead**
- **Low Overhead:** Static routing
- **Medium Overhead:** RIP, OSPF
- **High Overhead:** BGP, complex OSPF

### **Protocol Comparison**

| Protocol | Type | Metric | Convergence | Scalability | Complexity |
|----------|------|--------|-------------|-------------|------------|
| **RIP** | Distance Vector | Hop Count | Slow | Low | Low |
| **OSPF** | Link State | Cost | Fast | High | Medium |
| **EIGRP** | Hybrid | Composite | Very Fast | High | Medium |
| **BGP** | Path Vector | Multiple | Slow | Very High | High |

---

## Summary

Dynamic routing protocols provide automatic route learning and fault tolerance. Understanding the differences between distance vector and link state protocols, along with their characteristics and configuration methods, is essential for designing and implementing effective routing solutions. Proper protocol selection and configuration ensure optimal network performance and reliability. 