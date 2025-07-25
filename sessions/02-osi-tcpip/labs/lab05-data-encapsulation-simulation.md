# Lab 05: Data Encapsulation Simulation

## 🎯 Objective
Understand data encapsulation by simulating the OSI layer process and measuring protocol overhead using various network analysis tools.

## 🛠️ Prerequisites
- Computer with Windows, macOS, or Linux
- Network connection
- Basic command line knowledge
- Wireshark installed (free download from wireshark.org)

## 📋 Lab Overview
This lab will demonstrate how data encapsulation works by:
1. Capturing real network traffic
2. Analyzing protocol overhead
3. Simulating encapsulation process
4. Calculating bandwidth efficiency

---

## Part 1: Real Traffic Analysis with Wireshark

### Step 1: Install and Configure Wireshark
1. **Download Wireshark** from https://www.wireshark.org/
2. **Install with default settings**
3. **Launch Wireshark** as administrator (Windows) or with sudo (Linux/macOS)

### Step 2: Capture HTTP Traffic
1. **Start a new capture:**
   - Click "Capture" → "Start capturing packets"
   - Select your active network interface
   - Click "Start"

2. **Generate HTTP traffic:**
   - Open a web browser
   - Navigate to http://httpbin.org/get
   - This will generate a simple HTTP GET request

3. **Stop the capture** after the page loads

### Step 3: Analyze Packet Structure
1. **Find the HTTP request packet:**
   - Look for packets with "GET" in the Info column
   - Click on the packet to see the details

2. **Examine each layer:**
   ```
   Frame (Physical Layer):
   - Frame length: ____ bytes
   - Captured length: ____ bytes
   
   Ethernet II (Data Link Layer):
   - Destination: ____
   - Source: ____
   - Type: ____
   
   Internet Protocol (Network Layer):
   - Version: ____
   - Header length: ____ bytes
   - Total length: ____ bytes
   - Source: ____
   - Destination: ____
   
   Transmission Control Protocol (Transport Layer):
   - Source port: ____
   - Destination port: ____
   - Sequence number: ____
   - Header length: ____ bytes
   
   Hypertext Transfer Protocol (Application Layer):
   - Request Method: ____
   - Request URI: ____
   - Request Version: ____
   ```

3. **Calculate overhead:**
   - Record the total frame size
   - Record the HTTP payload size
   - Calculate: Overhead = (Total - Payload) / Total × 100%

---

## Part 2: Protocol Overhead Calculator

### Step 1: Create Overhead Calculator Script
Create a Python script to simulate encapsulation:

```python
#!/usr/bin/env python3
# encapsulation_calculator.py

def calculate_encapsulation_overhead(original_data_size):
    """Calculate protocol overhead for different data sizes"""
    
    # Protocol header sizes (in bytes)
    headers = {
        'http': 200,      # HTTP headers (approximate)
        'tcp': 20,        # TCP header (minimum)
        'ip': 20,         # IP header (minimum)
        'ethernet': 18,   # Ethernet header + trailer
        'physical': 9     # Preamble + delimiter
    }
    
    # Calculate total overhead
    total_overhead = sum(headers.values())
    total_transmitted = original_data_size + total_overhead
    
    # Calculate efficiency
    efficiency = (original_data_size / total_transmitted) * 100
    overhead_percentage = (total_overhead / total_transmitted) * 100
    
    return {
        'original_size': original_data_size,
        'total_overhead': total_overhead,
        'total_transmitted': total_transmitted,
        'efficiency': efficiency,
        'overhead_percentage': overhead_percentage,
        'headers': headers
    }

def print_analysis(data_sizes):
    """Print analysis for different data sizes"""
    print("=" * 60)
    print("DATA ENCAPSULATION OVERHEAD ANALYSIS")
    print("=" * 60)
    
    for size in data_sizes:
        result = calculate_encapsulation_overhead(size)
        
        print(f"\nOriginal Data Size: {size:,} bytes")
        print(f"Protocol Overhead: {result['total_overhead']} bytes")
        print(f"Total Transmitted: {result['total_transmitted']:,} bytes")
        print(f"Efficiency: {result['efficiency']:.1f}%")
        print(f"Overhead: {result['overhead_percentage']:.1f}%")
        
        print("\nHeader Breakdown:")
        for protocol, header_size in result['headers'].items():
            print(f"  {protocol.upper()}: {header_size} bytes")

# Test with different data sizes
test_sizes = [100, 1000, 10000, 100000, 1000000]
print_analysis(test_sizes)
```

