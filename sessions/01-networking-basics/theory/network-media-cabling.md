# Network Media and Cabling

## Introduction to Network Media

**Network media** refers to the physical cables and wireless technologies used to transmit data between network devices. The choice of media affects network performance, reliability, and cost.

## Types of Network Media

### **1. Copper Cables**
- **UTP (Unshielded Twisted Pair):** Most common for Ethernet
- **STP (Shielded Twisted Pair):** Enhanced EMI protection
- **Coaxial Cable:** Legacy and cable TV applications

### **2. Fiber Optic Cables**
- **Single-mode Fiber:** Long-distance, high-speed
- **Multi-mode Fiber:** Short-distance, cost-effective

### **3. Wireless Media**
- **Radio Waves:** Wi-Fi, Bluetooth
- **Microwave:** Point-to-point links
- **Infrared:** Short-range communication

---

## UTP (Unshielded Twisted Pair) Cables

### **What is UTP?**

**UTP (Unshielded Twisted Pair)** is the most common type of network cable used in Ethernet networks. It consists of four pairs of copper wires twisted together to reduce electromagnetic interference (EMI) and crosstalk.

### **UTP Cable Structure**

#### **Physical Components:**
- **4 Pairs:** 8 individual copper wires (24 AWG typically)
- **Twisted Pairs:** Each pair twisted at different rates
- **Color Coding:** Standard color scheme for easy identification
- **Outer Jacket:** PVC or plenum-rated material
- **No Shielding:** Unlike STP, no metallic shielding around pairs

#### **Color Coding Standards:**
```
Pair 1: Blue/Blue-White
Pair 2: Orange/Orange-White
Pair 3: Green/Green-White
Pair 4: Brown/Brown-White
```

### **UTP Cable Categories**

#### **Cat 3 (Category 3)**
- **Bandwidth:** 16 MHz
- **Speed:** Up to 10 Mbps
- **Use Cases:** Legacy telephone systems, old Ethernet
- **Standard:** TIA/EIA-568-B
- **Status:** Obsolete for data networks
- **Distance:** 100 meters

#### **Cat 5 (Category 5)**
- **Bandwidth:** 100 MHz
- **Speed:** Up to 100 Mbps (Fast Ethernet)
- **Use Cases:** Legacy networks, some home installations
- **Standard:** TIA/EIA-568-A
- **Status:** Mostly obsolete
- **Distance:** 100 meters

#### **Cat 5e (Category 5 Enhanced)**
- **Bandwidth:** 100 MHz
- **Speed:** Up to 1 Gbps (Gigabit Ethernet)
- **Use Cases:** Home networks, small offices
- **Standard:** TIA/EIA-568-B.2
- **Features:** Reduced crosstalk, better performance than Cat 5
- **Distance:** 100 meters
- **Cost:** Affordable

#### **Cat 6 (Category 6)**
- **Bandwidth:** 250 MHz
- **Speed:** Up to 1 Gbps (10 Gbps over short distances)
- **Use Cases:** Modern office networks, data centers
- **Standard:** TIA/EIA-568-B.2-1
- **Features:** Improved crosstalk performance, larger conductors
- **Distance:** 100 meters (10 Gbps: 55 meters)
- **Cost:** Moderate

#### **Cat 6a (Category 6 Augmented)**
- **Bandwidth:** 500 MHz
- **Speed:** Up to 10 Gbps
- **Use Cases:** High-speed networks, data centers
- **Standard:** TIA/EIA-568-B.2-10
- **Features:** Full 10 Gbps support up to 100 meters
- **Distance:** 100 meters
- **Cost:** Higher than Cat 6

#### **Cat 7 (Category 7)**
- **Bandwidth:** 600 MHz
- **Speed:** Up to 10 Gbps
- **Use Cases:** High-performance networks
- **Standard:** ISO/IEC 11801
- **Features:** Individual pair shielding, GG45 connectors
- **Distance:** 100 meters
- **Cost:** Premium

