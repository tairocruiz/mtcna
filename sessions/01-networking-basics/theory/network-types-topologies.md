# Network Types and Topologies

## Types of Networks by Geographic Scope

### 1. **PAN (Personal Area Network)**
- **Range:** 1-10 meters
- **Examples:** Bluetooth devices, USB connections
- **Use Cases:** Connecting smartphone to headphones, laptop to mouse
- **Technologies:** Bluetooth, USB, IEEE 802.15

### 2. **LAN (Local Area Network)**
- **Range:** Up to a few kilometers (typically within a building)
- **Examples:** Office networks, home networks, school networks
- **Use Cases:** File sharing, printer access, internet sharing
- **Technologies:** Ethernet (IEEE 802.3), Wi-Fi (IEEE 802.11)

### 3. **MAN (Metropolitan Area Network)**
- **Range:** City-wide (5-50 km)
- **Examples:** City government networks, cable TV networks
- **Use Cases:** Connecting multiple LANs across a city
- **Technologies:** Fiber optic, microwave, WiMAX

### 4. **WAN (Wide Area Network)**
- **Range:** Country-wide or global
- **Examples:** Internet, corporate networks spanning multiple cities
- **Use Cases:** Connecting remote offices, global communications
- **Technologies:** MPLS, satellite, leased lines, VPN

## Network Types by Relationship

### **Internet**
- Global network of interconnected networks
- Uses TCP/IP protocol suite
- Public access with proper connectivity

### **Intranet**
- Private network using internet technologies
- Restricted to organization members
- Uses web browsers and internet protocols

### **Extranet**
- Extended intranet allowing controlled external access
- Partners, suppliers, customers can access specific resources
- Secured with authentication and authorization

## Network Topologies

### **Physical vs Logical Topologies**

**Physical Topology:** How devices are physically connected with cables and hardware.

**Logical Topology:** How data flows through the network, regardless of physical layout.

### Common Physical Topologies

#### 1. **Bus Topology**
```
[Device] ---- [Device] ---- [Device] ---- [Device]
              |
         [Terminator]
```
- **Advantages:** Simple, cost-effective, easy to extend
- **Disadvantages:** Single point of failure, performance degrades with more devices
- **Use Cases:** Early Ethernet networks (10BASE2)

#### 2. **Star Topology**
```
        [Device]
            |
[Device] - [Hub/Switch] - [Device]
            |
        [Device]
```
- **Advantages:** Easy troubleshooting, failure isolation, scalable
- **Disadvantages:** Central device is single point of failure
- **Use Cases:** Modern Ethernet networks, most LANs

#### 3. **Ring Topology**
```
[Device] ---- [Device]
   |             |
[Device] ---- [Device]
```
- **Advantages:** Equal access, predictable performance
- **Disadvantages:** Single break affects entire network
- **Use Cases:** Token Ring networks, FDDI

#### 4. **Mesh Topology**

**Full Mesh:** Every device connects to every other device
**Partial Mesh:** Some devices have multiple connections

- **Advantages:** High redundancy, excellent fault tolerance
- **Disadvantages:** Expensive, complex to manage
- **Use Cases:** Internet backbone, critical infrastructure

#### 5. **Hybrid Topologies**
- Combination of two or more topologies
- **Star-Bus:** Multiple star networks connected via bus
- **Star-Ring:** Star networks connected in ring fashion

## Choosing the Right Topology

### Factors to Consider:
1. **Cost** - Budget for equipment and installation
2. **Scalability** - Future growth requirements
3. **Reliability** - Fault tolerance needs
4. **Performance** - Speed and bandwidth requirements
5. **Management** - Ease of troubleshooting and maintenance

---

## Summary

Understanding network types and topologies is crucial for designing and implementing effective networks. Each type serves different purposes and scales, while topologies determine how devices connect and communicate.

**Next:** [Network Components](./network-components.md)