### Step 2: Run the Calculator
1. **Save the script** as `encapsulation_calculator.py`
2. **Run the script:**
   ```bash
   python3 encapsulation_calculator.py
   ```
3. **Analyze the results** and note how efficiency changes with data size

---

## Part 3: Bandwidth vs File Size Simulation

### Step 1: Create Bandwidth Calculator
Create a script to calculate actual download times:

```python
#!/usr/bin/env python3
# bandwidth_calculator.py

def calculate_download_time(file_size_mb, bandwidth_mbps, overhead_percentage=5):
    """
    Calculate actual download time considering protocol overhead
    
    Args:
        file_size_mb: File size in megabytes
        bandwidth_mbps: Bandwidth in megabits per second
        overhead_percentage: Protocol overhead percentage (default 5%)
    """
    
    # Convert file size to bits
    file_size_bits = file_size_mb * 8 * 1024 * 1024
    
    # Calculate effective bandwidth (accounting for overhead)
    effective_bandwidth_mbps = bandwidth_mbps * (1 - overhead_percentage / 100)
    
    # Calculate download time in seconds
    download_time_seconds = file_size_bits / (effective_bandwidth_mbps * 1000000)
    
    # Calculate theoretical time (without overhead)
    theoretical_time = file_size_bits / (bandwidth_mbps * 1000000)
    
    return {
        'file_size_mb': file_size_mb,
        'bandwidth_mbps': bandwidth_mbps,
        'effective_bandwidth_mbps': effective_bandwidth_mbps,
        'theoretical_time': theoretical_time,
        'actual_time': download_time_seconds,
        'overhead_impact': download_time_seconds - theoretical_time
    }

def print_bandwidth_analysis():
    """Print bandwidth analysis for common scenarios"""
    
    scenarios = [
        (100, 100),    # 100MB file, 100Mbps connection
        (1000, 100),   # 1GB file, 100Mbps connection
        (100, 1000),   # 100MB file, 1Gbps connection
        (1000, 1000),  # 1GB file, 1Gbps connection
    ]
    
    print("=" * 70)
    print("BANDWIDTH vs FILE SIZE ANALYSIS")
    print("=" * 70)
    
    for file_size, bandwidth in scenarios:
        result = calculate_download_time(file_size, bandwidth)
        
        print(f"\nFile Size: {file_size} MB")
        print(f"Connection: {bandwidth} Mbps")
        print(f"Effective Bandwidth: {result['effective_bandwidth_mbps']:.1f} Mbps")
        print(f"Theoretical Time: {result['theoretical_time']:.1f} seconds")
        print(f"Actual Time: {result['actual_time']:.1f} seconds")
        print(f"Overhead Impact: +{result['overhead_impact']:.1f} seconds")
        print(f"Efficiency: {(result['theoretical_time']/result['actual_time'])*100:.1f}%")

if __name__ == "__main__":
    print_bandwidth_analysis()
```

### Step 2: Run Bandwidth Analysis
1. **Save the script** as `bandwidth_calculator.py`
2. **Run the analysis:**
   ```bash
   python3 bandwidth_calculator.py
   ```
3. **Compare results** with your expectations

---

## Part 4: Advanced Simulation with Network Emulator

### Step 1: Install Network Emulation Tools

#### **Option A: GNS3 (Recommended)**
1. **Download GNS3** from https://www.gns3.com/
2. **Install with default settings**
3. **Add MikroTik RouterOS** appliance
4. **Create a simple topology** with two routers

