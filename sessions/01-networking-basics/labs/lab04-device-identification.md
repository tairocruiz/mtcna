# Lab 04: Network Device Identification

## 🎯 Objective
Learn to identify and analyze network devices in real-world environments using various tools and techniques. Develop skills to recognize device types, capabilities, and network roles through systematic discovery and documentation.

## 🛠️ Prerequisites
- Access to a network environment (home, office, or lab)
- Computer with network connectivity
- Basic command line knowledge
- Network scanning tools (optional)
- Documentation tools

## 📋 Lab Overview
This lab will help you:
1. Use network discovery tools to identify devices
2. Analyze device characteristics and capabilities
3. Document network device inventory
4. Understand device roles and relationships
5. Practice network documentation skills

---

## Part 1: Network Discovery Tools

### Step 1: Command Line Tools
**Use built-in operating system tools for device discovery:**

#### **Windows Commands**
```cmd
# View network configuration
ipconfig /all

# View ARP table (MAC address mapping)
arp -a

# Test connectivity to devices
ping [IP_ADDRESS]

# Trace route to destination
tracert [IP_ADDRESS]

# View network connections
netstat -an

# View active connections
netstat -b
```

#### **Linux/macOS Commands**
```bash
# View network configuration
ifconfig -a
# or
ip addr show

# View ARP table
arp -a

# Test connectivity
ping [IP_ADDRESS]

# Trace route
traceroute [IP_ADDRESS]

# View network connections
netstat -an

# View active connections
netstat -tuln
```

### Step 2: Network Scanning Tools
**Use specialized tools for comprehensive device discovery:**

#### **Free Network Scanners**
- **Advanced IP Scanner** (Windows)
- **Angry IP Scanner** (Cross-platform)
- **Nmap** (Command line, all platforms)
- **Fing** (Mobile app)

#### **Nmap Examples**
```bash
# Basic network scan
nmap -sn 192.168.1.0/24

# Port scan for common services
nmap -sS -p 22,23,80,443,3389 192.168.1.0/24

# Service version detection
nmap -sV 192.168.1.0/24

# OS detection
nmap -O 192.168.1.0/24
```

---

## Part 2: Device Identification Process

### Step 1: Network Range Discovery
**Identify the network range to scan:**

#### **Determine Network Range**
```
Your IP Address: ________
Subnet Mask: ________
Network Address: ________
Broadcast Address: ________
Scan Range: ________ to ________
```

#### **Common Private Network Ranges**
- **192.168.0.0/24** - 192.168.0.1 to 192.168.0.254
- **192.168.1.0/24** - 192.168.1.1 to 192.168.1.254
- **10.0.0.0/8** - 10.0.0.1 to 10.255.255.254
- **172.16.0.0/12** - 172.16.0.1 to 172.31.255.254

### Step 2: Active Device Discovery
**Scan the network for active devices:**

#### **Ping Sweep**
```bash
# Windows ping sweep
for /L %i in (1,1,254) do ping -n 1 -w 100 192.168.1.%i | find "Reply"

# Linux/macOS ping sweep
for i in {1..254}; do ping -c 1 -W 1 192.168.1.$i | grep "64 bytes"; done
```

#### **Document Active Devices**
```
=== ACTIVE DEVICES DISCOVERY ===

Device 1:
- IP Address: ________
- MAC Address: ________
- Response Time: ________ ms
- Status: Active/Inactive

Device 2:
- IP Address: ________
- MAC Address: ________
- Response Time: ________ ms
- Status: Active/Inactive

Total Active Devices: ________
```

### Step 3: Device Type Identification
**Analyze discovered devices to determine their type:**

#### **MAC Address Analysis**
```
MAC Address Format: XX:XX:XX:XX:XX:XX
OUI (First 6 characters): ________
Manufacturer: ________
Device Type: ________
```

#### **Common OUI Examples**
- **00:50:56** - VMware (Virtual machines)
- **00:0C:29** - VMware (Virtual machines)
- **00:1A:11** - Google (Chromecast, etc.)
- **B8:27:EB** - Raspberry Pi Foundation
- **DC:A6:32** - Raspberry Pi Foundation
- **00:1B:21** - Cisco Systems
- **00:1C:58** - Cisco Systems

