# Quiz: Routing Fundamentals

## 📝 Instructions
- **Time Limit:** 20 minutes
- **Total Questions:** 25
- **Passing Score:** 80% (20 correct answers)
- **Question Types:** Multiple Choice, True/False, Fill in the Blank

---

## 🎯 Quiz Questions

### **Section 1: Routing Fundamentals (5 questions)**

#### **Question 1**
What is the primary function of a router?
- [ ] A. To connect devices within the same network
- [ ] B. To forward packets between different networks
- [ ] C. To provide wireless connectivity
- [ ] D. To store network data

#### **Question 2**
Which layer of the OSI model does routing operate at?
- [ ] A. Layer 1 (Physical)
- [ ] B. Layer 2 (Data Link)
- [ ] C. Layer 3 (Network)
- [ ] D. Layer 4 (Transport)

#### **Question 3**
What is the main difference between routing and switching?
- [ ] A. Routing uses MAC addresses, switching uses IP addresses
- [ ] B. Routing operates at Layer 3, switching operates at Layer 2
- [ ] C. Routing is faster than switching
- [ ] D. Switching is more complex than routing

#### **Question 4**
Which of the following is NOT a core router function?
- [ ] A. Packet forwarding
- [ ] B. Path determination
- [ ] C. Network interconnection
- [ ] D. Data encryption

#### **Question 5**
What is the purpose of a routing table?
- [ ] A. To store user data
- [ ] B. To maintain a list of available routes to destination networks
- [ ] C. To configure router interfaces
- [ ] D. To manage user accounts

---

### **Section 2: Routing Table Components (5 questions)**

#### **Question 6**
Which field in a routing table indicates the destination network?
- [ ] A. Gateway
- [ ] B. Interface
- [ ] C. Destination
- [ ] D. Metric

#### **Question 7**
What does the "Next Hop" field represent?
- [ ] A. The final destination of the packet
- [ ] B. The IP address of the next router in the path
- [ ] C. The source address of the packet
- [ ] D. The interface name

#### **Question 8**
Which routing table field indicates the trustworthiness of a route source?
- [ ] A. Metric
- [ ] B. Administrative Distance
- [ ] C. Interface
- [ ] D. Gateway

#### **Question 9**
What is the administrative distance of a connected route?
- [ ] A. 0
- [ ] B. 1
- [ ] C. 110
- [ ] D. 255

#### **Question 10**
Which route selection criterion is checked first?
- [ ] A. Administrative Distance
- [ ] B. Metric
- [ ] C. Longest Match
- [ ] D. Interface Status

---

### **Section 3: Static Routing (5 questions)**

#### **Question 11**
What is a static route?
- [ ] A. A route that changes automatically
- [ ] B. A manually configured route
- [ ] C. A route learned from a routing protocol
- [ ] D. A default route

#### **Question 12**
What is the RouterOS command to add a static route?
- [ ] A. `/ip route add`
- [ ] B. `/route add`
- [ ] C. `/static route add`
- [ ] D. `/routing add`

#### **Question 13**
What is the purpose of a default route (0.0.0.0/0)?
- [ ] A. To route traffic to a specific network
- [ ] B. To provide a route of last resort for unknown destinations
- [ ] C. To connect to the internet
- [ ] D. To configure a backup route

#### **Question 14**
What is a floating static route?
- [ ] A. A route that moves between routers
- [ ] B. A backup route with higher administrative distance
- [ ] C. A route that changes automatically
- [ ] D. A default route

#### **Question 15**
Which command shows all static routes in RouterOS?
- [ ] A. `/ip route print where static=yes`
- [ ] B. `/ip route print where distance=1`
- [ ] C. `/ip route print where type=static`
- [ ] D. `/ip route print where source=static`

---

### **Section 4: Dynamic Routing (5 questions)**

#### **Question 16**
What is the main advantage of dynamic routing over static routing?
- [ ] A. Lower administrative overhead
- [ ] B. Automatic adaptation to network changes
- [ ] C. Better security
- [ ] D. Faster packet forwarding

#### **Question 17**
Which routing protocol is a distance vector protocol?
- [ ] A. OSPF
- [ ] B. RIP
- [ ] C. BGP
- [ ] D. IS-IS

#### **Question 18**
What is the maximum hop count for RIP?
- [ ] A. 10
- [ ] B. 15
- [ ] C. 16
- [ ] D. 255

#### **Question 19**
Which routing protocol uses the Dijkstra algorithm?
- [ ] A. RIP
- [ ] B. OSPF
- [ ] C. EIGRP
- [ ] D. BGP

