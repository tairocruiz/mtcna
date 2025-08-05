# Lab 02: VLAN Configuration

## 🎯 Objective
Learn to configure and manage Virtual Local Area Networks (VLANs) using MikroTik RouterOS. Develop skills in VLAN design, implementation, and troubleshooting for network segmentation and security.

## 🛠️ Prerequisites
- Access to a MikroTik switch or router with RouterOS
- Basic RouterOS configuration knowledge
- Understanding of VLAN concepts
- Network cables and devices for testing
- RouterOS documentation (if available)

## 📋 Lab Overview
This lab will help you:
1. Design and implement VLANs for network segmentation
2. Configure VLAN trunking between switches
3. Implement inter-VLAN routing
4. Test VLAN connectivity and isolation
5. Troubleshoot VLAN configuration issues

---

## Part 1: VLAN Design and Planning

### Step 1: VLAN Design Principles
**Understand VLAN design best practices:**

#### **VLAN Design Guidelines**
```
Network Segmentation:
- Separate departments or functions
- Improve security and performance
- Reduce broadcast domains
- Simplify network management

VLAN Numbering:
- Use consistent numbering scheme
- Reserve ranges for specific purposes
- Document VLAN assignments
- Plan for future growth

VLAN Naming:
- Use descriptive names
- Include department or function
- Follow naming conventions
- Document in network diagrams
```

#### **Sample VLAN Design**
```
VLAN 10: SALES (192.168.10.0/24)
VLAN 20: ENGINEERING (192.168.20.0/24)
VLAN 30: GUEST (192.168.30.0/24)
VLAN 40: MANAGEMENT (192.168.40.0/24)
VLAN 99: NATIVE (for trunk ports)
```

### Step 2: Network Topology Planning
**Plan the physical and logical network topology:**

#### **Physical Topology**
```
Switch Layout:
- Core Switch: Central distribution
- Access Switches: End device connections
- Trunk Links: Inter-switch connections
- Access Links: End device connections

Cable Planning:
- UTP cables for access ports
- Fiber or high-quality UTP for trunks
- Cable labeling and documentation
- Spare cable planning
```

#### **Logical Topology**
```
VLAN Distribution:
- VLAN 10: Sales department devices
- VLAN 20: Engineering department devices
- VLAN 30: Guest network devices
- VLAN 40: Network management devices

Traffic Flow:
- Intra-VLAN: Direct communication
- Inter-VLAN: Through router or Layer 3 switch
- Broadcast: Limited to VLAN scope
- Multicast: VLAN-specific forwarding
```

---

## Part 2: Basic VLAN Configuration

### Step 1: VLAN Creation
**Create VLANs on the switch:**

#### **VLAN Creation Commands**
```
Commands:
/interface vlan add name=[VLAN_NAME] vlan-id=[VLAN_ID]

Example:
/interface vlan add name=SALES vlan-id=10
/interface vlan add name=ENGINEERING vlan-id=20
/interface vlan add name=GUEST vlan-id=30
/interface vlan add name=MANAGEMENT vlan-id=40
/interface vlan add name=NATIVE vlan-id=99
```

#### **VLAN Verification**
```
Commands:
/interface vlan print: Display all VLANs
/interface vlan print brief: Summary VLAN information
/interface vlan print detail: Specific VLAN details
```

### Step 2: Access Port Configuration
**Configure ports for specific VLANs:**

#### **Access Port Setup**
```
Commands:
/interface ethernet switch set [PORT] vlan-mode=access
/interface ethernet switch set [PORT] vlan-id=[VLAN_ID]
/interface ethernet switch set [PORT] comment=[DESCRIPTION]

Example:
/interface ethernet switch set 1 vlan-mode=access
/interface ethernet switch set 1 vlan-id=10
/interface ethernet switch set 1 comment=SALES-PC-01

/interface ethernet switch set 2 vlan-mode=access
/interface ethernet switch set 2 vlan-id=20
/interface ethernet switch set 2 comment=ENGINEERING-PC-01
```

#### **Access Port Verification**
```
Commands:
/interface ethernet switch print: Port VLAN info
/interface ethernet switch print detail: Interface details
/interface vlan print: VLAN and port assignments
```

### Step 3: VLAN Testing
**Test VLAN connectivity and isolation:**

#### **Connectivity Testing**
```
Within VLAN:
- Connect devices to same VLAN
- Test ping between devices
- Verify broadcast communication
- Check ARP table

Between VLANs:
- Attempt ping between VLANs
- Verify traffic is blocked
- Check routing table
- Monitor traffic flow
```

---

## Part 3: VLAN Trunking Configuration

### Step 1: Trunk Port Configuration
**Configure trunk ports between switches:**

#### **Basic Trunk Configuration**
```
Commands:
/interface ethernet switch set [PORT] vlan-mode=trunk
/interface ethernet switch set [PORT] vlan-trunk=[VLAN_LIST]
/interface ethernet switch set [PORT] comment=[DESCRIPTION]

Example:
/interface ethernet switch set 24 vlan-mode=trunk
/interface ethernet switch set 24 vlan-trunk=10,20,30,40
/interface ethernet switch set 24 comment=TRUNK-TO-CORE
```