#### **Port Analysis**
```
Common Service Ports:
- Port 22: SSH (Linux/Unix systems)
- Port 23: Telnet (Network devices)
- Port 80: HTTP (Web servers, printers)
- Port 443: HTTPS (Secure web services)
- Port 3389: RDP (Windows systems)
- Port 8080: HTTP Alternative (Web services)
```

---

## Part 3: Device Capability Analysis

### Step 1: Service Discovery
**Identify services running on discovered devices:**

#### **Web Interface Detection**
```
Device IP: ________
Web Interface: http://[IP]/ or https://[IP]/
Accessible: Yes/No
Device Type: Router/Switch/Printer/Camera/Other
```

#### **SSH/Telnet Access**
```
Device IP: ________
SSH Access: Yes/No (Port 22)
Telnet Access: Yes/No (Port 23)
Device Type: Network Device/Server/Other
```

#### **Common Device Web Interfaces**
- **192.168.1.1** - Common router default
- **192.168.0.1** - Common router default
- **10.0.0.1** - Common router default
- **172.16.0.1** - Common router default

### Step 2: Device Fingerprinting
**Use various techniques to identify device types:**

#### **HTTP Headers Analysis**
```
Server Header: ________
Device Type: ________
Model: ________
Firmware: ________
```

#### **SNMP Discovery**
```bash
# SNMP community string discovery
snmpwalk -v1 -c public [IP_ADDRESS] system

# System description
snmpwalk -v1 -c public [IP_ADDRESS] .1.3.6.1.2.1.1.1.0
```

#### **Device Response Analysis**
```
Ping Response Pattern: ________
TTL Values: ________
Port Response: ________
Device Characteristics: ________
```

---

## Part 4: Network Device Inventory

### Step 1: Device Classification
**Categorize discovered devices:**

#### **End Devices**
```
Computers/Workstations:
- Count: ________
- IP Range: ________
- Operating Systems: ________

Mobile Devices:
- Count: ________
- IP Range: ________
- Device Types: ________

Network Printers:
- Count: ________
- IP Addresses: ________
- Models: ________

IP Phones:
- Count: ________
- IP Addresses: ________
- Models: ________

Other IoT Devices:
- Count: ________
- IP Addresses: ________
- Device Types: ________
```

#### **Infrastructure Devices**
```
Routers/Gateways:
- Count: ________
- IP Addresses: ________
- Models: ________

Switches:
- Count: ________
- IP Addresses: ________
- Models: ________

Access Points:
- Count: ________
- IP Addresses: ________
- Models: ________

Firewalls:
- Count: ________
- IP Addresses: ________
- Models: ________
```

### Step 2: Network Topology Mapping
**Create a visual representation of discovered devices:**

#### **Physical Layout**
```
Draw or describe the physical network layout:
- Device locations
- Connection types (wired/wireless)
- Network segments
- Equipment rooms
```

#### **Logical Topology**
```
Create a network diagram showing:
- Device relationships
- IP addressing scheme
- Network segments
- VLANs (if applicable)
```

---

## Part 5: Advanced Device Analysis

### Step 1: Network Traffic Analysis
**Use packet capture tools to analyze device behavior:**

#### **Wireshark Analysis**
```
Capture Filter: host [IP_ADDRESS]
Analysis Focus:
- Protocol types
- Traffic patterns
- Communication partners
- Service identification
```

#### **Traffic Patterns**
```
Device IP: ________
Protocols Used: ________
Peak Traffic Times: ________
Communication Partners: ________
Bandwidth Usage: ________
```

### Step 2: Security Assessment
**Evaluate device security posture:**

#### **Open Ports Analysis**
```
Device IP: ________
Open Ports: ________
Services Running: ________
Security Risk Level: Low/Medium/High
Recommendations: ________
```