#### **Question 20**
What is convergence in routing?
- [ ] A. The time it takes for all routers to have consistent routing information
- [ ] B. The process of learning routes from neighbors
- [ ] C. The selection of the best route
- [ ] D. The configuration of routing protocols

---

### **Section 5: Routing Metrics and Selection (5 questions)**

#### **Question 21**
Which metric does RIP use?
- [ ] A. Bandwidth
- [ ] B. Hop count
- [ ] C. Delay
- [ ] D. Cost

#### **Question 22**
What happens when two routes have the same administrative distance but different metrics?
- [ ] A. The route with lower metric is preferred
- [ ] B. Both routes are used for load balancing
- [ ] C. The route with higher metric is preferred
- [ ] D. Neither route is used

#### **Question 23**
What is the administrative distance of OSPF?
- [ ] A. 90
- [ ] B. 110
- [ ] C. 120
- [ ] D. 170

#### **Question 24**
Which of the following is NOT a routing metric?
- [ ] A. Hop count
- [ ] B. Bandwidth
- [ ] C. Delay
- [ ] D. MAC address

#### **Question 25**
What is the purpose of route summarization?
- [ ] A. To increase routing table size
- [ ] B. To reduce routing table size and improve convergence
- [ ] C. To make routes more specific
- [ ] D. To improve security

---

## 📋 Answer Key

### **Section 1: Routing Fundamentals**
1. **B** - To forward packets between different networks
2. **C** - Layer 3 (Network)
3. **B** - Routing operates at Layer 3, switching operates at Layer 2
4. **D** - Data encryption
5. **B** - To maintain a list of available routes to destination networks

### **Section 2: Routing Table Components**
6. **C** - Destination
7. **B** - The IP address of the next router in the path
8. **B** - Administrative Distance
9. **A** - 0
10. **C** - Longest Match

### **Section 3: Static Routing**
11. **B** - A manually configured route
12. **A** - `/ip route add`
13. **B** - To provide a route of last resort for unknown destinations
14. **B** - A backup route with higher administrative distance
15. **B** - `/ip route print where distance=1`

### **Section 4: Dynamic Routing**
16. **B** - Automatic adaptation to network changes
17. **B** - RIP
18. **B** - 15
19. **B** - OSPF
20. **A** - The time it takes for all routers to have consistent routing information

### **Section 5: Routing Metrics and Selection**
21. **B** - Hop count
22. **A** - The route with lower metric is preferred
23. **B** - 110
24. **D** - MAC address
25. **B** - To reduce routing table size and improve convergence

---

## 📊 Scoring Guide

### **Score Calculation**
- **Correct Answers:** 1 point each
- **Total Possible:** 25 points
- **Passing Score:** 20 points (80%)

### **Performance Levels**
- **90-100% (23-25 points):** Excellent understanding
- **80-89% (20-22 points):** Good understanding
- **70-79% (18-19 points):** Satisfactory understanding
- **Below 70% (<18 points):** Needs review

---

## 🔍 Review Topics

### **If you scored below 80%, review these topics:**

#### **Routing Fundamentals**
- Router functions and components
- Packet forwarding process
- Routing vs switching differences

#### **Routing Table Analysis**
- Routing table structure and fields
- Route selection process
- Administrative distance concepts

#### **Static Routing**
- Static route configuration
- Default routes and floating routes
- Route verification commands

#### **Dynamic Routing**
- Routing protocol types
- Distance vector vs link state
- Convergence concepts

#### **Routing Metrics**
- Common routing metrics
- Route selection criteria
- Route summarization

---

## 📚 Additional Resources

### **For Further Study**
- [Routing Fundamentals](./../theory/routing-fundamentals.md)
- [Static Routing Configuration](./../theory/static-routing.md)
- [Dynamic Routing Protocols](./../theory/dynamic-routing.md)
- [Lab 01: Static Route Configuration](./../labs/lab01-static-routes.md)
- [Lab 02: Routing Table Analysis](./../labs/lab02-routing-table.md)

### **Practice Exercises**
- Configure static routes in RouterOS
- Analyze routing table output
- Test route selection scenarios
- Practice troubleshooting routing issues

---

## ✅ Quiz Completion Checklist

- [ ] All 25 questions answered
- [ ] Answer key reviewed
- [ ] Score calculated
- [ ] Performance level determined
- [ ] Weak areas identified
- [ ] Review topics selected
- [ ] Additional practice planned 