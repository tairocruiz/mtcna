# Lab 07: Network Performance Analysis

## 🎯 Objective
Learn to analyze and optimize network performance using various tools and techniques. Develop skills to measure, monitor, and improve network throughput, latency, and reliability through systematic performance analysis.

## 🛠️ Prerequisites
- Computer with Windows, macOS, or Linux
- Network connection
- Wireshark installed
- Basic command line knowledge
- Performance monitoring tools (optional)
- Administrator/root privileges for some tools

## 📋 Lab Overview
This lab will help you:
1. Measure network performance metrics
2. Identify performance bottlenecks
3. Analyze network capacity and utilization
4. Optimize network performance
5. Create performance baselines and reports

---

## Part 1: Performance Metrics Fundamentals

### Step 1: Understanding Key Performance Indicators
**Learn the essential network performance metrics:**

#### **Bandwidth Metrics**
```
Throughput: Actual data transfer rate achieved
- Measured in: bits per second (bps), bytes per second (B/s)
- Tools: Speed tests, file transfers, monitoring software
- Factors: Network capacity, protocol overhead, congestion

Bandwidth Utilization: Percentage of available bandwidth used
- Formula: (Used Bandwidth / Total Bandwidth) × 100
- Target: 70-80% for optimal performance
- Monitoring: Continuous measurement over time
```

#### **Latency Metrics**
```
Round-Trip Time (RTT): Time for packet to reach destination and return
- Measured in: milliseconds (ms)
- Tools: ping, traceroute, specialized latency tools
- Factors: Distance, network congestion, processing delays

Jitter: Variation in packet arrival times
- Measured in: milliseconds (ms)
- Impact: Affects real-time applications (VoIP, video)
- Calculation: Standard deviation of RTT values

Packet Loss: Percentage of packets that don't reach destination
- Formula: (Lost Packets / Total Packets) × 100
- Acceptable: < 1% for most applications
- Causes: Network congestion, hardware failures, errors
```

#### **Quality Metrics**
```
Error Rate: Percentage of packets with transmission errors
- Types: CRC errors, frame errors, alignment errors
- Monitoring: Switch/router statistics, protocol analyzers
- Impact: Retransmissions, reduced throughput

Connection Quality: Overall network reliability
- Factors: Uptime, stability, consistency
- Measurement: Continuous monitoring over time
- Reporting: Availability percentages, MTBF (Mean Time Between Failures)
```

### Step 2: Performance Measurement Tools
**Identify and use appropriate measurement tools:**

#### **Built-in Operating System Tools**
```
Windows:
- ping: Basic connectivity and RTT measurement
- tracert: Path analysis and hop-by-hop latency
- netstat: Connection statistics and port usage
- perfmon: Performance monitoring and logging

Linux/macOS:
- ping: Connectivity and RTT testing
- traceroute: Path analysis and latency measurement
- netstat: Network statistics and connections
- iperf: Bandwidth testing and measurement
- iftop: Real-time bandwidth monitoring
```

#### **Specialized Performance Tools**
```
Bandwidth Testing:
- Speedtest.net: Internet speed measurement
- iperf/iperf3: Network bandwidth testing
- NetCPS: Windows bandwidth testing
- nttcp: Network throughput testing

Latency Testing:
- ping: Basic RTT measurement
- hping3: Advanced ping with custom options
- mtr: Continuous traceroute with statistics
- smokeping: Continuous latency monitoring

Monitoring Tools:
- Wireshark: Detailed packet analysis
- Nagios: Network monitoring and alerting
- PRTG: Network monitoring and reporting
- SolarWinds: Enterprise network monitoring
```

---

## Part 2: Bandwidth Analysis

### Step 1: Internet Speed Testing
**Measure your internet connection performance:**

#### **Speedtest.net Analysis**
```
1. Visit speedtest.net
2. Run multiple tests at different times
3. Record results:
   - Download Speed: ________ Mbps
   - Upload Speed: ________ Mbps
   - Ping: ________ ms
   - Jitter: ________ ms
   - Packet Loss: ________ %

4. Compare with advertised speeds
5. Identify performance gaps
```