#### **Trunk Configuration Options**
```
Allowed VLANs:
- vlan-trunk=all: All VLANs
- vlan-trunk=10,20,30: Specific VLANs
- vlan-trunk=10-30: VLAN range
- vlan-trunk=10,20,30,40: Multiple VLANs

Native VLAN:
- vlan-trunk-native=99: Set native VLAN
- vlan-trunk-native-tag=yes: Tag native VLAN
```

### Step 2: Trunk Verification
**Verify trunk port configuration:**

#### **Trunk Status Commands**
```
Commands:
/interface ethernet switch print: Trunk port information
/interface ethernet switch print detail: Port details
/interface vlan print: VLAN distribution across trunks
```

#### **Trunk Troubleshooting**
```
Common Issues:
- Trunk negotiation failures
- VLAN mismatch
- Native VLAN mismatch
- Allowed VLAN restrictions
- Duplex/speed mismatches
```

### Step 3: Multi-Switch VLAN Configuration
**Configure VLANs across multiple switches:**

#### **VLAN Database Synchronization**
```
Manual Configuration:
- Configure VLANs on each switch
- More control and security
- Requires careful documentation
- No automatic synchronization

RouterOS Approach:
- Use /interface vlan add on each device
- Export/import configurations
- Use scripts for consistency
- Monitor for configuration drift
```

---

## Part 4: Inter-VLAN Routing

### Step 1: Router-on-a-Stick Configuration
**Configure router for inter-VLAN routing:**

#### **Router Interface Configuration**
```
Commands:
/interface vlan add name=[VLAN_NAME] vlan-id=[VLAN_ID]
/ip address add address=[IP_ADDRESS]/[SUBNET] interface=[VLAN_NAME]

Example:
/interface vlan add name=SALES vlan-id=10
/ip address add address=192.168.10.1/24 interface=SALES

/interface vlan add name=ENGINEERING vlan-id=20
/ip address add address=192.168.20.1/24 interface=ENGINEERING
```

#### **Switch Trunk Configuration**
```
Commands:
/interface ethernet switch set [PORT] vlan-mode=trunk
/interface ethernet switch set [PORT] vlan-trunk=[VLAN_LIST]

Example:
/interface ethernet switch set 24 vlan-mode=trunk
/interface ethernet switch set 24 vlan-trunk=10,20,30,40
```

### Step 2: Layer 3 Switch Configuration
**Configure Layer 3 switch for inter-VLAN routing:**

#### **SVI (Switch Virtual Interface) Configuration**
```
Commands:
/interface vlan add name=[VLAN_NAME] vlan-id=[VLAN_ID]
/ip address add address=[IP_ADDRESS]/[SUBNET] interface=[VLAN_NAME]

Example:
/interface vlan add name=SALES vlan-id=10
/ip address add address=192.168.10.1/24 interface=SALES

/interface vlan add name=ENGINEERING vlan-id=20
/ip address add address=192.168.20.1/24 interface=ENGINEERING
```

#### **Routing Configuration**
```
Commands:
/ip route add dst-address=0.0.0.0/0 gateway=[GATEWAY]: Default route
/ip route print: Display routing table
/ip address print: Interface status
```

### Step 3: Inter-VLAN Connectivity Testing
**Test communication between VLANs:**

#### **Connectivity Verification**
```
Commands:
/ping [IP_ADDRESS]: Test connectivity
/tool traceroute [IP_ADDRESS]: Path analysis
/ip arp print: ARP table verification
/ip route print: Routing table check
```

---

## Part 5: VLAN Security Configuration

### Step 1: VLAN Access Control
**Implement VLAN security measures:**

#### **Port Security with VLANs**
```
Commands:
/interface ethernet switch set [PORT] port-security=yes
/interface ethernet switch set [PORT] port-security-max-addresses=[NUMBER]
/interface ethernet switch set [PORT] port-security-mode=[MODE]
/interface ethernet switch set [PORT] vlan-mode=access
/interface ethernet switch set [PORT] vlan-id=[VLAN_ID]

Example:
/interface ethernet switch set 1 port-security=yes
/interface ethernet switch set 1 port-security-max-addresses=1
/interface ethernet switch set 1 port-security-mode=shutdown
/interface ethernet switch set 1 vlan-mode=access
/interface ethernet switch set 1 vlan-id=10
```

#### **VLAN ACLs (Access Control Lists)**
```
Commands:
/ip firewall filter add chain=forward src-address=[SOURCE] dst-address=[DESTINATION] action=[ACTION]

Example:
/ip firewall filter add chain=forward src-address=192.168.10.0/24 dst-address=192.168.20.0/24 action=accept
/ip firewall filter add chain=forward src-address=192.168.10.0/24 action=drop
```

### Step 2: Private VLANs
**Configure private VLANs for additional security:**

#### **Private VLAN Configuration**
```
RouterOS Approach:
- Use firewall rules for isolation
- Implement VLAN segmentation
- Use bridge filtering
- Monitor traffic patterns
```

