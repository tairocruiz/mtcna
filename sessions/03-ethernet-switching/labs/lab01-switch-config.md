# Lab 01: Switch Configuration

## 🎯 Objective
Learn to configure and manage network switches using MikroTik RouterOS. Develop skills in basic switch configuration, interface management, and switch operation verification.

## 🛠️ Prerequisites
- Access to a MikroTik switch or router with RouterOS
- Console cable or network access to device
- Basic command line knowledge
- Understanding of Ethernet fundamentals
- RouterOS documentation (if available)

## 📋 Lab Overview
This lab will help you:
1. Access and configure a MikroTik switch/router
2. Configure switch interfaces and settings
3. Manage switch security features
4. Monitor switch operation and performance
5. Troubleshoot basic switch issues

---

## Part 1: Switch Access and Initial Configuration

### Step 1: Physical Connection
**Connect to the switch using console or network access:**

#### **Console Connection**
```
Equipment Needed:
- Console cable (RJ-45 to DB-9 or USB)
- Terminal emulation software
- Switch power supply

Connection Steps:
1. Connect console cable to switch console port
2. Connect other end to computer serial/USB port
3. Open terminal emulation software
4. Configure terminal settings:
   - Baud Rate: 115200
   - Data Bits: 8
   - Parity: None
   - Stop Bits: 1
   - Flow Control: None
```

#### **Network Access**
```
Equipment Needed:
- Network cable
- Switch IP address
- SSH/Telnet client or WinBox

Connection Steps:
1. Connect network cable to switch management port
2. Configure computer IP address in same subnet
3. Open SSH/Telnet client or WinBox
4. Connect to switch IP address
```

### Step 2: Initial Switch Access
**Access the switch command line interface:**

#### **Default Access**
```
Username: admin
Password: (blank)
Default IP: 192.168.88.1 (varies by model)

RouterOS Default Credentials:
- Username: admin
- Password: (blank)
- IP Address: 192.168.88.1
- MAC Address: Check device label
```

#### **Access Verification**
```
Commands to verify access:
- /system resource print: Display system information
- /interface print: Display interface status
- /export: Display current configuration
- /system identity print: Display device identity
```

### Step 3: Basic Switch Configuration
**Configure essential switch settings:**

#### **Device Identity Configuration**
```
Command: /system identity set name=[DEVICE_NAME]
Example: /system identity set name=LAB-SWITCH-01

Purpose: Identify switch in network
Verification: /system identity print
```

#### **Management IP Configuration**
```
Commands:
/ip address add address=192.168.88.10/24 interface=ether1
/interface ethernet enable ether1

Purpose: Enable network management
Verification: /ip address print
```

#### **Default Gateway Configuration**
```
Command: /ip route add gateway=192.168.88.1

Purpose: Enable management from other networks
Verification: /ip route print
```

---

## Part 2: Interface Configuration

### Step 1: Interface Status Verification
**Check current interface status:**

#### **Interface Status Commands**
```
/interface print: Detailed interface information
/interface print brief: Summary interface status
/interface ethernet print: Ethernet interface status
/interface ethernet monitor [number|name]: Interface statistics
```

#### **Interface Status Indicators**
```
Status Indicators:
- Running: Interface is operational
- No Link: Physical down
- Disabled: Manually disabled
- Unknown: Interface not recognized
```

### Step 2: Interface Configuration
**Configure switch interfaces:**

#### **Basic Interface Settings**
```
Commands:
/interface ethernet set [number|name] name=[NAME]
/interface ethernet set [number|name] comment=[DESCRIPTION]
/interface ethernet set [number|name] speed=[10M|100M|1G|auto]
/interface ethernet enable [number|name]

Example:
/interface ethernet set 1 name=PC-01
/interface ethernet set 1 comment=Sales-PC-01
/interface ethernet set 1 speed=auto
/interface ethernet enable 1
```

#### **Interface Configuration Verification**
```
Commands:
/interface ethernet print: Detailed interface info
/interface ethernet print brief: Interface status
/interface ethernet monitor [number|name]: Interface statistics
```

### Step 3: Interface Security
**Configure interface security features:**

