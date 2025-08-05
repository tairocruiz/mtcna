# Routing Table Explained: Understanding 0.0.0.0 and Default Routes

## 📋 What is a Routing Table?

A **routing table** is a data structure stored in a router's memory that contains information about how to reach destination networks. Think of it as a "map" that tells the router where to send packets based on their destination IP address.

### **Purpose of Routing Tables**
- **Path Selection:** Determines the best route to each destination
- **Packet Forwarding:** Guides packets from source to destination
- **Network Discovery:** Maintains information about reachable networks
- **Fault Tolerance:** Provides backup routes when primary paths fail

---

## 🏗️ RouterOS Routing Table Structure

### **Basic Routing Table Fields**

When you run `/ip route print` in RouterOS, you'll see a table with these columns:

```
DST-ADDRESS        GATEWAY         DISTANCE  INTERFACE
0.0.0.0/0         192.168.1.1     1         ether1
192.168.1.0/24    -               0         ether1
192.168.2.0/24    192.168.1.10    1         ether1
```

#### **Field Explanations:**

| Field | Description | Example |
|-------|-------------|---------|
| **DST-ADDRESS** | Destination network address and subnet mask | `192.168.2.0/24` |
| **GATEWAY** | Next-hop IP address (where to send packet) | `192.168.1.10` |
| **DISTANCE** | Administrative distance (trustworthiness) | `1` (static route) |
| **INTERFACE** | Outgoing interface name | `ether1` |

### **Detailed RouterOS Routing Table**

Using `/ip route print detail` shows additional information:

```
DST-ADDRESS: 192.168.2.0/24
GATEWAY: 192.168.1.10
DISTANCE: 1
INTERFACE: ether1
COMMENT: Branch Office Route
ACTIVE: yes
DYNAMIC: no
```

---

## 🎯 Understanding the 0.0.0.0/0 Route (Default Route)

### **What is 0.0.0.0/0?**

The **0.0.0.0/0** route is the **default route** or **gateway of last resort**. It's a catch-all route that tells the router where to send packets when no specific route exists for the destination.

#### **Breaking Down 0.0.0.0/0:**
- **0.0.0.0:** Represents "any" IP address
- **/0:** Subnet mask of 0.0.0.0 (no bits set)
- **Combined:** Matches ANY destination IP address

### **How Default Routes Work**

#### **Route Selection Process:**
1. **Longest Match First:** Router looks for most specific route
2. **If No Match Found:** Router uses default route (0.0.0.0/0)
3. **Packet Forwarded:** To the gateway specified in default route

#### **Example Scenario:**
```
Router receives packet for destination: 203.0.113.45
Routing table entries:
- 192.168.1.0/24 → ether1 (connected)
- 192.168.2.0/24 → 192.168.1.10 (static)
- 0.0.0.0/0 → 192.168.1.1 (default)

Result: Packet sent to 192.168.1.1 (default gateway)
```

---

## 🔧 Configuring Default Routes in RouterOS

### **Basic Default Route Configuration**

```bash
# Add default route to internet
/ip route add dst-address=0.0.0.0/0 gateway=192.168.1.1 comment="Internet Default"
```

### **Multiple Default Routes (Load Balancing)**

```bash
# Primary default route
/ip route add dst-address=0.0.0.0/0 gateway=192.168.1.1 distance=1

# Backup default route
/ip route add dst-address=0.0.0.0/0 gateway=192.168.1.2 distance=10
```

### **Interface-Based Default Route**

```bash
# Default route via specific interface
/ip route add dst-address=0.0.0.0/0 gateway=ether2
```

---

## 📊 Default Route Examples

### **Scenario 1: Home Router**

```
Internet ←→ [Router] ←→ Home Network
          192.168.1.1   192.168.1.0/24
```

**Router Configuration:**
```bash
# Connected route (local network)
/ip route add dst-address=192.168.1.0/24 gateway=ether1

# Default route (internet)
/ip route add dst-address=0.0.0.0/0 gateway=203.0.113.1 comment="Internet"
```

**Result:**
- Local traffic (192.168.1.x) stays on local network
- All other traffic goes to internet via 203.0.113.1

### **Scenario 2: Corporate Network**

```
Internet ←→ [Core Router] ←→ [Branch Router] ←→ Branch Network
          203.0.113.1     192.168.1.1        192.168.2.0/24
```

**Core Router:**
```bash
# Default route to internet
/ip route add dst-address=0.0.0.0/0 gateway=203.0.113.1

# Route to branch network
/ip route add dst-address=192.168.2.0/24 gateway=192.168.1.10
```

**Branch Router:**
```bash
# Default route to core router
/ip route add dst-address=0.0.0.0/0 gateway=192.168.1.1

# Local network route
/ip route add dst-address=192.168.2.0/24 gateway=ether2
```

---

## 🔍 Verifying Default Routes

### **View Default Routes**

```bash
# Show all default routes
/ip route print where dst-address=0.0.0.0/0

# Show active default routes only
/ip route print where dst-address=0.0.0.0/0 and active=yes

# Show default routes with details
/ip route print detail where dst-address=0.0.0.0/0
```

### **Test Default Route Functionality**

```bash
# Test connectivity to internet
/ping 8.8.8.8

# Test connectivity to external site
/ping google.com

# Traceroute to see path
/traceroute 8.8.8.8
```

