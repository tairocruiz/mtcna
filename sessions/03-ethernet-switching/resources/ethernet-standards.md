# Ethernet Standards Reference

## 🎯 Overview
This reference provides comprehensive information about Ethernet standards, speeds, and specifications used in modern networking.

## 📋 IEEE 802.3 Ethernet Standards

### **Classic Ethernet (10 Mbps)**

#### **10BASE5 (Thick Ethernet)**
```
Standard: IEEE 802.3
Speed: 10 Mbps
Media: Thick coaxial cable (RG-8)
Maximum Distance: 500 meters
Topology: Bus
Connector: AUI (Attachment Unit Interface)
Status: Obsolete
```

#### **10BASE2 (Thin Ethernet)**
```
Standard: IEEE 802.3a
Speed: 10 Mbps
Media: Thin coaxial cable (RG-58)
Maximum Distance: 185 meters
Topology: Bus
Connector: BNC
Status: Obsolete
```

#### **10BASE-T**
```
Standard: IEEE 802.3i
Speed: 10 Mbps
Media: UTP Cat 3 or better
Maximum Distance: 100 meters
Topology: Star
Connector: RJ-45
Status: Legacy (still supported)
```

#### **10BASE-F**
```
Standard: IEEE 802.3j
Speed: 10 Mbps
Media: Fiber optic cable
Maximum Distance: 2,000 meters
Topology: Star
Connector: ST, SC, or LC
Status: Legacy
```

### **Fast Ethernet (100 Mbps)**

#### **100BASE-TX**
```
Standard: IEEE 802.3u
Speed: 100 Mbps
Media: UTP Cat 5 or better
Maximum Distance: 100 meters
Topology: Star
Connector: RJ-45
Encoding: 4B/5B + MLT-3
Status: Widely used
```

#### **100BASE-FX**
```
Standard: IEEE 802.3u
Speed: 100 Mbps
Media: Multimode fiber
Maximum Distance: 2,000 meters
Topology: Star
Connector: ST, SC, or LC
Status: Still used
```

#### **100BASE-T4**
```
Standard: IEEE 802.3u
Speed: 100 Mbps
Media: UTP Cat 3 (4 pairs)
Maximum Distance: 100 meters
Topology: Star
Connector: RJ-45
Status: Obsolete
```

### **Gigabit Ethernet (1 Gbps)**

#### **1000BASE-T**
```
Standard: IEEE 802.3ab
Speed: 1 Gbps
Media: UTP Cat 5e or better
Maximum Distance: 100 meters
Topology: Star
Connector: RJ-45
Encoding: PAM-5
Status: Widely used
```

#### **1000BASE-SX**
```
Standard: IEEE 802.3z
Speed: 1 Gbps
Media: Multimode fiber (850nm)
Maximum Distance: 550 meters
Topology: Star
Connector: LC, SC, or ST
Status: Common in data centers
```

#### **1000BASE-LX**
```
Standard: IEEE 802.3z
Speed: 1 Gbps
Media: Single-mode fiber (1310nm)
Maximum Distance: 5,000 meters
Topology: Star
Connector: LC, SC, or ST
Status: Long-distance applications
```

#### **1000BASE-CX**
```
Standard: IEEE 802.3z
Speed: 1 Gbps
Media: Twinaxial cable
Maximum Distance: 25 meters
Topology: Star
Connector: Specialized
Status: Obsolete
```

### **10 Gigabit Ethernet (10 Gbps)**

#### **10GBASE-T**
```
Standard: IEEE 802.3an
Speed: 10 Gbps
Media: UTP Cat 6a or better
Maximum Distance: 100 meters
Topology: Star
Connector: RJ-45
Encoding: PAM-16
Status: Growing adoption
```

#### **10GBASE-SR**
```
Standard: IEEE 802.3ae
Speed: 10 Gbps
Media: Multimode fiber (850nm)
Maximum Distance: 300 meters
Topology: Star
Connector: LC, SC, or ST
Status: Common in data centers
```

#### **10GBASE-LR**
```
Standard: IEEE 802.3ae
Speed: 10 Gbps
Media: Single-mode fiber (1310nm)
Maximum Distance: 10,000 meters
Topology: Star
Connector: LC, SC, or ST
Status: Long-distance applications
```

