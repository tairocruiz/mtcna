# Lab 06: Protocol Analysis with Wireshark

## 🎯 Objective
Learn to use Wireshark for advanced protocol analysis and network troubleshooting. Develop skills to capture, analyze, and interpret network traffic to understand protocol behavior and identify network issues.

## 🛠️ Prerequisites
- Computer with Windows, macOS, or Linux
- Wireshark installed (free download from wireshark.org)
- Network connection
- Basic understanding of OSI model and TCP/IP protocols
- Administrator/root privileges for packet capture

## 📋 Lab Overview
This lab will help you:
1. Master Wireshark interface and capture techniques
2. Analyze different protocol types and their characteristics
3. Use filters and display options for traffic analysis
4. Identify network problems through packet analysis
5. Create custom capture and display filters

---

## Part 1: Wireshark Interface Mastery

### Step 1: Wireshark Installation and Setup
**Install and configure Wireshark for optimal analysis:**

#### **Installation**
1. **Download Wireshark** from https://www.wireshark.org/
2. **Install with default settings** (includes WinPcap/Npcap)
3. **Launch as administrator** (Windows) or with sudo (Linux/macOS)
4. **Verify installation** by checking version and interface list

#### **Initial Configuration**
```
File → Preferences → Capture
- Default Interface: Select your active network interface
- Capture in promiscuous mode: Enabled
- Update list of packets in real time: Enabled
- Automatic scrolling in live capture: Enabled
```

### Step 2: Wireshark Interface Components
**Understand the main interface elements:**

#### **Main Window Layout**
```
┌─────────────────────────────────────────────────────────┐
│ Menu Bar: File, Edit, View, Go, Capture, Analyze, etc.  │
├─────────────────────────────────────────────────────────┤
│ Toolbar: Quick access to common functions               │
├─────────────────────────────────────────────────────────┤
│ Packet List: Shows captured packets with key info       │
├─────────────────────────────────────────────────────────┤
│ Packet Details: Hierarchical view of packet contents    │
├─────────────────────────────────────────────────────────┤
│ Packet Bytes: Hexadecimal and ASCII representation      │
└─────────────────────────────────────────────────────────┘
```

#### **Packet List Columns**
- **No.:** Packet number in capture
- **Time:** Timestamp of packet
- **Source:** Source IP address
- **Destination:** Destination IP address
- **Protocol:** Protocol type
- **Length:** Packet size in bytes
- **Info:** Summary information

### Step 3: Basic Capture Operations
**Learn essential capture functions:**

#### **Starting a Capture**
```
1. Click "Capture" → "Start capturing packets"
2. Select interface from list
3. Click "Start" to begin capture
4. Observe packets appearing in real-time
5. Click "Stop" when finished
```

#### **Saving and Loading Captures**
```
Save Capture:
- File → Save As
- Choose location and filename
- Select format (.pcapng recommended)

Load Capture:
- File → Open
- Navigate to saved file
- Select and open
```

---

## Part 2: Protocol Analysis Techniques

### Step 1: HTTP/HTTPS Analysis
**Analyze web traffic patterns:**

#### **HTTP Traffic Capture**
```
1. Start new capture
2. Open web browser
3. Navigate to http://httpbin.org/get
4. Stop capture after page loads
5. Filter: http
```

#### **HTTP Packet Analysis**
```
Key Fields to Examine:
- HTTP Method: GET, POST, PUT, DELETE
- Status Code: 200, 404, 500, etc.
- Headers: Host, User-Agent, Content-Type
- Request/Response Body
```

#### **HTTPS Traffic Analysis**
```
1. Navigate to https://www.google.com
2. Filter: ssl or tls
3. Analyze TLS handshake:
   - Client Hello
   - Server Hello
   - Certificate Exchange
   - Key Exchange
```

### Step 2: TCP Connection Analysis
**Examine TCP connection establishment and teardown:**

#### **TCP Three-Way Handshake**
```
Filter: tcp.flags.syn == 1 or tcp.flags.ack == 1

Look for:
1. SYN packet (SYN=1, ACK=0)
2. SYN-ACK packet (SYN=1, ACK=1)
3. ACK packet (SYN=0, ACK=1)
```

#### **TCP Connection Teardown**
```
Filter: tcp.flags.fin == 1 or tcp.flags.rst == 1

Look for:
1. FIN packet from one side
2. ACK packet in response
3. FIN packet from other side
4. Final ACK packet
```

### Step 3: DNS Analysis
**Analyze Domain Name System queries:**

#### **DNS Query Capture**
```
1. Clear DNS cache (ipconfig /flushdns on Windows)
2. Start capture
3. Ping a new domain (ping www.mboratech.co.tz)
4. Stop capture
5. Filter: dns
```

#### **DNS Packet Structure**
```
Examine:
- Query Type: A, AAAA, MX, CNAME
- Query Name: Domain being resolved
- Response: IP address or other data
- TTL: Time to live value
```

### Step 4: DHCP Analysis
**Analyze Dynamic Host Configuration Protocol:**