#### **Cat 8 (Category 8)**
- **Bandwidth:** 2000 MHz
- **Speed:** Up to 25/40 Gbps
- **Use Cases:** Data centers, high-speed backbones
- **Standard:** TIA/EIA-568-B.2-1
- **Features:** Shielded, short distance (30 meters max)
- **Distance:** 30 meters
- **Cost:** Highest

### **UTP Cable Standards**

#### **TIA/EIA-568 Standards**
- **TIA/EIA-568-A:** Original standard (1995)
- **TIA/EIA-568-B:** Updated standard (2001)
- **TIA/EIA-568-C:** Current standard (2009)
- **TIA/EIA-568-D:** Latest standard (2018)

#### **ISO/IEC Standards**
- **ISO/IEC 11801:** International cabling standard
- **ISO/IEC 11801-1:** General requirements
- **ISO/IEC 11801-2:** Office premises
- **ISO/IEC 11801-3:** Industrial premises

### **UTP Cable Classes**

#### **Class A (Voice)**
- **Frequency:** Up to 100 kHz
- **Use Cases:** Telephone systems
- **Cable Type:** Cat 1, Cat 2

#### **Class B (Low Speed Data)**
- **Frequency:** Up to 1 MHz
- **Use Cases:** ISDN, basic data
- **Cable Type:** Cat 3

#### **Class C (Medium Speed Data)**
- **Frequency:** Up to 16 MHz
- **Use Cases:** 10BASE-T Ethernet
- **Cable Type:** Cat 3

#### **Class D (High Speed Data)**
- **Frequency:** Up to 100 MHz
- **Use Cases:** 100BASE-TX, 1000BASE-T
- **Cable Type:** Cat 5e, Cat 6

#### **Class E (Very High Speed Data)**
- **Frequency:** Up to 250 MHz
- **Use Cases:** 1000BASE-T, 10GBASE-T
- **Cable Type:** Cat 6

#### **Class EA (Enhanced Very High Speed Data)**
- **Frequency:** Up to 500 MHz
- **Use Cases:** 10GBASE-T
- **Cable Type:** Cat 6a

#### **Class F (High Frequency Data)**
- **Frequency:** Up to 600 MHz
- **Use Cases:** 10GBASE-T
- **Cable Type:** Cat 7

#### **Class FA (Enhanced High Frequency Data)**
- **Frequency:** Up to 1000 MHz
- **Use Cases:** 10GBASE-T, future applications
- **Cable Type:** Cat 7a

#### **Class I (Data Center)**
- **Frequency:** Up to 2000 MHz
- **Use Cases:** 25GBASE-T, 40GBASE-T
- **Cable Type:** Cat 8

### **UTP Cable Characteristics**

#### **Advantages:**
- **Cost-effective:** Cheaper than fiber optic cables
- **Easy Installation:** Flexible and easy to work with
- **Widely Available:** Standard in most environments
- **Compatible:** Works with most network equipment
- **Termination:** Easy to terminate and test

#### **Disadvantages:**
- **Limited Distance:** Maximum 100 meters for most applications
- **Susceptible to EMI:** No shielding against interference
- **Bandwidth Limitations:** Lower bandwidth than fiber
- **Security:** Can be tapped more easily than fiber
- **Environmental:** Sensitive to moisture and temperature

### **UTP Cable Installation Best Practices**

#### **Cable Management:**
- **Proper Routing:** Avoid sharp bends and kinks
- **Cable Ties:** Use appropriate cable management tools
- **Labeling:** Clearly label all cables
- **Documentation:** Maintain cable run documentation
- **Organized Layout:** Plan cable routes in advance

#### **Performance Considerations:**
- **Maximum Length:** 100 meters (328 feet) for most applications
- **Bend Radius:** Minimum 4x cable diameter
- **Tension:** Avoid excessive pulling force (max 25 lbs)
- **Environmental:** Protect from moisture and extreme temperatures
- **Separation:** Keep away from electrical interference sources