---

## 🚨 Common Default Route Issues

### **Issue 1: No Default Route**
**Symptoms:**
- Can't reach internet
- Can't reach external networks
- Only local network works

**Solution:**
```bash
# Add default route
/ip route add dst-address=0.0.0.0/0 gateway=192.168.1.1
```

### **Issue 2: Wrong Gateway**
**Symptoms:**
- Intermittent connectivity
- Timeout errors
- Packet loss

**Solution:**
```bash
# Check gateway reachability
/ping 192.168.1.1

# Update default route
/ip route set [find dst-address=0.0.0.0/0] gateway=192.168.1.2
```

### **Issue 3: Multiple Default Routes**
**Symptoms:**
- Unpredictable routing
- Load balancing (if equal distance)
- Route conflicts

**Solution:**
```bash
# View all default routes
/ip route print where dst-address=0.0.0.0/0

# Remove unwanted routes
/ip route remove [find dst-address=0.0.0.0/0 and gateway=192.168.1.3]
```

---

## 📈 Route Selection Process

### **RouterOS Route Selection Order**

1. **Longest Match:** Most specific route wins
   - `192.168.1.0/24` beats `192.168.0.0/16`

2. **Administrative Distance:** Lower is preferred
   - Connected (0) beats Static (1) beats OSPF (110)

3. **Metric:** Lower is preferred (within same protocol)
   - OSPF cost 10 beats OSPF cost 20

4. **Default Route:** Used when no other route matches
   - `0.0.0.0/0` is the least specific route

### **Example Route Selection**

```
Packet destination: 203.0.113.45

Available routes:
1. 192.168.1.0/24 → ether1 (connected, distance=0)
2. 192.168.2.0/24 → 192.168.1.10 (static, distance=1)
3. 0.0.0.0/0 → 192.168.1.1 (default, distance=1)

Result: Route 3 selected (default route)
```

---

## 🔧 Advanced Default Route Configurations

### **Floating Default Routes**

```bash
# Primary default route
/ip route add dst-address=0.0.0.0/0 gateway=192.168.1.1 distance=1 comment="Primary"

# Backup default route
/ip route add dst-address=0.0.0.0/0 gateway=192.168.1.2 distance=10 comment="Backup"
```

### **Load Balancing Default Routes**

```bash
# Equal-cost default routes
/ip route add dst-address=0.0.0.0/0 gateway=192.168.1.1 distance=1
/ip route add dst-address=0.0.0.0/0 gateway=192.168.1.2 distance=1
```

### **Policy-Based Default Routes**

```bash
# Default route for specific source
/ip route add dst-address=0.0.0.0/0 gateway=192.168.1.1 src-address=192.168.2.0/24

# Default route for specific interface
/ip route add dst-address=0.0.0.0/0 gateway=192.168.1.1 routing-mark=WAN1
```

---

## 📊 Monitoring Default Routes

### **Real-time Monitoring**

```bash
# Monitor default route changes
/ip route monitor [find dst-address=0.0.0.0/0]

# Monitor all route changes
/ip route monitor
```

### **Route Statistics**

```bash
# View route statistics
/ip route print stats-only

# Check route status
/ip route print where active=yes
```

---

## 🎯 Best Practices for Default Routes

### **1. Always Have a Default Route**
- Essential for internet connectivity
- Provides fallback for unknown destinations
- Required for most network configurations

### **2. Use Appropriate Administrative Distance**
- Primary routes: distance=1
- Backup routes: distance=10 or higher
- Avoid conflicts with dynamic routes

### **3. Verify Gateway Reachability**
- Test gateway before adding route
- Monitor gateway health
- Have backup gateways

### **4. Document Your Routes**
- Use comments for clarity
- Document route purposes
- Keep configuration backups

### **5. Test After Changes**
- Verify connectivity
- Test failover scenarios
- Monitor for issues

---

## ❓ Common Questions

### **Q: Why do I need a default route?**
**A:** Default routes handle traffic to destinations not specifically listed in your routing table, such as internet traffic.

### **Q: Can I have multiple default routes?**
**A:** Yes, but they should have different administrative distances to avoid conflicts. Equal-distance routes will load balance.

### **Q: What happens if my default route fails?**
**A:** Traffic to unknown destinations will be dropped unless you have a backup default route with higher administrative distance.

### **Q: How do I know if my default route is working?**
**A:** Test connectivity to external destinations like `8.8.8.8` or `google.com` using `/ping`.

### **Q: Can I remove the default route?**
**A:** Yes, but you'll lose connectivity to destinations not specifically routed. Only remove if you have specific routes for all needed destinations.

---

## 📚 Summary

The **0.0.0.0/0 default route** is a fundamental component of network routing that:

- **Acts as a catch-all** for unknown destinations
- **Enables internet connectivity** in most networks
- **Provides fault tolerance** when configured with backups
- **Follows route selection rules** (longest match, administrative distance, metric)

Understanding default routes is essential for:
- **Network design and implementation**
- **Troubleshooting connectivity issues**
- **MTCNA certification preparation**
- **Real-world network administration**

Master the default route concept, and you'll have a solid foundation for understanding routing in MikroTik RouterOS and beyond! 