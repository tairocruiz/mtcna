# Routing Commands Reference

## 📋 RouterOS Routing Commands

This reference provides the most commonly used RouterOS commands for routing configuration and management.

---

## 🔧 Basic Route Commands

### **View Routes**
```bash
# Display all routes
/ip route print

# Display active routes only
/ip route print where active=yes

# Display inactive routes only
/ip route print where active=no

# Display routes with details
/ip route print detail

# Count total routes
/ip route print count-only
```

### **Add Routes**
```bash
# Basic static route
/ip route add dst-address=192.168.2.0/24 gateway=192.168.1.1

# Static route with comment
/ip route add dst-address=192.168.2.0/24 gateway=192.168.1.1 comment="Branch Office"

# Default route
/ip route add dst-address=0.0.0.0/0 gateway=192.168.1.1

# Route with distance
/ip route add dst-address=192.168.2.0/24 gateway=192.168.1.1 distance=5

# Route with preference
/ip route add dst-address=192.168.2.0/24 gateway=192.168.1.1 preference=100

# Interface-based route
/ip route add dst-address=192.168.2.0/24 gateway=ether2
```

### **Remove Routes**
```bash
# Remove route by number
/ip route remove 0

# Remove route by destination
/ip route remove [find dst-address=192.168.2.0/24]

# Remove all routes to specific destination
/ip route remove [find dst-address=192.168.2.0/24]
```

### **Modify Routes**
```bash
# Change gateway
/ip route set 0 gateway=192.168.1.2

# Change distance
/ip route set 0 distance=10

# Change comment
/ip route set 0 comment="Updated Route"

# Enable/disable route
/ip route set 0 disabled=yes
/ip route set 0 disabled=no
```

---

## 🔍 Route Filtering Commands

### **Filter by Destination**
```bash
# Routes to specific network
/ip route print where dst-address=192.168.2.0/24

# Routes matching pattern
/ip route print where dst-address~"192.168"

# Routes to specific host
/ip route print where dst-address=192.168.2.1/32
```

### **Filter by Gateway**
```bash
# Routes via specific gateway
/ip route print where gateway=192.168.1.1

# Routes via gateway pattern
/ip route print where gateway~"192.168.1"
```

### **Filter by Distance**
```bash
# Connected routes (distance=0)
/ip route print where distance=0

# Static routes (distance=1)
/ip route print where distance=1

# Routes with specific distance
/ip route print where distance=5
```

### **Filter by Interface**
```bash
# Routes via specific interface
/ip route print where interface=ether1

# Routes via interface pattern
/ip route print where interface~"ether"
```

### **Filter by Status**
```bash
# Active routes only
/ip route print where active=yes

# Inactive routes only
/ip route print where active=no

# Dynamic routes only
/ip route print where dynamic=yes

# Static routes only
/ip route print where dynamic=no
```

---

## 📊 Route Analysis Commands

### **Route Statistics**
```bash
# Count routes by distance
/ip route print count-only where distance=0
/ip route print count-only where distance=1
/ip route print count-only where distance=5

# Count active routes
/ip route print count-only where active=yes

# Count routes by interface
/ip route print count-only where interface=ether1
```

### **Route Monitoring**
```bash
# Monitor route changes
/ip route monitor

# Monitor specific route
/ip route monitor 0

# Monitor routes to destination
/ip route monitor [find dst-address=192.168.2.0/24]
```

### **Route Details**
```bash
# Detailed route information
/ip route print detail

# Route with specific fields
/ip route print detail where dst-address=192.168.2.0/24

# Route statistics
/ip route print stats-only
```

---

## 🔧 Advanced Route Commands

### **Route Preferences**
```bash
# Add route with preference
/ip route add dst-address=192.168.2.0/24 gateway=192.168.1.1 preference=100

# View routes by preference
/ip route print where preference=100

# Change route preference
/ip route set 0 preference=200
```

### **Route Comments**
```bash
# Add route with comment
/ip route add dst-address=192.168.2.0/24 gateway=192.168.1.1 comment="Branch Office"

# View routes with comments
/ip route print where comment~"Branch"

# Update route comment
/ip route set 0 comment="Updated Branch Office"
```

### **Route Disabling**
```bash
# Disable route
/ip route set 0 disabled=yes

# Enable route
/ip route set 0 disabled=no

# View disabled routes
/ip route print where disabled=yes
```

---

## 🚨 Troubleshooting Commands