#### **Multiple Speed Test Tools**
```
Test with different services:
- Speedtest.net (Ookla)
- Fast.com (Netflix)
- Google Speed Test
- DSLReports Speed Test

Compare results:
- Consistency across services
- Time-of-day variations
- Peak vs off-peak performance
- Provider vs third-party results
```

### Step 2: Local Network Bandwidth Testing
**Measure internal network performance:**

#### **iperf Bandwidth Testing**
```
Server Setup (Linux/macOS):
iperf -s -p 5201

Client Testing:
# TCP Test
iperf -c [SERVER_IP] -p 5201 -t 30

# UDP Test
iperf -c [SERVER_IP] -p 5201 -u -b 100M -t 30

# Bidirectional Test
iperf -c [SERVER_IP] -p 5201 -d -t 30
```

#### **Windows Bandwidth Testing**
```
Using NetCPS:
# Server mode
netcps -s -p 5000

# Client mode
netcps -c [SERVER_IP] -p 5000 -t 30

Using nttcp:
# Server mode
nttcp -s -p 5000

# Client mode
nttcp -c [SERVER_IP] -p 5000 -t 30
```

### Step 3: Bandwidth Utilization Monitoring
**Monitor real-time bandwidth usage:**

#### **Real-time Monitoring Tools**
```
Linux/macOS:
- iftop: Real-time bandwidth monitoring
- nethogs: Process-based bandwidth usage
- bmon: Bandwidth monitor with graphs
- vnstat: Network traffic monitor

Windows:
- Resource Monitor: Built-in network monitoring
- NetWorx: Free bandwidth monitoring
- PRTG: Professional monitoring solution
- Wireshark: Detailed traffic analysis
```

#### **Bandwidth Utilization Analysis**
```
Monitor for:
- Peak usage times
- Bandwidth hogs (applications/users)
- Unusual traffic patterns
- Capacity planning data
- Performance bottlenecks
```

---

## Part 3: Latency and Jitter Analysis

### Step 1: Basic Latency Testing
**Measure network latency using ping:**

#### **Comprehensive Ping Analysis**
```
Extended Ping Test:
ping -n 100 [TARGET_IP]

Analyze results:
- Minimum RTT: ________ ms
- Maximum RTT: ________ ms
- Average RTT: ________ ms
- Standard Deviation: ________ ms
- Packet Loss: ________ %

Calculate jitter:
Jitter = Standard Deviation of RTT values
```

#### **Path Analysis with Traceroute**
```
Windows:
tracert [TARGET_IP]

Linux/macOS:
traceroute [TARGET_IP]

Analyze each hop:
- Hop number and IP address
- RTT for each hop
- Identify bottlenecks
- Geographic path analysis
```

### Step 2: Advanced Latency Testing
**Use specialized tools for detailed latency analysis:**

#### **Continuous Latency Monitoring**
```
Using mtr (Linux/macOS):
mtr [TARGET_IP] -r -c 100

Using hping3:
hping3 -c 100 -i u1000 [TARGET_IP]

Analysis:
- Continuous RTT measurement
- Jitter calculation
- Packet loss detection
- Path stability assessment
```

#### **Jitter Analysis**
```
Calculate jitter:
1. Collect RTT samples (minimum 100)
2. Calculate mean RTT
3. Calculate standard deviation
4. Jitter = Standard deviation

Jitter Categories:
- Excellent: < 5ms
- Good: 5-15ms
- Fair: 15-30ms
- Poor: > 30ms
```

### Step 3: Application-Specific Latency
**Test latency for specific applications:**

#### **Web Application Latency**
```
Tools:
- Browser Developer Tools (Network tab)
- curl with timing options
- wget with timing
- Custom scripts

Measure:
- DNS resolution time
- TCP connection time
- Time to first byte (TTFB)
- Total page load time
```

#### **Database Latency Testing**
```
Tools:
- Database client timing
- Custom scripts
- Monitoring tools

Measure:
- Connection establishment time
- Query execution time
- Response time
- Transaction latency
```

---

## Part 4: Packet Loss and Error Analysis

### Step 1: Packet Loss Detection
**Identify and measure packet loss:**