#### **Port Security Configuration**
```
Commands:
/interface ethernet switch port-security=yes
/interface ethernet switch port-security-max-addresses=[number|name]
/interface ethernet switch port-security-mode=[shutdown|restrict|protect]

Example:
/interface ethernet switch port-security=yes
/interface ethernet switch port-security-max-addresses=1
/interface ethernet switch port-security-mode=shutdown
```

#### **Port Security Verification**
```
Commands:
/interface ethernet switch print: Port security status
/interface ethernet switch host print: MAC addresses
/interface ethernet switch print detail: Interface details
```

---

## Part 3: VLAN Configuration

### Step 1: VLAN Creation
**Create and configure VLANs:**

#### **VLAN Creation Commands**
```
Commands:
/interface vlan add name=[VLAN_NAME] vlan-id=[VLAN_ID]

Example:
/interface vlan add name=SALES vlan-id=10
/interface vlan add name=ENGINEERING vlan-id=20
/interface vlan add name=GUEST vlan-id=30
```

#### **VLAN Verification**
```
Commands:
/interface vlan print: Display all VLANs
/interface vlan print brief: Summary VLAN information
/interface vlan print detail: Specific VLAN details
```

### Step 2: Port VLAN Assignment
**Assign ports to VLANs:**

#### **Access Port Configuration**
```
Commands:
/interface ethernet switch vlan-mode=access
/interface ethernet switch vlan-id=[VLAN_ID]

Example:
/interface ethernet switch set 1 vlan-mode=access
/interface ethernet switch set 1 vlan-id=10
```

#### **Trunk Port Configuration**
```
Commands:
/interface ethernet switch vlan-mode=trunk
/interface ethernet switch vlan-trunk=[VLAN_LIST]

Example:
/interface ethernet switch set 24 vlan-mode=trunk
/interface ethernet switch set 24 vlan-trunk=10,20,30
```

### Step 3: VLAN Verification
**Verify VLAN configuration:**

#### **VLAN Status Commands**
```
Commands:
/interface vlan print: All VLANs and ports
/interface ethernet switch print: Trunk port information
/interface ethernet switch print detail: Port VLAN info
```

---

## Part 4: Switch Security Configuration

### Step 1: User Account Management
**Configure user accounts and passwords:**

#### **User Account Creation**
```
Commands:
/user add name=[USERNAME] password=[PASSWORD] group=[GROUP]

Example:
/user add name=admin password=Admin123! group=full
/user add name=operator password=Operator123! group=read
```

#### **Password Configuration**
```
Commands:
/user set [number|name] password=[PASSWORD]: User password
/user group print: Display user groups
/user print: Display all users
```

### Step 2: SSH Configuration
**Enable secure shell access:**

#### **SSH Setup**
```
Commands:
/ip ssh set always-allow-password-login=yes
/ip service enable ssh
/user add name=[USERNAME] password=[PASSWORD] group=full
```

#### **SSH Verification**
```
Commands:
/ip service print: SSH status
/ip ssh print: SSH configuration
```

### Step 3: Access Control Lists
**Configure basic access control:**

#### **Management ACL**
```
Commands:
/ip firewall filter add chain=input src-address=192.168.88.0/24 action=accept
/ip firewall filter add chain=input action=drop

Example:
/ip firewall filter add chain=input src-address=192.168.88.0/24 action=accept
/ip firewall filter add chain=input action=drop
```

---

## Part 5: Switch Monitoring and Management

### Step 1: System Monitoring
**Monitor switch system status:**

#### **System Status Commands**
```
Commands:
/system resource print: Switch hardware and software info
/export: Current configuration
/system identity print: Device identity
/system clock print: System time
/log print: System log messages
```

#### **Resource Monitoring**
```
Commands:
/system resource print: CPU and memory usage
/system health print: Environmental conditions
/system resource cpu print: CPU utilization
/system resource memory print: Memory usage
```

### Step 2: Interface Monitoring
**Monitor interface performance:**

#### **Interface Statistics**
```
Commands:
/interface print: Detailed interface statistics
/interface ethernet monitor [number|name]: Interface counters
/interface ethernet monitor [number|name] once: Single reading
/interface print brief: Interface status summary
```

#### **Performance Metrics**
```
Key Metrics:
- Input/Output packets
- Input/Output bytes
- Error counters
- Interface utilization
```

### Step 3: Network Monitoring
**Monitor network connectivity:**