#### **10GBASE-ER**
```
Standard: IEEE 802.3ae
Speed: 10 Gbps
Media: Single-mode fiber (1550nm)
Maximum Distance: 40,000 meters
Topology: Star
Connector: LC, SC, or ST
Status: Extended reach applications
```

### **Modern Ethernet Standards**

#### **25 Gigabit Ethernet**
```
Standard: IEEE 802.3by
Speed: 25 Gbps
Media: Twinaxial, fiber
Maximum Distance: Varies by media
Topology: Star
Status: Data center applications
```

#### **40 Gigabit Ethernet**
```
Standard: IEEE 802.3ba
Speed: 40 Gbps
Media: Twinaxial, fiber
Maximum Distance: Varies by media
Topology: Star
Status: High-performance computing
```

#### **100 Gigabit Ethernet**
```
Standard: IEEE 802.3ba
Speed: 100 Gbps
Media: Fiber optic
Maximum Distance: Varies by media
Topology: Star
Status: Core networks, data centers
```

#### **400 Gigabit Ethernet**
```
Standard: IEEE 802.3bs
Speed: 400 Gbps
Media: Fiber optic
Maximum Distance: Varies by media
Topology: Star
Status: Emerging technology
```

---

## 🔧 Ethernet Frame Specifications

### **Standard Ethernet Frame**
```
┌─────────┬─────────┬─────────┬─────────┬─────────┬─────────┬─────────┐
│ Preamble│   SFD   │ Dest MAC│ Src MAC │Type/Len │  Data   │   FCS   │
│  7 bytes│ 1 byte  │ 6 bytes │ 6 bytes │ 2 bytes │46-1500B │ 4 bytes │
└─────────┴─────────┴─────────┴─────────┴─────────┴─────────┴─────────┘
Total: 64-1518 bytes
```

### **Jumbo Frame**
```
┌─────────┬─────────┬─────────┬─────────┬─────────┬─────────┬─────────┐
│ Preamble│   SFD   │ Dest MAC│ Src MAC │Type/Len │  Data   │   FCS   │
│  7 bytes│ 1 byte  │ 6 bytes │ 6 bytes │ 2 bytes │ 46-9000B│ 4 bytes │
└─────────┴─────────┴─────────┴─────────┴─────────┴─────────┴─────────┘
Total: 64-9018 bytes
```

### **VLAN Tagged Frame**
```
┌─────────┬─────────┬─────────┬─────────┬─────────┬─────────┬─────────┬─────────┐
│ Preamble│   SFD   │ Dest MAC│ Src MAC │ VLAN Tag│Type/Len │  Data   │   FCS   │
│  7 bytes│ 1 byte  │ 6 bytes │ 6 bytes │ 4 bytes │ 2 bytes │46-1500B │ 4 bytes │
└─────────┴─────────┴─────────┴─────────┴─────────┴─────────┴─────────┴─────────┘
Total: 68-1522 bytes
```

---

## 📊 Performance Characteristics

### **Speed Comparison**
```
Standard    | Speed     | Media Type    | Distance | Use Case
------------|-----------|---------------|----------|----------
10BASE-T    | 10 Mbps   | UTP Cat 3+    | 100m     | Legacy
100BASE-TX  | 100 Mbps  | UTP Cat 5+    | 100m     | General
1000BASE-T  | 1 Gbps    | UTP Cat 5e+   | 100m     | Standard
10GBASE-T   | 10 Gbps   | UTP Cat 6a+   | 100m     | High-speed
25GBASE-SR  | 25 Gbps   | Fiber         | 100m     | Data center
40GBASE-SR4 | 40 Gbps   | Fiber         | 150m     | Core network
100GBASE-SR4| 100 Gbps  | Fiber         | 100m     | Backbone
400GBASE-SR8| 400 Gbps  | Fiber         | 100m     | Future
```