### Step 3: VLAN Hopping Prevention
**Prevent VLAN hopping attacks:**

#### **Security Measures**
```
Native VLAN:
- Change from default VLAN 1
- Use dedicated native VLAN
- Tag native VLAN traffic

Trunk Security:
- Explicitly configure allowed VLANs
- Monitor trunk ports
- Use VLAN pruning
```

---

## Part 6: VLAN Monitoring and Troubleshooting

### Step 1: VLAN Monitoring
**Monitor VLAN performance and status:**

#### **VLAN Statistics**
```
Commands:
/interface vlan print: VLAN status and ports
/interface vlan monitor [NUMBER]: SVI statistics
/interface ethernet switch host print: MAC addresses
/interface ethernet switch print: STP information
```

#### **Traffic Analysis**
```
Tools:
- Wireshark: Packet capture and analysis
- Interface monitoring: Traffic statistics
- SNMP monitoring: Network management
- Logging: Event logging
```

### Step 2: VLAN Troubleshooting
**Troubleshoot common VLAN issues:**

#### **Common VLAN Problems**
```
Connectivity Issues:
- Incorrect VLAN assignment
- Trunk configuration errors
- Routing problems
- Security restrictions

Performance Issues:
- Broadcast storms
- VLAN spanning tree issues
- Bandwidth limitations
- Configuration conflicts
```

#### **Troubleshooting Commands**
```
Commands:
/interface vlan print: Verify VLAN configuration
/interface ethernet switch print: Check trunk status
/interface ethernet switch host print: MAC address learning
/ip route print: Routing table
/ping [ADDRESS]: Connectivity testing
```

### Step 3: VLAN Documentation
**Document VLAN configuration:**

#### **Documentation Requirements**
```
VLAN Information:
- VLAN ID and name
- IP subnet and gateway
- Purpose and scope
- Security requirements

Port Assignments:
- Interface to VLAN mapping
- Device connections
- Trunk configurations
- Access restrictions
```

---

## 📊 Lab Results Template

Fill out this template with your findings:

```
=== VLAN CONFIGURATION LAB ===

Network Design: ________
Date: ________
Switch Model: ________

Part 1: VLAN Design
- VLANs Created: ________
- VLAN Numbering Scheme: ________
- IP Subnet Plan: ________
- Security Requirements: ________

Part 2: Basic VLAN Configuration
- VLANs Configured: ________
- Access Ports: ________
- Port Assignments: ________
- Connectivity Test Results: ________

Part 3: Trunk Configuration
- Trunk Ports: ________
- Allowed VLANs: ________
- Native VLAN: ________
- Trunk Status: ________

Part 4: Inter-VLAN Routing
- Routing Method: ________
- Gateway Addresses: ________
- Routing Table: ________
- Inter-VLAN Test Results: ________

Part 5: Security Configuration
- Port Security: ________
- Access Control Lists: ________
- Private VLANs: ________
- Security Test Results: ________

Part 6: Monitoring and Troubleshooting
- Monitoring Tools: ________
- Performance Metrics: ________
- Issues Encountered: ________
- Resolution Steps: ________
```

---

## 🔍 Analysis Questions

1. **VLAN Design:** How did you design your VLAN structure to meet network requirements?

2. **Security Implementation:** What security measures did you implement to protect VLANs?

3. **Inter-VLAN Routing:** How did you configure routing between VLANs and why?

4. **Troubleshooting:** What common VLAN issues did you encounter and how did you resolve them?

5. **Scalability:** How would you modify your VLAN design to accommodate network growth?

---

## 🎓 Learning Outcomes

After completing this lab, you should understand:
- VLAN design principles and best practices
- VLAN configuration and management using RouterOS
- Trunk port configuration and verification
- Inter-VLAN routing implementation
- VLAN security features and configuration
- VLAN monitoring and troubleshooting techniques

---

## 🛠️ Recommended Tools

### **Configuration Tools:**
- **WinBox:** MikroTik GUI management tool
- **RouterOS CLI:** Command line interface
- **Configuration Templates:** Standard configurations
- **Documentation Tools:** Network diagrams and documentation

### **Testing Tools:**
- **ping/traceroute:** Connectivity testing
- **Wireshark:** Packet analysis
- **Network Scanners:** Device discovery
- **Performance Monitors:** Traffic analysis

### **Monitoring Tools:**
- **SNMP:** Network monitoring
- **Logging:** Event logging
- **Network Analyzers:** Traffic analysis
- **Management Platforms:** Centralized monitoring

---

## ⚠️ Important Notes

### **Best Practices:**
- **Plan VLAN design** before implementation
- **Document all configurations** thoroughly
- **Test connectivity** after each change
- **Implement security** from the beginning
- **Monitor performance** continuously

### **Security Considerations:**
- **VLAN hopping** prevention measures
- **Access control** implementation
- **Traffic monitoring** and analysis
- **Regular security** audits
- **Incident response** planning

---

**Next Session:** [Session 04: IP Addressing and Subnetting](../04-ip-addressing/) 