#### **Testing and Certification:**
- **Wire Map Test:** Verify correct pin connections
- **Length Test:** Ensure cable doesn't exceed maximum length
- **Attenuation Test:** Measure signal loss
- **NEXT Test:** Near-End Crosstalk measurement
- **Certification:** Use proper cable certification tools

### **UTP Cable Termination**

#### **RJ-45 Connector Pinout:**

##### **T568A Standard:**
```
Pin 1: Green-White  (Transmit +)
Pin 2: Green        (Transmit -)
Pin 3: Orange-White (Receive +)
Pin 4: Blue         (Unused)
Pin 5: Blue-White   (Unused)
Pin 6: Orange       (Receive -)
Pin 7: Brown-White  (Unused)
Pin 8: Brown        (Unused)
```

##### **T568B Standard:**
```
Pin 1: Orange-White (Transmit +)
Pin 2: Orange       (Transmit -)
Pin 3: Green-White  (Receive +)
Pin 4: Blue         (Unused)
Pin 5: Blue-White   (Unused)
Pin 6: Green        (Receive -)
Pin 7: Brown-White  (Unused)
Pin 8: Brown        (Unused)
```

#### **Ethernet Pin Functions:**

##### **10/100 Mbps Ethernet (2 pairs used):**
- **Pins 1,2:** Transmit pair (Tx+ and Tx-)
- **Pins 3,6:** Receive pair (Rx+ and Rx-)
- **Pins 4,5,7,8:** Unused

##### **1000 Mbps Ethernet (4 pairs used):**
- **Pins 1,2:** Transmit pair (Tx+ and Tx-)
- **Pins 3,6:** Receive pair (Rx+ and Rx-)
- **Pins 4,5:** Bidirectional pair (BiDi+ and BiDi-)
- **Pins 7,8:** Bidirectional pair (BiDi+ and BiDi-)

#### **Cable Pinout Comparison:**

##### **Straight-through Cable:**
```
End A (T568B)    End B (T568B)
Pin 1 → Pin 1    (Orange-White)
Pin 2 → Pin 2    (Orange)
Pin 3 → Pin 3    (Green-White)
Pin 4 → Pin 4    (Blue)
Pin 5 → Pin 5    (Blue-White)
Pin 6 → Pin 6    (Green)
Pin 7 → Pin 7    (Brown-White)
Pin 8 → Pin 8    (Brown)
```

##### **Crossover Cable:**
```
End A (T568B)    End B (T568A)
Pin 1 → Pin 3    (Orange-White → Green-White)
Pin 2 → Pin 6    (Orange → Green)
Pin 3 → Pin 1    (Green-White → Orange-White)
Pin 4 → Pin 4    (Blue → Blue)
Pin 5 → Pin 5    (Blue-White → Blue-White)
Pin 6 → Pin 2    (Green → Orange)
Pin 7 → Pin 7    (Brown-White → Brown-White)
Pin 8 → Pin 8    (Brown → Brown)
```

##### **Rollover Cable:**
```
End A            End B
Pin 1 → Pin 8
Pin 2 → Pin 7
Pin 3 → Pin 6
Pin 4 → Pin 5
Pin 5 → Pin 4
Pin 6 → Pin 3
Pin 7 → Pin 2
Pin 8 → Pin 1
```

#### **Cable Types:**

##### **Straight-through Cable (T568B to T568B)**
- **Pinout:** Same wiring standard on both ends
- **Use Cases:**
  - **PC to Switch:** Computer connecting to network switch
  - **PC to Router:** Computer connecting to router
  - **PC to Hub:** Computer connecting to network hub
  - **Server to Switch:** Server connecting to network switch
  - **Printer to Switch:** Network printer connecting to switch
  - **IP Phone to Switch:** VoIP phone connecting to switch
  - **Access Point to Switch:** Wireless access point to switch
  - **Any end device to network infrastructure**