#### **DHCP Process Capture**
```
1. Release IP address (ipconfig /release on Windows)
2. Start capture
3. Renew IP address (ipconfig /renew on Windows)
4. Stop capture
5. Filter: dhcp
```

#### **DHCP Message Types**
```
Look for:
- DHCP Discover (client seeking server)
- DHCP Offer (server offering IP)
- DHCP Request (client requesting IP)
- DHCP ACK (server confirming IP)
```

---

## Part 3: Advanced Filtering Techniques

### Step 1: Display Filters
**Use filters to focus on specific traffic:**

#### **Basic Display Filters**
```
Protocol Filters:
- tcp - Show only TCP packets
- udp - Show only UDP packets
- http - Show only HTTP packets
- dns - Show only DNS packets
- arp - Show only ARP packets

IP Address Filters:
- ip.addr == 192.168.1.1 - Packets to/from specific IP
- ip.src == 192.168.1.1 - Packets from specific IP
- ip.dst == 192.168.1.1 - Packets to specific IP
```

#### **Advanced Display Filters**
```
Port Filters:
- tcp.port == 80 - HTTP traffic
- tcp.port == 443 - HTTPS traffic
- udp.port == 53 - DNS traffic

Content Filters:
- http.request.method == "GET" - HTTP GET requests
- http.response.code == 200 - HTTP 200 responses
- dns.qry.name contains "google" - DNS queries for Google
```

### Step 2: Capture Filters
**Filter traffic during capture to reduce file size:**

#### **Capture Filter Syntax**
```
Protocol Filters:
- tcp - Capture only TCP packets
- udp - Capture only UDP packets
- port 80 - Capture traffic on port 80
- port 443 - Capture traffic on port 443

Host Filters:
- host 192.168.1.1 - Capture traffic to/from specific host
- src host 192.168.1.1 - Capture traffic from specific host
- dst host 192.168.1.1 - Capture traffic to specific host
```

#### **Complex Capture Filters**
```
Multiple Conditions:
- tcp and port 80 - TCP traffic on port 80
- udp and port 53 - UDP traffic on port 53
- host 192.168.1.1 and not port 80 - Traffic to/from host, excluding port 80
```

### Step 3: Custom Filters
**Create filters for specific analysis needs:**

#### **Filter Examples**
```
HTTP Analysis:
- http.request.method == "POST" - HTTP POST requests
- http.response.code >= 400 - HTTP error responses
- http.user_agent contains "Chrome" - Chrome browser traffic

TCP Analysis:
- tcp.flags.syn == 1 - TCP SYN packets
- tcp.window_size < 1000 - Small TCP window sizes
- tcp.analysis.retransmission - TCP retransmissions

Error Analysis:
- tcp.analysis.flags - TCP analysis flags
- tcp.analysis.duplicate_ack - Duplicate ACKs
- tcp.analysis.fast_retransmission - Fast retransmissions
```

---

## Part 4: Network Troubleshooting

### Step 1: Connectivity Issues
**Use Wireshark to diagnose connection problems:**

#### **Ping Analysis**
```
1. Start capture
2. Ping a remote host (ping 8.8.8.8)
3. Stop capture
4. Filter: icmp

Look for:
- Echo Request packets (Type 8)
- Echo Reply packets (Type 0)
- Time Exceeded packets (Type 11)
- Destination Unreachable packets (Type 3)
```

#### **TCP Connection Issues**
```
Filter: tcp.flags.syn == 1

Analyze:
- SYN packets sent but no SYN-ACK received
- RST packets indicating connection refused
- Timeout patterns
- Port scanning attempts
```

### Step 2: Performance Analysis
**Identify performance bottlenecks:**

#### **Bandwidth Analysis**
```
Statistics → Protocol Hierarchy
- Shows traffic distribution by protocol
- Identifies bandwidth-heavy applications
- Reveals unexpected traffic patterns
```

#### **Latency Analysis**
```
Filter: tcp

Examine:
- Round-trip time (RTT) values
- TCP window size changes
- Retransmission patterns
- Connection establishment delays
```

### Step 3: Security Analysis
**Detect security threats and anomalies:**

#### **Port Scanning Detection**
```
Filter: tcp.flags.syn == 1

Look for:
- Multiple SYN packets to different ports
- Rapid succession of connection attempts
- Unusual port ranges
- Failed connection attempts
```

#### **Malicious Traffic Patterns**
```
Common Indicators:
- Large number of failed login attempts
- Unusual protocol usage
- Data exfiltration patterns
- Command and control traffic
- DDoS attack signatures
```

---

## Part 5: Advanced Analysis Features

### Step 1: Statistics and Graphs
**Use Wireshark's statistical analysis tools:**

#### **Protocol Hierarchy**
```
Statistics → Protocol Hierarchy
- Shows percentage breakdown by protocol
- Helps identify traffic patterns
- Useful for capacity planning
```

#### **Conversations**
```
Statistics → Conversations
- Shows communication between hosts
- Displays data transfer amounts
- Helps identify top talkers
```