#### **Default Credentials Check**
```
Device Type: ________
Default Username: ________
Default Password: ________
Credentials Changed: Yes/No
Security Status: ________
```

---

## Part 6: Documentation and Reporting

### Step 1: Device Inventory Report
**Create a comprehensive device inventory:**

```
=== NETWORK DEVICE INVENTORY REPORT ===

Scan Date: ________
Scan Range: ________
Total Devices Found: ________
Active Devices: ________
Inactive Devices: ________

Device Details:
1. Device Name: ________
   IP Address: ________
   MAC Address: ________
   Device Type: ________
   Manufacturer: ________
   Model: ________
   Services: ________
   Security Status: ________

2. Device Name: ________
   IP Address: ________
   MAC Address: ________
   Device Type: ________
   Manufacturer: ________
   Model: ________
   Services: ________
   Security Status: ________

[Continue for all discovered devices]
```

### Step 2: Network Map Creation
**Create visual network documentation:**

#### **Network Diagram Elements**
- **Device Icons:** Use standard network icons
- **IP Addresses:** Label each device with IP
- **Connection Lines:** Show device relationships
- **Network Segments:** Group related devices
- **Legend:** Explain symbols and colors

#### **Documentation Standards**
- **Consistent Naming:** Use clear device names
- **IP Addressing:** Document IP scheme
- **VLAN Information:** Include VLAN assignments
- **Physical Location:** Note device placement
- **Update Procedures:** Plan for regular updates

---

## 📊 Lab Results Template

Fill out this template with your findings:

```
=== NETWORK DEVICE IDENTIFICATION LAB ===

Environment: ________ (Home/Office/Lab)
Scan Date: ________
Scan Duration: ________

Part 1: Network Discovery
- Network Range: ________
- Total IPs Scanned: ________
- Active Devices Found: ________
- Discovery Tools Used: ________

Part 2: Device Classification
- End Devices: ________
- Infrastructure Devices: ________
- Unknown Devices: ________
- Device Types Identified: ________

Part 3: Service Analysis
- Web Interfaces: ________
- SSH/Telnet Services: ________
- Common Services: ________
- Security Concerns: ________

Part 4: Network Topology
- Network Segments: ________
- Device Relationships: ________
- Connection Types: ________
- Architecture Pattern: ________

Part 5: Security Assessment
- Open Ports: ________
- Default Credentials: ________
- Security Recommendations: ________
- Risk Level: ________
```

---

## 🔍 Analysis Questions

1. **Device Discovery:** What tools were most effective for discovering network devices?

2. **Device Identification:** How did you determine the type and manufacturer of each device?

3. **Network Architecture:** What patterns did you observe in the network topology?

4. **Security Assessment:** What security vulnerabilities did you identify?

5. **Documentation:** How would you maintain this device inventory over time?

---

## 🎓 Learning Outcomes

After completing this lab, you should understand:
- Network discovery techniques and tools
- Device identification and classification methods
- Network topology mapping and documentation
- Security assessment procedures
- Inventory management best practices

---

## 🛠️ Recommended Tools

### **Discovery Tools:**
- **Nmap:** Comprehensive network scanning
- **Advanced IP Scanner:** User-friendly Windows scanner
- **Angry IP Scanner:** Cross-platform network scanner
- **Fing:** Mobile network discovery app

### **Analysis Tools:**
- **Wireshark:** Network traffic analysis
- **Nmap:** Service and OS detection
- **SNMP Tools:** Device information gathering
- **Web Browsers:** Interface access testing

### **Documentation Tools:**
- **Draw.io:** Network diagram creation
- **Visio:** Professional network documentation
- **Lucidchart:** Online diagramming
- **Spreadsheets:** Inventory management

---

## ⚠️ Important Notes

### **Legal and Ethical Considerations:**
- **Only scan networks you own or have permission to scan**
- **Respect network usage policies**
- **Do not attempt unauthorized access to devices**
- **Document all activities for learning purposes only**

### **Best Practices:**
- **Use non-intrusive scanning methods**
- **Respect device response times**
- **Document findings accurately**
- **Maintain security awareness**

---