##### **Crossover Cable (T568B to T568A)**
- **Pinout:** Different wiring standard on each end
- **Use Cases:**
  - **PC to PC:** Direct computer-to-computer connection
  - **Switch to Switch:** Connecting two network switches
  - **Hub to Hub:** Connecting two network hubs
  - **Router to Router:** Connecting two routers
  - **PC to Router (direct):** Computer directly to router (no switch)
  - **Server to Server:** Direct server-to-server connection
  - **Any like device to like device connection**

##### **Rollover Cable (Console Cable)**
- **Pinout:** Completely reversed pinout (Pin 1 to Pin 8, Pin 2 to Pin 7, etc.)
- **Use Cases:**
  - **Console Connection:** Connecting to network device console port
  - **Router Management:** Initial router configuration
  - **Switch Management:** Initial switch configuration
  - **Firewall Management:** Initial firewall configuration
  - **Any network device initial setup**

#### **Why Different Cable Types?**

##### **Straight-through Cable Logic:**
```
PC (MDI) → Switch (MDI-X)
- PC transmits on pins 1,2 (MDI)
- Switch receives on pins 1,2 (MDI-X)
- PC receives on pins 3,6 (MDI)
- Switch transmits on pins 3,6 (MDI-X)
```

##### **Crossover Cable Logic:**
```
PC (MDI) → PC (MDI)
- PC1 transmits on pins 1,2 (MDI)
- PC2 receives on pins 3,6 (MDI) ← Crossover needed
- PC1 receives on pins 3,6 (MDI)
- PC2 transmits on pins 1,2 (MDI) ← Crossover needed
```

#### **Auto-MDI/MDI-X Technology:**

##### **What is Auto-MDI/MDI-X?**
**Auto-MDI/MDI-X (Automatic Medium Dependent Interface/Medium Dependent Interface Crossover)** is a technology that allows Ethernet devices to automatically detect the cable type and adjust their transmit/receive pairs accordingly.

##### **How Auto-MDI/MDI-X Works:**
1. **Detection Phase:** Device sends test signals on both transmit and receive pairs
2. **Analysis:** Device analyzes which pairs receive signals from the other end
3. **Configuration:** Device automatically configures its interface (MDI or MDI-X)
4. **Connection:** Normal Ethernet communication begins

##### **Technical Process:**
```
Step 1: Device A sends test signal on pins 1,2 (Tx pair)
Step 2: Device B receives signal on pins 1,2 (Tx pair)
Step 3: Device B detects "like device" (both using Tx on same pins)
Step 4: Device B switches to MDI-X mode (Tx on pins 3,6)
Step 5: Both devices now have proper Tx/Rx pair alignment
Step 6: Normal Ethernet communication established
```

##### **Why Modern Devices Can Use Straight-through:**
- **Automatic Detection:** Devices detect cable type automatically
- **Interface Switching:** Can switch between MDI and MDI-X modes
- **Intelligent Configuration:** Determines optimal pin configuration
- **Backward Compatibility:** Works with both straight-through and crossover cables

##### **Device Compatibility:**
```
Modern Devices (Auto-MDI/MDI-X Support):
- Switches (2000+ models)
- Routers (2000+ models)
- Network Interface Cards (2000+ models)
- Access Points (2000+ models)
- Most enterprise and consumer equipment

Legacy Devices (No Auto-MDI/MDI-X):
- Older switches (pre-2000)
- Older routers (pre-2000)
- Some industrial equipment
- Specialized network devices
```

##### **Auto-MDI/MDI-X Standards:**
- **IEEE 802.3ab:** Gigabit Ethernet standard (1999)
- **IEEE 802.3u:** Fast Ethernet standard (1995)
- **Industry Adoption:** Widespread by early 2000s
- **Current Status:** Standard feature on all modern devices