#### **IO Graphs**
```
Statistics → IO Graphs
- Visual representation of traffic over time
- Helps identify traffic spikes
- Useful for performance analysis
```

### Step 2: Expert Information
**Use Wireshark's expert system:**

#### **Expert Information Panel**
```
Analyze → Expert Information
- Shows warnings and notes about packets
- Identifies potential problems
- Provides analysis suggestions
```

#### **Expert Information Types**
```
Chat: Normal conversation
Note: Informational messages
Warn: Potential problems
Error: Definite problems
```

### Step 3: Custom Columns
**Create custom columns for specific analysis:**

#### **Adding Custom Columns**
```
1. Right-click column header
2. Select "Column Preferences"
3. Click "Add" to create new column
4. Choose field type and title
5. Apply changes
```

#### **Useful Custom Columns**
```
- tcp.window_size - TCP window size
- http.response.code - HTTP response codes
- dns.qry.name - DNS query names
- tcp.analysis.ack_rtt - TCP RTT values
```

---

## Part 6: Reporting and Documentation

### Step 1: Exporting Data
**Export analysis results for reporting:**

#### **Export Options**
```
File → Export
- Packet Dissections → As Plain Text
- Packet Dissections → As CSV
- Packet Dissections → As XML
- Specific Packets → As Plain Text
```

#### **Report Generation**
```
Include in Reports:
- Capture summary statistics
- Protocol breakdown
- Key findings and anomalies
- Screenshots of important packets
- Filter expressions used
```

### Step 2: Creating Analysis Reports
**Document your findings professionally:**

#### **Report Structure**
```
1. Executive Summary
   - Key findings
   - Issues identified
   - Recommendations

2. Methodology
   - Capture setup
   - Filters used
   - Analysis approach

3. Detailed Analysis
   - Protocol breakdown
   - Traffic patterns
   - Performance metrics

4. Conclusions
   - Summary of findings
   - Action items
   - Follow-up recommendations
```

---

## 📊 Lab Results Template

Fill out this template with your findings:

```
=== WIRESHARK PROTOCOL ANALYSIS LAB ===

Environment: ________ (Home/Office/Lab)
Capture Duration: ________
Total Packets Captured: ________

Part 1: HTTP/HTTPS Analysis
- HTTP Requests: ________
- HTTPS Connections: ________
- TLS Handshakes: ________
- Common User-Agents: ________

Part 2: TCP Analysis
- TCP Connections: ________
- Three-Way Handshakes: ________
- Connection Teardowns: ________
- Retransmissions: ________

Part 3: DNS Analysis
- DNS Queries: ________
- Query Types: ________
- Response Times: ________
- Failed Resolutions: ________

Part 4: Performance Analysis
- Average RTT: ________ ms
- Bandwidth Utilization: ________
- Protocol Distribution: ________
- Performance Issues: ________

Part 5: Security Analysis
- Suspicious Patterns: ________
- Port Scanning: ________
- Failed Connections: ________
- Security Recommendations: ________
```

---

## 🔍 Analysis Questions

1. **Protocol Behavior:** What patterns did you observe in different protocol types?

2. **Performance Issues:** How did you identify and analyze performance problems?

3. **Security Threats:** What security indicators did you look for in the traffic?

4. **Filtering Techniques:** Which filters were most useful for your analysis?

5. **Troubleshooting:** How would you use Wireshark to troubleshoot specific network issues?

---

## 🎓 Learning Outcomes

After completing this lab, you should understand:
- Wireshark interface and capture techniques
- Protocol analysis and interpretation
- Advanced filtering and display options
- Network troubleshooting methodologies
- Security analysis and threat detection

---

## 🛠️ Recommended Tools

### **Wireshark Extensions:**
- **Protocol Decoders:** Additional protocol support
- **Custom Dissectors:** Protocol-specific analysis
- **Statistics Plugins:** Enhanced statistical analysis
- **Export Tools:** Custom export formats

### **Complementary Tools:**
- **tcpdump:** Command-line packet capture
- **tshark:** Wireshark command-line interface
- **NetworkMiner:** Network forensic analysis
- **CapAnalysis:** Web-based pcap analysis

### **Analysis Tools:**
- **Excel/Google Sheets:** Data analysis and graphing
- **Python Scripts:** Custom analysis automation
- **Network Monitoring:** Real-time traffic analysis
- **SIEM Systems:** Security information and event management

---

## ⚠️ Important Notes

### **Legal and Ethical Considerations:**
- **Only capture traffic you own or have permission to capture**
- **Respect privacy and data protection regulations**
- **Do not capture sensitive information without authorization**
- **Follow organizational security policies**

### **Best Practices:**
- **Use capture filters** to reduce file size
- **Document your analysis** thoroughly
- **Keep captures secure** and confidential
- **Regularly update Wireshark** for latest features

---

**Next Lab:** [Lab 07: Network Performance Analysis](./lab07-performance-analysis.md) 