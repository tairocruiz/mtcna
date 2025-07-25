# Network Types and Topologies

## Network Media and Cabling

### **UTP (Unshielded Twisted Pair) Cables**

#### **What is UTP?**
**UTP (Unshielded Twisted Pair)** is the most common type of network cable used in Ethernet networks. It consists of four pairs of copper wires twisted together to reduce electromagnetic interference (EMI) and crosstalk.

#### **UTP Cable Structure:**
- **4 Pairs:** 8 individual copper wires
- **Twisted Pairs:** Each pair twisted at different rates
- **Color Coding:** Standard color scheme for easy identification
- **No Shielding:** Unlike STP, no metallic shielding around pairs

#### **UTP Cable Categories:**

##### **Cat 3 (Category 3)**
- **Bandwidth:** 16 MHz
- **Speed:** Up to 10 Mbps
- **Use Cases:** Legacy telephone systems, old Ethernet
- **Standard:** TIA/EIA-568-B
- **Status:** Obsolete for data networks

##### **Cat 5 (Category 5)**
- **Bandwidth:** 100 MHz
- **Speed:** Up to 100 Mbps (Fast Ethernet)
- **Use Cases:** Legacy networks, some home installations
- **Standard:** TIA/EIA-568-A
- **Status:** Mostly obsolete

##### **Cat 5e (Category 5 Enhanced)**
- **Bandwidth:** 100 MHz
- **Speed:** Up to 1 Gbps (Gigabit Ethernet)
- **Use Cases:** Home networks, small offices
- **Standard:** TIA/EIA-568-B.2
- **Features:** Reduced crosstalk, better performance than Cat 5

##### **Cat 6 (Category 6)**
- **Bandwidth:** 250 MHz
- **Speed:** Up to 1 Gbps (10 Gbps over short distances)
- **Use Cases:** Modern office networks, data centers
- **Standard:** TIA/EIA-568-B.2-1
- **Features:** Improved crosstalk performance, larger conductors

##### **Cat 6a (Category 6 Augmented)**
- **Bandwidth:** 500 MHz
- **Speed:** Up to 10 Gbps
- **Use Cases:** High-speed networks, data centers
- **Standard:** TIA/EIA-568-B.2-10
- **Features:** Full 10 Gbps support up to 100 meters

##### **Cat 7 (Category 7)**
- **Bandwidth:** 600 MHz
- **Speed:** Up to 10 Gbps
- **Use Cases:** High-performance networks
- **Standard:** ISO/IEC 11801
- **Features:** Individual pair shielding, GG45 connectors

##### **Cat 8 (Category 8)**
- **Bandwidth:** 2000 MHz
- **Speed:** Up to 25/40 Gbps
- **Use Cases:** Data centers, high-speed backbones
- **Standard:** TIA/EIA-568-B.2-1
- **Features:** Shielded, short distance (30 meters max)

#### **UTP Cable Standards:**

##### **TIA/EIA-568 Standards**
- **TIA/EIA-568-A:** Original standard (1995)
- **TIA/EIA-568-B:** Updated standard (2001)
- **TIA/EIA-568-C:** Current standard (2009)
- **TIA/EIA-568-D:** Latest standard (2018)

##### **ISO/IEC Standards**
- **ISO/IEC 11801:** International cabling standard
- **ISO/IEC 11801-1:** General requirements
- **ISO/IEC 11801-2:** Office premises
- **ISO/IEC 11801-3:** Industrial premises

#### **UTP Cable Classes:**

##### **Class A (Voice)**
- **Frequency:** Up to 100 kHz
- **Use Cases:** Telephone systems
- **Cable Type:** Cat 1, Cat 2

##### **Class B (Low Speed Data)**
- **Frequency:** Up to 1 MHz
- **Use Cases:** ISDN, basic data
- **Cable Type:** Cat 3

##### **Class C (Medium Speed Data)**
- **Frequency:** Up to 16 MHz
- **Use Cases:** 10BASE-T Ethernet
- **Cable Type:** Cat 3

##### **Class D (High Speed Data)**
- **Frequency:** Up to 100 MHz
- **Use Cases:** 100BASE-TX, 1000BASE-T
- **Cable Type:** Cat 5e, Cat 6

##### **Class E (Very High Speed Data)**
- **Frequency:** Up to 250 MHz
- **Use Cases:** 1000BASE-T, 10GBASE-T
- **Cable Type:** Cat 6

##### **Class EA (Enhanced Very High Speed Data)**
- **Frequency:** Up to 500 MHz
- **Use Cases:** 10GBASE-T
- **Cable Type:** Cat 6a

##### **Class F (High Frequency Data)**
- **Frequency:** Up to 600 MHz
- **Use Cases:** 10GBASE-T
- **Cable Type:** Cat 7

##### **Class FA (Enhanced High Frequency Data)**
- **Frequency:** Up to 1000 MHz
- **Use Cases:** 10GBASE-T, future applications
- **Cable Type:** Cat 7a

##### **Class I (Data Center)**
- **Frequency:** Up to 2000 MHz
- **Use Cases:** 25GBASE-T, 40GBASE-T
- **Cable Type:** Cat 8

#### **UTP Cable Characteristics:**

##### **Advantages:**
- **Cost-effective:** Cheaper than fiber optic cables
- **Easy Installation:** Flexible and easy to work with
- **Widely Available:** Standard in most environments
- **Compatible:** Works with most network equipment

##### **Disadvantages:**
- **Limited Distance:** Maximum 100 meters for most applications
- **Susceptible to EMI:** No shielding against interference
- **Bandwidth Limitations:** Lower bandwidth than fiber
- **Security:** Can be tapped more easily than fiber

#### **UTP Cable Installation Best Practices:**

##### **Cable Management:**
- **Proper Routing:** Avoid sharp bends and kinks
- **Cable Ties:** Use appropriate cable management tools
- **Labeling:** Clearly label all cables
- **Documentation:** Maintain cable run documentation

##### **Performance Considerations:**
- **Maximum Length:** 100 meters (328 feet) for most applications
- **Bend Radius:** Minimum 4x cable diameter
- **Tension:** Avoid excessive pulling force
- **Environmental:** Protect from moisture and extreme temperatures

---

## Types of Networks by Geographic Scope

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