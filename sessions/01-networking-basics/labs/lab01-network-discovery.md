# Lab 01: Network Discovery

## 🎯 Objective
Learn to identify and explore your local network using built-in operating system tools.

## 🛠️ Prerequisites
- Computer with Windows, macOS, or Linux
- Network connection (wired or wireless)
- Basic command line knowledge

## 📋 Lab Steps

### Step 1: Identify Your Network Interface
Discover your network adapters and their configuration.

#### Windows:
```cmd
ipconfig /all
```

#### macOS/Linux:
```bash
ifconfig
# or
ip addr show
```

**Questions:**
1. How many network interfaces do you have?
2. What is your IP address?
3. What is your subnet mask?
4. What is your default gateway?

### Step 2: Discover Network Neighbors
Find other devices on your local network.

#### Windows:
```cmd
arp -a
```

#### macOS/Linux:
```bash
arp -a
# or
ip neighbor show
```

**Questions:**
1. How many devices are visible in your ARP table?
2. Can you identify what types of devices they might be?

### Step 3: Test Network Connectivity
Test connectivity to various network destinations.

#### Ping Local Gateway:
```bash
ping [gateway-ip]
# Example: ping 192.168.1.1
```

#### Ping External Host:
```bash
ping google.com
ping 8.8.8.8
```

**Questions:**
1. What is the response time to your gateway?
2. What is the response time to Google?
3. What does this tell you about your network path?

### Step 4: Trace Network Path
Discover the path packets take to reach a destination.

#### Windows:
```cmd
tracert google.com
```

#### macOS/Linux:
```bash
traceroute google.com
```

**Questions:**
1. How many hops to reach Google?
2. Can you identify your ISP's routers?
3. Where do you see the highest latency?

### Step 5: Network Statistics
View network usage and statistics.

#### Windows:
```cmd
netstat -e
netstat -an
```

#### macOS/Linux:
```bash
netstat -i
netstat -an
```

**Questions:**
1. How much data has been transmitted/received?
2. What network connections are currently active?
3. Which ports are listening on your system?

## 📊 Lab Results Template

Fill out this template with your findings:

```
=== NETWORK DISCOVERY LAB RESULTS ===

Network Interface Information:
- Interface Name: ________________
- IP Address: ___________________
- Subnet Mask: __________________
- Default Gateway: ______________
- DNS Servers: __________________

Network Neighbors:
- Total devices found: __________
- Gateway MAC address: __________
- Other device types identified: _____________

Connectivity Tests:
- Gateway ping time: ____________
- Google.com ping time: _________
- Packet loss percentage: _______

Network Path:
- Hops to Google: ______________
- ISP identified: ______________
- Highest latency hop: __________

Network Statistics:
- Bytes sent: __________________
- Bytes received: ______________
- Active connections: __________
```

## 🔍 Analysis Questions

1. **Network Type:** Based on your IP address, what type of network are you on? (Home, office, public Wi-Fi?)

2. **Network Size:** Estimate how many devices could be on your network based on the subnet mask.

3. **Performance:** Is your network performing well? What evidence supports your conclusion?

4. **Security:** What security concerns might exist based on what you discovered?

## 🎓 Learning Outcomes

After completing this lab, you should understand:
- How to identify your network configuration
- How to discover other devices on your network
- How to test network connectivity and performance
- How to trace network paths
- Basic network troubleshooting techniques

---

**Next Lab:** [Lab 02: Identifying Network Components](./lab02-identify-components.md)