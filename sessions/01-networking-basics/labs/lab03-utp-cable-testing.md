# Lab 03: UTP Cable Testing and Termination

## 🎯 Objective
Learn to test, terminate, and troubleshoot UTP cables using proper tools and techniques. Understand cable categories, standards, and performance characteristics.

## 🛠️ Prerequisites
- UTP cable (Cat 5e or Cat 6 recommended)
- RJ-45 connectors
- Cable crimping tool
- Cable tester (basic or advanced)
- Wire stripper
- Scissors or cable cutter
- Safety glasses

## 📋 Lab Overview
This lab will cover:
1. UTP cable structure and color coding
2. RJ-45 termination techniques
3. Cable testing and certification
4. Troubleshooting common cable issues
5. Performance measurement

---

## Part 1: Understanding UTP Cable Structure

### Step 1: Examine UTP Cable
1. **Cut a 2-foot piece** of UTP cable
2. **Strip the outer jacket** carefully (about 1 inch)
3. **Identify the four pairs:**
   ```
   Pair 1: Blue/Blue-White
   Pair 2: Orange/Orange-White
   Pair 3: Green/Green-White
   Pair 4: Brown/Brown-White
   ```

### Step 2: Cable Specifications
**Record the following information:**
- **Cable Category:** ________ (Cat 5e, Cat 6, etc.)
- **AWG Size:** ________ (typically 24 AWG)
- **Jacket Type:** ________ (PVC, Plenum, etc.)
- **Manufacturer:** ________
- **Part Number:** ________

### Step 3: Color Coding Standards
**Learn the T568A and T568B standards:**

```
T568A Pinout:
Pin 1: Green-White
Pin 2: Green
Pin 3: Orange-White
Pin 4: Blue
Pin 5: Blue-White
Pin 6: Orange
Pin 7: Brown-White
Pin 8: Brown

T568B Pinout:
Pin 1: Orange-White
Pin 2: Orange
Pin 3: Green-White
Pin 4: Blue
Pin 5: Blue-White
Pin 6: Green
Pin 7: Brown-White
Pin 8: Brown
```

---

## Part 2: RJ-45 Termination

### Step 1: Prepare the Cable
1. **Cut cable to desired length** (minimum 1 foot, maximum 100 meters)
2. **Strip outer jacket** (about 1 inch)
3. **Untwist pairs** carefully
4. **Arrange wires** according to T568B standard
5. **Trim wires** to uniform length (about 0.5 inch)

### Step 2: Insert into RJ-45 Connector
1. **Hold connector** with clip facing down
2. **Insert wires** in correct order
3. **Push wires** all the way to the end
4. **Verify wire order** through transparent connector
5. **Check jacket** extends into connector

### Step 3: Crimp the Connector
1. **Insert connector** into crimping tool
2. **Squeeze handle** firmly until it clicks
3. **Remove connector** from tool
4. **Inspect crimp** for proper termination
5. **Repeat** for other end of cable

### Step 4: Create Different Cable Types
**Make the following cables:**

#### **Straight-through Cable (T568B to T568B)**
- **Use:** PC to switch, PC to router
- **Both ends:** T568B pinout
- **Length:** 3 feet

#### **Crossover Cable (T568B to T568A)**
- **Use:** PC to PC, switch to switch
- **One end:** T568B, other end: T568A
- **Length:** 3 feet

#### **Rollover Cable (Console Cable)**
- **Use:** Console connection to network devices
- **Pinout:** Completely reversed
- **Length:** 6 feet

---

## Part 3: Cable Testing

### Step 1: Basic Cable Testing
**Use a basic cable tester:**

1. **Connect cable** to tester
2. **Power on** the tester
3. **Observe LED indicators:**
   - **Green:** Good connection
   - **Red:** Open circuit
   - **No light:** Short circuit
   - **Wrong order:** Split pair

### Step 2: Wire Map Testing
**Verify each wire connection:**

```
Expected Results for Straight-through Cable:
Pin 1 → Pin 1: Green
Pin 2 → Pin 2: Green
Pin 3 → Pin 3: Green
Pin 4 → Pin 4: Green
Pin 5 → Pin 5: Green
Pin 6 → Pin 6: Green
Pin 7 → Pin 7: Green
Pin 8 → Pin 8: Green
```

### Step 3: Advanced Testing (if available)
**Use a certification tester for:**

#### **Length Test**
- **Expected:** Actual cable length
- **Maximum:** 100 meters for most applications
- **Unit:** Meters or feet

#### **Attenuation Test**
- **Purpose:** Measure signal loss
- **Frequency:** 1-100 MHz
- **Result:** dB loss per frequency

#### **NEXT Test (Near-End Crosstalk)**
- **Purpose:** Measure interference between pairs
- **Frequency:** 1-100 MHz
- **Result:** dB margin

#### **Return Loss**
- **Purpose:** Measure signal reflection
- **Frequency:** 1-100 MHz
- **Result:** dB reflection

---

## Part 4: Performance Testing

### Step 1: Network Speed Test
1. **Connect cable** between two computers
2. **Configure IP addresses** on same subnet
3. **Run speed test** using network tools
4. **Record results:**
   ```
   Cable Type: ________
   Speed Achieved: ________ Mbps
   Expected Speed: ________ Mbps
   Performance: ________%
   ```