### **Cable Requirements**
```
Speed       | Minimum Cable | Recommended | Distance
------------|---------------|-------------|----------
10 Mbps     | Cat 3         | Cat 5       | 100m
100 Mbps    | Cat 5         | Cat 5e      | 100m
1 Gbps      | Cat 5e        | Cat 6       | 100m
10 Gbps     | Cat 6a        | Cat 7       | 100m
25 Gbps     | Cat 8         | Cat 8       | 30m
40 Gbps     | Cat 8         | Fiber       | Varies
100 Gbps    | Fiber         | Fiber       | Varies
400 Gbps    | Fiber         | Fiber       | Varies
```

---

## 🔄 Auto-Negotiation

### **Supported Speeds**
```
10BASE-T: 10 Mbps half/full duplex
100BASE-TX: 100 Mbps half/full duplex
1000BASE-T: 1 Gbps full duplex
10GBASE-T: 10 Gbps full duplex
```

### **Negotiation Process**
```
1. Link Pulse Detection
2. Fast Link Pulse (FLP) Exchange
3. Capability Advertisement
4. Mode Selection
5. Link Establishment
```

### **Priority Order**
```
1. 10 Gbps full duplex
2. 1 Gbps full duplex
3. 1 Gbps half duplex
4. 100 Mbps full duplex
5. 100 Mbps half duplex
6. 10 Mbps full duplex
7. 10 Mbps half duplex
```

---

## 🛡️ Power over Ethernet (PoE)

### **PoE Standards**
```
Standard    | Power    | Voltage | Use Case
------------|----------|---------|----------
IEEE 802.3af| 15.4W    | 48V     | Basic PoE
IEEE 802.3at| 30W      | 48V     | PoE+
IEEE 802.3bt| 60W      | 48V     | PoE++
IEEE 802.3bt| 100W     | 48V     | PoE++ (Type 4)
```

### **PoE Classes**
```
Class 0: 0.44W to 12.95W
Class 1: 0.44W to 3.84W
Class 2: 3.84W to 6.49W
Class 3: 6.49W to 12.95W
Class 4: 12.95W to 25.5W (PoE+)
Class 5: 40W to 51W (PoE++)
Class 6: 51W to 71.3W (PoE++)
Class 7: 40W to 51W (PoE++)
Class 8: 71.3W to 100W (PoE++)
```

---

## 🔍 Troubleshooting Reference

### **Common Issues**
```
Speed Mismatch: Auto-negotiation failures
Duplex Mismatch: Half/full duplex conflicts
Cable Issues: Damaged or incorrect cables
Distance Exceeded: Beyond maximum cable length
Interference: EMI/RFI affecting signal quality
```

### **Troubleshooting Commands**
```
Windows:
- ipconfig /all: Interface details
- netsh interface show interface: Interface status

Linux:
- ethtool [interface]: Interface details
- ifconfig [interface]: Interface configuration

Cisco:
- show interface [interface]: Interface status
- show interface [interface] counters: Error statistics
```

### **Performance Testing**
```
Tools:
- iperf: Bandwidth testing
- ping: Latency testing
- Wireshark: Packet analysis
- Speed tests: Internet connectivity
```

---

## 📚 Additional Resources

### **Standards Organizations**
- **IEEE 802.3 Working Group:** Ethernet standards
- **TIA/EIA:** Cable standards
- **ISO/IEC:** International standards
- **ANSI:** American standards

### **Documentation**
- **IEEE 802.3 Standard:** Complete Ethernet specification
- **Cable Standards:** TIA/EIA-568 series
- **Manufacturer Documentation:** Vendor-specific guides
- **Network Design Guides:** Best practices

### **Tools and Software**
- **Cable Testers:** Physical layer testing
- **Protocol Analyzers:** Frame analysis
- **Network Monitors:** Performance monitoring
- **Configuration Tools:** Device management

---

## 🎓 Summary

### **Key Points**
- Ethernet standards evolve with increasing speeds
- Cable quality affects maximum performance
- Auto-negotiation ensures compatibility
- PoE provides power over data cables
- Proper troubleshooting requires systematic approach

### **Best Practices**
- Use appropriate cable categories for speed
- Test cables before deployment
- Monitor performance continuously
- Document network configurations
- Plan for future growth and upgrades

### **Future Trends**
- Higher speeds (400 Gbps and beyond)
- Improved power efficiency
- Enhanced security features
- Simplified management
- Integration with wireless technologies 