#### **Connectivity Testing**
```
Commands:
/ping [IP_ADDRESS]: Test connectivity
/tool traceroute [IP_ADDRESS]: Path analysis
/ip arp print: ARP table
/interface ethernet switch host print: MAC address table
```

---

## Part 6: Configuration Management

### Step 1: Configuration Backup
**Backup switch configuration:**

#### **Configuration Backup Commands**
```
Commands:
/system backup save name=[BACKUP_NAME]: Save configuration
/export file=[FILENAME]: Export configuration
/system backup print: List backups
/system backup load name=[BACKUP_NAME]: Load backup
```

#### **Configuration Verification**
```
Commands:
/export: Current configuration
/system backup print: Saved backups
/system backup print detail: Backup details
```

### Step 2: Configuration Restoration
**Restore switch configuration:**

#### **Configuration Restoration**
```
Commands:
/system backup load name=[BACKUP_NAME]: Restore from backup
/import [FILENAME]: Import configuration
/system reset-configuration: Reset to defaults
```

### Step 3: Configuration Validation
**Validate configuration changes:**

#### **Configuration Testing**
```
Steps:
1. Test connectivity after changes
2. Verify VLAN assignments
3. Test security features
4. Monitor for errors
5. Document changes
```

---

## 📊 Lab Results Template

Fill out this template with your findings:

```
=== SWITCH CONFIGURATION LAB ===

Switch Model: ________
Switch Name: ________
Management IP: ________
Date: ________

Part 1: Basic Configuration
- Device Identity: ________
- Management IP: ________
- Default Gateway: ________
- Access Method: ________

Part 2: Interface Configuration
- Total Interfaces: ________
- Configured Interfaces: ________
- Interface Types: ________
- Security Features: ________

Part 3: VLAN Configuration
- VLANs Created: ________
- Access Ports: ________
- Trunk Ports: ________
- VLAN Names: ________

Part 4: Security Configuration
- User Accounts: ________
- SSH Status: ________
- Port Security: ________
- Access Control: ________

Part 5: Monitoring Results
- System Status: ________
- Interface Status: ________
- Error Counters: ________
- Performance Metrics: ________

Part 6: Configuration Management
- Backup Method: ________
- Configuration Status: ________
- Validation Results: ________
- Documentation: ________
```

---

## 🔍 Analysis Questions

1. **Interface Configuration:** How did you configure the switch interfaces for optimal performance?

2. **VLAN Design:** What VLAN structure did you implement and why?

3. **Security Implementation:** What security features did you enable and how do they protect the network?

4. **Monitoring Strategy:** How would you monitor this switch in a production environment?

5. **Troubleshooting Approach:** What steps would you take to troubleshoot connectivity issues?

---

## 🎓 Learning Outcomes

After completing this lab, you should understand:
- MikroTik RouterOS switch access and initial configuration
- Interface configuration and management
- VLAN creation and port assignment
- Switch security features and implementation
- Switch monitoring and troubleshooting
- Configuration backup and restoration

---

## ��️ Recommended Tools

### **Terminal Emulation:**
- **WinBox:** MikroTik GUI management tool
- **PuTTY:** Windows SSH/Telnet client
- **SecureCRT:** Professional terminal emulator
- **Tera Term:** Free terminal emulator

### **Network Tools:**
- **Wireshark:** Packet analysis
- **ping/traceroute:** Connectivity testing
- **telnet/ssh:** Remote access
- **TFTP Server:** Configuration backup

### **Documentation:**
- **RouterOS Manual:** Official MikroTik documentation
- **Configuration Templates:** Standard configurations
- **Network Diagrams:** Topology documentation
- **Change Log:** Configuration change tracking

---

## ⚠️ Important Notes

### **Best Practices:**
- **Document all changes** before making them
- **Test configurations** in non-production first
- **Backup configurations** before major changes
- **Use descriptive names** for interfaces and VLANs
- **Implement security** from the beginning

### **Safety Considerations:**
- **Console access** is critical for recovery
- **Configuration backups** prevent data loss
- **Security features** protect against unauthorized access
- **Monitoring** helps detect issues early
- **Documentation** aids troubleshooting

---

**Next Lab:** [Lab 02: VLAN Configuration](./lab02-vlan-config.md) 