### Step 2: Ping Test
1. **Ping between devices** using cable
2. **Record latency:**
   ```
   Average Latency: ________ ms
   Minimum Latency: ________ ms
   Maximum Latency: ________ ms
   Packet Loss: ________%
   ```

### Step 3: Throughput Test
1. **Transfer large file** between devices
2. **Measure transfer time**
3. **Calculate throughput:**
   ```
   File Size: ________ MB
   Transfer Time: ________ seconds
   Throughput: ________ Mbps
   ```

---

## Part 5: Troubleshooting

### Step 1: Common Issues
**Test and document these problems:**

#### **Open Circuit**
- **Symptoms:** No connectivity, LED off
- **Causes:** Broken wire, poor crimp
- **Solution:** Re-terminate cable

#### **Short Circuit**
- **Symptoms:** No connectivity, LED on
- **Causes:** Wires touching, damaged insulation
- **Solution:** Replace cable

#### **Split Pair**
- **Symptoms:** Intermittent connectivity
- **Causes:** Wrong wire order
- **Solution:** Re-terminate with correct order

#### **Reversed Pair**
- **Symptoms:** No connectivity
- **Causes:** Wires in pair swapped
- **Solution:** Correct wire order

### Step 2: Environmental Factors
**Test cable performance under different conditions:**

#### **Temperature Test**
- **Cold:** Test at low temperature
- **Hot:** Test at high temperature
- **Result:** Performance variation

#### **Bend Radius Test**
- **Sharp bend:** Test with tight bend
- **Normal bend:** Test with proper radius
- **Result:** Performance impact

#### **Interference Test**
- **Near power cables:** Test near electrical interference
- **Away from interference:** Test in clean environment
- **Result:** Performance difference

---

## Part 6: Cable Management

### Step 1: Cable Organization
1. **Label cables** with clear identifiers
2. **Use cable ties** for organization
3. **Route cables** properly
4. **Document** cable runs

### Step 2: Cable Documentation
**Create cable documentation:**

```
Cable ID: CABLE-001
Type: Cat 6 UTP
Length: 25 feet
Termination: T568B to T568B
Use: PC to Switch
Location: Office A to Server Room
Installation Date: ________
Tester Used: ________
Test Results: ________
```

### Step 3: Best Practices
**Follow these guidelines:**

#### **Installation**
- **Maximum length:** 100 meters
- **Bend radius:** 4x cable diameter
- **Tension:** Maximum 25 lbs
- **Separation:** Keep away from electrical interference

#### **Testing**
- **Test every cable** before installation
- **Document results** for future reference
- **Use proper tools** for testing
- **Follow standards** for termination

---

## 📊 Lab Results Template

Fill out this template with your findings:

```
=== UTP CABLE TESTING LAB RESULTS ===

Part 1: Cable Structure
- Cable Category: ________
- AWG Size: ________
- Color Coding: ________
- Standards Compliance: ________

Part 2: Termination
- Straight-through Cable: ________ (Pass/Fail)
- Crossover Cable: ________ (Pass/Fail)
- Rollover Cable: ________ (Pass/Fail)
- Termination Quality: ________ (Good/Fair/Poor)

Part 3: Testing Results
- Wire Map Test: ________ (Pass/Fail)
- Length Test: ________ meters
- Attenuation: ________ dB
- NEXT Test: ________ dB

Part 4: Performance
- Network Speed: ________ Mbps
- Latency: ________ ms
- Throughput: ________ Mbps
- Performance Rating: ________%

Part 5: Troubleshooting
- Issues Found: ________
- Solutions Applied: ________
- Final Status: ________ (Working/Not Working)
```

---

## 🔍 Analysis Questions

1. **Cable Categories:** How does Cat 6 performance compare to Cat 5e?

2. **Standards:** Why are T568A and T568B standards important?

3. **Testing:** What is the difference between a wire map test and a certification test?

4. **Performance:** How do environmental factors affect cable performance?

5. **Troubleshooting:** What are the most common cable termination problems?

---

## 🎓 Learning Outcomes

After completing this lab, you should understand:
- UTP cable structure and color coding
- Proper RJ-45 termination techniques
- Cable testing and certification procedures
- Common cable problems and solutions
- Performance measurement and documentation

---

## 🛠️ Recommended Tools

### **Basic Tools:**
- **Cable Tester:** Basic continuity and wire map testing
- **Crimping Tool:** RJ-45 connector termination
- **Wire Stripper:** Cable preparation
- **Cable Cutter:** Clean cable cutting

### **Advanced Tools:**
- **Certification Tester:** Professional testing and certification
- **TDR (Time Domain Reflectometer):** Distance and fault location
- **Network Analyzer:** Advanced performance testing
- **Cable Certifier:** Full compliance testing

### **Safety Equipment:**
- **Safety Glasses:** Eye protection
- **Gloves:** Hand protection
- **Proper Lighting:** Good visibility
- **Ventilation:** For crimping operations

---

**Next Lab:** [Lab 04: Network Device Identification](./lab04-device-identification.md) 