### **Connectivity Testing**
```bash
# Test gateway reachability
/ping 192.168.1.1

# Test destination reachability
/ping 192.168.2.1

# Traceroute to destination
/traceroute 192.168.2.1
```

### **Interface Status**
```bash
# Check interface status
/interface print

# Check interface details
/interface print detail

# Check interface statistics
/interface print stats-only
```

### **IP Address Verification**
```bash
# Check IP addresses
/ip address print

# Check IP addresses by interface
/ip address print where interface=ether1

# Check IP address details
/ip address print detail
```

---

## 📋 Route Management Commands

### **Route Backup and Restore**
```bash
# Export routes to file
/export file=backup-routes

# Import routes from file
/import file=backup-routes

# Export specific routes
/ip route print file=static-routes.txt
```

### **Route Cleanup**
```bash
# Remove all static routes
/ip route remove [find dynamic=no]

# Remove routes to specific destination
/ip route remove [find dst-address=192.168.2.0/24]

# Remove inactive routes
/ip route remove [find active=no]
```

### **Route Verification**
```bash
# Verify route exists
/ip route print where dst-address=192.168.2.0/24

# Check route status
/ip route print detail where dst-address=192.168.2.0/24

# Verify gateway reachability
/ping 192.168.1.1
```

---

## 🔧 Dynamic Routing Commands

### **RIP Commands**
```bash
# Enable RIP instance
/routing rip instance add name=rip-instance

# Add RIP interface
/routing rip interface add interface=ether1

# Start RIP
/routing rip instance enable rip-instance

# View RIP routes
/routing rip route print
```

### **OSPF Commands**
```bash
# Enable OSPF instance
/routing ospf instance add name=ospf-instance

# Add OSPF network
/routing ospf network add network=192.168.1.0/24 area=backbone

# Start OSPF
/routing ospf instance enable ospf-instance

# View OSPF routes
/routing ospf route print
```

### **BGP Commands**
```bash
# Enable BGP instance
/routing bgp instance add name=bgp-instance as=65000

# Add BGP peer
/routing bgp peer add name=peer1 remote-address=203.0.113.1 remote-as=65001

# Start BGP
/routing bgp instance enable bgp-instance

# View BGP routes
/routing bgp route print
```

---

## 📊 Route Monitoring Commands

### **Real-time Monitoring**
```bash
# Monitor all route changes
/ip route monitor

# Monitor specific route
/ip route monitor 0

# Monitor routes to destination
/ip route monitor [find dst-address=192.168.2.0/24]
```

### **Route Statistics**
```bash
# Route statistics
/ip route print stats-only

# Interface statistics
/interface print stats-only

# Traffic statistics
/interface monitor-traffic ether1
```

---

## 🎯 Common Use Cases

### **Scenario 1: Add Default Route**
```bash
# Add default route to internet
/ip route add dst-address=0.0.0.0/0 gateway=192.168.1.1 comment="Internet Default"
```

### **Scenario 2: Add Backup Route**
```bash
# Primary route
/ip route add dst-address=192.168.2.0/24 gateway=192.168.1.1 distance=1

# Backup route
/ip route add dst-address=192.168.2.0/24 gateway=192.168.1.2 distance=10
```

### **Scenario 3: Load Balancing**
```bash
# Equal-cost routes
/ip route add dst-address=192.168.2.0/24 gateway=192.168.1.1 distance=1
/ip route add dst-address=192.168.2.0/24 gateway=192.168.1.2 distance=1
```

### **Scenario 4: Route Summarization**
```bash
# Summary route
/ip route add dst-address=192.168.0.0/16 gateway=192.168.1.1 comment="Summary Route"
```

---

## ✅ Best Practices

### **Command Organization**
- Use comments for route documentation
- Group related routes together
- Use consistent naming conventions
- Regular route table cleanup

### **Troubleshooting**
- Always verify gateway reachability
- Check interface status before adding routes
- Use route monitoring for troubleshooting
- Document route changes

### **Security**
- Limit route modification access
- Use route filters where appropriate
- Monitor route changes
- Backup route configurations

---

## 📚 Additional Resources

### **Related Commands**
- Interface configuration: `/interface`
- IP addressing: `/ip address`
- Firewall rules: `/ip firewall`
- NAT rules: `/ip firewall nat`

### **Documentation**
- RouterOS Manual: https://help.mikrotik.com/
- Routing Guide: https://wiki.mikrotik.com/
- Community Forum: https://forum.mikrotik.com/ 