#### **Option B: Cisco Packet Tracer**
1. **Download Packet Tracer** (if you have access)
2. **Create a simple network** with two PCs and a switch
3. **Configure IP addressing**

#### **Option C: Online Simulator**
1. **Use Cisco NetAcad** Packet Tracer (if available)
2. **Or use online network simulators** like:
   - https://www.netacad.com/courses/packet-tracer
   - https://www.cloudshark.org/ (for packet analysis)

### Step 2: Simulate Different Protocols
1. **Create test scenarios:**
   - HTTP traffic (TCP-based)
   - DNS queries (UDP-based)
   - Ping (ICMP)
   - FTP transfer (TCP-based)

2. **Capture and analyze** each protocol type
3. **Compare overhead** between different protocols

---

## Part 5: Real-World Testing

### Step 1: Speed Test Analysis
1. **Run multiple speed tests:**
   - https://www.speedtest.net/
   - https://fast.com/
   - Your ISP's speed test

2. **Record results:**
   - Download speed
   - Upload speed
   - Latency
   - Jitter

3. **Calculate efficiency:**
   - Compare advertised vs actual speeds
   - Account for protocol overhead

### Step 2: File Download Testing
1. **Download a large file** (100MB+) from a reliable source
2. **Time the download** using a stopwatch
3. **Calculate actual throughput:**
   ```
   Actual Throughput = File Size / Download Time
   Efficiency = Actual Throughput / Advertised Speed
   ```

---

## 📊 Lab Results Template

Fill out this template with your findings:

```
=== DATA ENCAPSULATION LAB RESULTS ===

Part 1: Wireshark Analysis
- HTTP Request Frame Size: ________ bytes
- HTTP Payload Size: ________ bytes
- Protocol Overhead: ________ bytes
- Overhead Percentage: ________%

Part 2: Protocol Overhead Calculator
- 1KB Data Efficiency: ________%
- 10KB Data Efficiency: ________%
- 100KB Data Efficiency: ________%
- 1MB Data Efficiency: ________%

Part 3: Bandwidth Analysis
- 1GB File, 1Gbps Connection:
  * Theoretical Time: ________ seconds
  * Actual Time: ________ seconds
  * Overhead Impact: ________ seconds

Part 4: Real-World Testing
- Advertised Speed: ________ Mbps
- Actual Download Speed: ________ Mbps
- Efficiency: ________%
- Observed Overhead: ________%
```

---

## 🔍 Analysis Questions

1. **Overhead Impact:** How does data size affect protocol efficiency? Why?

2. **Protocol Comparison:** Which protocol (TCP vs UDP) has more overhead? Why?

3. **Bandwidth Reality:** Why do ISPs advertise speeds that are rarely achieved?

4. **Optimization:** What strategies could reduce protocol overhead?

5. **Future Protocols:** How might QUIC improve efficiency compared to TCP?

---

## 🎓 Learning Outcomes

After completing this lab, you should understand:
- How protocol headers add overhead to network traffic
- Why bandwidth doesn't directly translate to file transfer speed
- How to calculate and measure protocol efficiency
- Tools and techniques for network traffic analysis
- Real-world implications of protocol overhead

---

## 🛠️ Recommended Tools

### **Free Tools:**
- **Wireshark:** Packet capture and analysis
- **Python:** Scripting and calculations
- **Speedtest.net:** Real-world speed testing
- **GNS3:** Network simulation (free tier)

### **Commercial Tools:**
- **Cisco Packet Tracer:** Network simulation
- **SolarWinds:** Network monitoring
- **PRTG:** Network monitoring
- **Wireshark Pro:** Advanced features

### **Online Resources:**
- **CloudShark:** Online packet analysis
- **NetAcad:** Cisco learning resources
- **MikroTik Wiki:** RouterOS documentation

---

**Next Lab:** [Lab 06: Protocol Analysis with Wireshark](./lab06-wireshark-analysis.md) 