#### **Ping-based Packet Loss Testing**
```
Extended ping test:
ping -n 1000 [TARGET_IP]

Calculate packet loss:
Packet Loss % = (Lost Packets / Total Packets) × 100

Acceptable thresholds:
- Voice/Video: < 1%
- Data transfer: < 5%
- General use: < 10%
```

#### **UDP Packet Loss Testing**
```
Using iperf:
# Server
iperf -s -u -p 5201

# Client with packet loss measurement
iperf -c [SERVER_IP] -u -p 5201 -b 10M -t 60

Analysis:
- Jitter measurement
- Packet loss percentage
- Out-of-order packets
- Duplicate packets
```

### Step 2: Error Rate Analysis
**Monitor network errors and their causes:**

#### **Interface Error Monitoring**
```
Linux/macOS:
ifconfig [INTERFACE]
cat /proc/net/dev

Windows:
netstat -e
Performance Monitor

Monitor for:
- CRC errors
- Frame errors
- Alignment errors
- Collision errors (Ethernet)
- Buffer overruns
```

#### **Switch/Router Error Statistics**
```
Access device statistics:
- Interface error counters
- Buffer utilization
- Queue statistics
- Dropped packet counters
- Error rate calculations
```

### Step 3: Quality of Service (QoS) Analysis
**Analyze QoS implementation and effectiveness:**

#### **QoS Policy Verification**
```
Check QoS policies:
- Traffic classification
- Bandwidth allocation
- Priority queuing
- Traffic shaping
- Policing rules
```

#### **QoS Performance Testing**
```
Test different traffic types:
- Voice traffic (low latency, low loss)
- Video traffic (consistent bandwidth)
- Data traffic (reliability)
- Background traffic (best effort)

Measure impact:
- Latency for priority traffic
- Bandwidth allocation
- Packet loss by traffic type
- Overall network performance
```

---

## Part 5: Performance Optimization

### Step 1: Bottleneck Identification
**Identify and analyze performance bottlenecks:**

#### **Network Bottleneck Analysis**
```
Common bottlenecks:
1. WAN link capacity
2. LAN switch capacity
3. Server processing power
4. Storage I/O performance
5. Application inefficiencies
6. Network configuration issues

Analysis methods:
- Traffic flow analysis
- Capacity planning
- Performance baselining
- Trend analysis
```

#### **Capacity Planning**
```
Current utilization:
- Peak usage: ________%
- Average usage: ________%
- Off-peak usage: ________%

Growth projections:
- Historical growth rate: ________%
- Future requirements: ________
- Upgrade timeline: ________
- Cost analysis: ________
```

### Step 2: Performance Tuning
**Optimize network performance:**

#### **TCP/IP Optimization**
```
TCP Window Size:
- Default: 64KB
- Optimal: Based on bandwidth-delay product
- Calculation: Bandwidth × RTT

TCP Buffer Tuning:
- Send buffer size
- Receive buffer size
- Buffer allocation

TCP Congestion Control:
- Algorithm selection
- Parameter tuning
- Performance impact
```

#### **Network Configuration Optimization**
```
MTU Size:
- Default: 1500 bytes
- Jumbo frames: 9000 bytes
- Testing: ping with DF flag
- Impact: Throughput and efficiency

QoS Configuration:
- Traffic classification
- Bandwidth allocation
- Priority queuing
- Traffic shaping
```

### Step 3: Monitoring and Alerting
**Implement continuous performance monitoring:**

#### **Performance Baselines**
```
Establish baselines:
- Normal operating ranges
- Peak usage patterns
- Seasonal variations
- Growth trends

Baseline metrics:
- Bandwidth utilization
- Latency ranges
- Packet loss rates
- Error rates
- Application performance
```

#### **Alerting Configuration**
```
Alert thresholds:
- Bandwidth: > 80% utilization
- Latency: > 100ms RTT
- Packet loss: > 1%
- Errors: > 0.1%

Alert actions:
- Email notifications
- SMS alerts
- Dashboard updates
- Automated responses
- Escalation procedures
```

---

## Part 6: Performance Reporting

### Step 1: Data Collection and Analysis
**Gather and analyze performance data:**