##### **Benefits of Auto-MDI/MDI-X:**
- **Reduced Cable Types:** Only need straight-through cables
- **Simplified Inventory:** Fewer cable types to stock
- **Faster Deployment:** No need to determine cable type
- **Reduced Errors:** Eliminates wrong cable type mistakes
- **Cost Savings:** Lower cable inventory costs

##### **When Auto-MDI/MDI-X May Fail:**
- **Legacy Equipment:** Devices without auto-detection
- **Damaged Cables:** Physical damage affecting detection
- **Poor Termination:** Incorrect wire mapping
- **Environmental Issues:** EMI interference affecting signals
- **Power Issues:** Insufficient power for detection circuits

##### **Troubleshooting Auto-MDI/MDI-X:**
```
Problem: Two modern switches won't connect with straight-through cable
Solution Steps:
1. Check cable integrity with tester
2. Verify both devices support auto-MDI/MDI-X
3. Try power cycling both devices
4. Test with known good crossover cable
5. Check for firmware updates
6. Verify cable length within limits
```

##### **Best Practices:**
- **Always carry crossover cable** for troubleshooting
- **Test with both cable types** if connection fails
- **Document device capabilities** for future reference
- **Keep legacy equipment** considerations in mind
- **Verify auto-MDI/MDI-X support** in device specifications

#### **Legacy vs Modern Device Behavior:**

##### **Legacy Network (Pre-2000):**
```
Switch A (MDI-X) ←→ Switch B (MDI-X)
- Both switches use pins 3,6 for transmit
- Both switches use pins 1,2 for receive
- Result: No communication (Tx to Tx, Rx to Rx)
- Solution: Must use crossover cable

PC (MDI) ←→ PC (MDI)
- Both PCs use pins 1,2 for transmit
- Both PCs use pins 3,6 for receive
- Result: No communication (Tx to Tx, Rx to Rx)
- Solution: Must use crossover cable
```

##### **Modern Network (2000+):**
```
Switch A (Auto-MDI/MDI-X) ←→ Switch B (Auto-MDI/MDI-X)
- Both switches start in MDI-X mode
- Auto-detection determines cable type
- One switch switches to MDI mode automatically
- Result: Communication established with straight-through cable

PC (Auto-MDI/MDI-X) ←→ PC (Auto-MDI/MDI-X)
- Both PCs start in MDI mode
- Auto-detection determines cable type
- One PC switches to MDI-X mode automatically
- Result: Communication established with straight-through cable
```

##### **Real-World Example:**

###### **Scenario 1: Two Modern Switches**
```
Equipment: Cisco Catalyst 2960 switches (2010+)
Cable: Straight-through Cat 6
Result: ✅ Connection established automatically
Process: Auto-MDI/MDI-X detection and configuration
Time: 2-5 seconds for auto-negotiation
```

###### **Scenario 2: Two Legacy Switches**
```
Equipment: Cisco Catalyst 1900 switches (1995-2000)
Cable: Straight-through Cat 5
Result: ❌ No connection
Process: Both devices use same pin configuration
Solution: Must use crossover cable
```

###### **Scenario 3: Mixed Environment**
```
Equipment: Modern switch + Legacy switch
Cable: Straight-through Cat 5e
Result: ❌ No connection (legacy device can't auto-detect)
Process: Modern device tries auto-detection, legacy device doesn't respond
Solution: Use crossover cable or upgrade legacy device
```

#### **Auto-MDI/MDI-X Detection Timeline:**
```
0-1 seconds: Device power-up and initialization
1-2 seconds: Auto-MDI/MDI-X detection signals
2-3 seconds: Interface configuration
3-5 seconds: Link establishment and negotiation
5+ seconds: Normal Ethernet communication
```

#### **Industry Impact:**
- **2000-2005:** Gradual adoption of auto-MDI/MDI-X
- **2005-2010:** Widespread implementation
- **2010+:** Standard feature on all devices
- **2020+:** Crossover cables mainly for troubleshooting

#### **Cable Selection Decision Guide:**