#### **Performance Data Sources**
```
Network devices:
- Switch/router statistics
- Interface counters
- Error logs
- Configuration data

Applications:
- Response times
- Throughput metrics
- Error rates
- User experience data

Infrastructure:
- Server performance
- Storage metrics
- Power consumption
- Environmental factors
```

#### **Data Analysis Techniques**
```
Statistical analysis:
- Mean, median, mode
- Standard deviation
- Percentiles
- Trend analysis
- Correlation analysis

Visualization:
- Time series graphs
- Histograms
- Scatter plots
- Heat maps
- Dashboard displays
```

### Step 2: Performance Report Creation
**Create comprehensive performance reports:**

#### **Executive Summary**
```
Key findings:
- Overall network health
- Performance trends
- Critical issues
- Recommendations
- ROI analysis
```

#### **Detailed Analysis**
```
Performance metrics:
- Bandwidth utilization
- Latency analysis
- Packet loss rates
- Error analysis
- Capacity planning

Technical details:
- Network topology
- Configuration analysis
- Bottleneck identification
- Optimization opportunities
- Future recommendations
```

#### **Action Items**
```
Immediate actions:
- Critical issues to resolve
- Performance improvements
- Configuration changes
- Monitoring enhancements

Long-term planning:
- Capacity upgrades
- Technology refresh
- Process improvements
- Training requirements
```

---

## 📊 Lab Results Template

Fill out this template with your findings:

```
=== NETWORK PERFORMANCE ANALYSIS LAB ===

Environment: ________ (Home/Office/Lab)
Analysis Date: ________
Duration: ________

Part 1: Bandwidth Analysis
- Internet Download: ________ Mbps
- Internet Upload: ________ Mbps
- Local Network: ________ Mbps
- Utilization Peak: ________%
- Utilization Average: ________%

Part 2: Latency Analysis
- Average RTT: ________ ms
- Minimum RTT: ________ ms
- Maximum RTT: ________ ms
- Jitter: ________ ms
- Path Hops: ________

Part 3: Quality Analysis
- Packet Loss: ________%
- Error Rate: ________%
- Connection Quality: ________
- QoS Effectiveness: ________

Part 4: Performance Issues
- Bottlenecks Identified: ________
- Performance Gaps: ________
- Optimization Opportunities: ________
- Capacity Planning: ________

Part 5: Recommendations
- Immediate Actions: ________
- Short-term Improvements: ________
- Long-term Planning: ________
- ROI Analysis: ________
```

---

## 🔍 Analysis Questions

1. **Performance Metrics:** Which metrics were most important for your network environment?

2. **Bottleneck Identification:** How did you identify and analyze performance bottlenecks?

3. **Optimization Strategies:** What optimization techniques were most effective?

4. **Capacity Planning:** How would you plan for future network growth?

5. **Monitoring Implementation:** What monitoring and alerting would you implement?

---

## 🎓 Learning Outcomes

After completing this lab, you should understand:
- Network performance metrics and measurement techniques
- Bottleneck identification and analysis methods
- Performance optimization strategies
- Capacity planning and monitoring
- Performance reporting and documentation

---

## 🛠️ Recommended Tools

### **Performance Testing:**
- **iperf/iperf3:** Bandwidth testing
- **ping/traceroute:** Latency testing
- **Speedtest.net:** Internet speed testing
- **Wireshark:** Detailed traffic analysis

### **Monitoring Tools:**
- **Nagios:** Network monitoring
- **PRTG:** Performance monitoring
- **SolarWinds:** Enterprise monitoring
- **Zabbix:** Open-source monitoring

### **Analysis Tools:**
- **Excel/Google Sheets:** Data analysis
- **Python Scripts:** Custom analysis
- **Grafana:** Visualization and dashboards
- **Kibana:** Log analysis and visualization

---

## ⚠️ Important Notes

### **Best Practices:**
- **Establish baselines** before making changes
- **Test in non-production** environments
- **Document all changes** and their impact
- **Monitor continuously** after optimizations
- **Plan for growth** and scalability

### **Performance Optimization:**
- **Measure before and after** changes
- **Focus on user experience** metrics
- **Consider total cost** of optimization
- **Balance performance** with security
- **Plan for maintenance** and updates

---

**Next Lab:** [Lab 08: Network Security Analysis](./lab08-security-analysis.md) 