##### **When to Use Straight-through Cable:**
```
Device Type A → Device Type B
PC/Server → Switch/Hub
PC/Server → Router
PC/Server → Access Point
Printer → Switch
IP Phone → Switch
Camera → Switch
Any End Device → Network Infrastructure
```

##### **When to Use Crossover Cable:**
```
Device Type A → Device Type A
PC → PC
Server → Server
Switch → Switch
Hub → Hub
Router → Router
Access Point → Access Point
Switch → Hub
Router → Switch (some cases)
```

##### **When to Use Rollover Cable:**
```
Management Device → Network Device Console Port
PC → Router Console
PC → Switch Console
PC → Firewall Console
PC → Server Console (if available)
Any Management Device → Any Network Device Console
```

#### **Practical Examples:**

##### **Home Network Setup:**
```
Modem → Router (usually straight-through)
Router → Switch (usually straight-through)
Switch → PC (straight-through)
Switch → Laptop (straight-through)
Switch → Smart TV (straight-through)
```

##### **Office Network Setup:**
```
Core Switch → Distribution Switch (crossover or straight-through with auto-MDI)
Distribution Switch → Access Switch (crossover or straight-through with auto-MDI)
Access Switch → PC (straight-through)
Access Switch → Printer (straight-through)
Access Switch → IP Phone (straight-through)
```

##### **Data Center Setup:**
```
Core Switch → Core Switch (crossover or straight-through with auto-MDI)
Core Switch → Server (straight-through)
Core Switch → Storage Device (straight-through)
Management PC → Device Console (rollover)
```

#### **Troubleshooting Cable Issues:**

##### **Common Problems:**
- **Wrong cable type:** Using straight-through instead of crossover
- **Auto-MDI failure:** Legacy devices not supporting auto-detection
- **Damaged cable:** Physical damage affecting connectivity
- **Poor termination:** Incorrect crimping or wire order

##### **Diagnostic Steps:**
1. **Check cable type:** Verify straight-through vs crossover
2. **Test with known good cable:** Use certified cable for testing
3. **Check device compatibility:** Verify auto-MDI support
4. **Use cable tester:** Verify wire map and continuity
5. **Check link lights:** Verify physical layer connectivity

### **UTP Cable Troubleshooting**

#### **Common Issues:**
- **Open Circuit:** Broken wire or poor termination
- **Short Circuit:** Wires touching each other
- **Split Pair:** Wires from different pairs connected
- **Reversed Pair:** Wires in a pair swapped
- **Crosstalk:** Interference between pairs

#### **Testing Tools:**
- **Cable Tester:** Basic continuity and wire map testing
- **Certification Tester:** Professional testing and certification
- **TDR (Time Domain Reflectometer):** Distance and fault location
- **Network Analyzer:** Advanced performance testing

---

## Other Network Media Types

### **STP (Shielded Twisted Pair)**
- **Shielding:** Metallic foil or braid around pairs
- **EMI Protection:** Better interference resistance
- **Use Cases:** Industrial environments, high EMI areas
- **Cost:** Higher than UTP

### **Coaxial Cable**
- **Structure:** Single conductor with shield
- **Use Cases:** Cable TV, legacy networks
- **Standards:** RG-6, RG-58, RG-59
- **Status:** Mostly replaced by UTP

### **Fiber Optic Cable**
- **Medium:** Glass or plastic fibers
- **Speed:** Very high bandwidth
- **Distance:** Long-distance transmission
- **Types:** Single-mode, Multi-mode

---

## Summary

UTP cables are the foundation of modern Ethernet networks:
- **Categories:** Cat 3 through Cat 8 with increasing performance
- **Standards:** TIA/EIA-568 and ISO/IEC 11801
- **Classes:** A through I based on frequency requirements
- **Installation:** Proper planning and testing essential
- **Future:** Cat 8 and beyond for high-speed applications

Understanding UTP cable specifications and installation practices is crucial for network design and troubleshooting.

**Next:** [Network Components](./network-components.md) 