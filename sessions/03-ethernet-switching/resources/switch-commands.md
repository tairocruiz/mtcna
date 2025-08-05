# Switch Commands Cheat Sheet

## 🎯 Overview
This cheat sheet provides quick reference for common switch configuration and troubleshooting commands across different vendor platforms.

## 📋 Basic Commands

### **Access and Navigation**
```
Enter Privileged Mode:
- Cisco: enable
- HP: enable
- Dell: enable
- MikroTik: /system login

Enter Configuration Mode:
- Cisco: configure terminal
- HP: configure terminal
- Dell: configure terminal
- MikroTik: /interface ethernet

Exit Commands:
- exit: Exit current mode
- end: Exit to privileged mode
- quit: Exit completely
```

### **Help and Information**
```
Show Help:
- Cisco: help, ?
- HP: help, ?
- Dell: help, ?
- MikroTik: /help

Show Version:
- Cisco: show version
- HP: show version
- Dell: show version
- MikroTik: /system resource print

Show Running Config:
- Cisco: show running-config
- HP: show running-config
- Dell: show running-config
- MikroTik: /export
```

---

## 🔧 Interface Configuration

### **Interface Access**
```
Enter Interface Mode:
- Cisco: interface [type] [number]
- HP: interface [type] [number]
- Dell: interface [type] [number]
- MikroTik: /interface ethernet [number]

Examples:
- interface FastEthernet0/1
- interface GigabitEthernet0/1
- interface ethernet 1
```

### **Basic Interface Settings**
```
Speed Configuration:
- Cisco: speed [10|100|1000|auto]
- HP: speed [10|100|1000|auto]
- Dell: speed [10|100|1000|auto]
- MikroTik: speed [10M|100M|1G|auto]

Duplex Configuration:
- Cisco: duplex [half|full|auto]
- HP: duplex [half|full|auto]
- Dell: duplex [half|full|auto]
- MikroTik: auto-negotiation [yes|no]

Interface Description:
- Cisco: description [text]
- HP: description [text]
- Dell: description [text]
- MikroTik: comment [text]

Enable/Disable Interface:
- Cisco: no shutdown / shutdown
- HP: no shutdown / shutdown
- Dell: no shutdown / shutdown
- MikroTik: disable / enable
```

### **Interface Verification**
```
Show Interface Status:
- Cisco: show interface [interface]
- HP: show interface [interface]
- Dell: show interface [interface]
- MikroTik: /interface ethernet print

Show Interface Brief:
- Cisco: show interface brief
- HP: show interface brief
- Dell: show interface brief
- MikroTik: /interface print

Show Interface Counters:
- Cisco: show interface [interface] counters
- HP: show interface [interface] counters
- Dell: show interface [interface] counters
- MikroTik: /interface ethernet monitor [number]
```

---

## 🌐 VLAN Configuration

### **VLAN Creation**
```
Create VLAN:
- Cisco: vlan [number]
- HP: vlan [number]
- Dell: vlan [number]
- MikroTik: /interface vlan add name=[name] vlan-id=[number]

VLAN Name:
- Cisco: name [name]
- HP: name [name]
- Dell: name [name]
- MikroTik: name=[name] (in creation command)
```

### **Port VLAN Assignment**
```
Access Port Configuration:
- Cisco: switchport mode access
- HP: switchport mode access
- Dell: switchport mode access
- MikroTik: /interface ethernet switch port-mode=access

Access VLAN Assignment:
- Cisco: switchport access vlan [number]
- HP: switchport access vlan [number]
- Dell: switchport access vlan [number]
- MikroTik: /interface ethernet switch vlan-mode=access vlan-id=[number]

Trunk Port Configuration:
- Cisco: switchport mode trunk
- HP: switchport mode trunk
- Dell: switchport mode trunk
- MikroTik: /interface ethernet switch port-mode=trunk

Trunk Allowed VLANs:
- Cisco: switchport trunk allowed vlan [list]
- HP: switchport trunk allowed vlan [list]
- Dell: switchport trunk allowed vlan [list]
- MikroTik: /interface ethernet switch vlan-trunk=[list]
```

### **VLAN Verification**
```
Show VLANs:
- Cisco: show vlan
- HP: show vlan
- Dell: show vlan
- MikroTik: /interface vlan print

Show VLAN Brief:
- Cisco: show vlan brief
- HP: show vlan brief
- Dell: show vlan brief
- MikroTik: /interface vlan print brief

Show Interface Switchport:
- Cisco: show interface [interface] switchport
- HP: show interface [interface] switchport
- Dell: show interface [interface] switchport
- MikroTik: /interface ethernet switch print
```

---

## 🔒 Security Configuration

### **Port Security**
```
Enable Port Security:
- Cisco: switchport port-security
- HP: port-security
- Dell: port-security
- MikroTik: /interface ethernet switch port-security=yes

Maximum MAC Addresses:
- Cisco: switchport port-security maximum [number]
- HP: port-security max-mac-count [number]
- Dell: port-security max-mac-count [number]
- MikroTik: /interface ethernet switch port-security-max-addresses=[number]

Violation Action:
- Cisco: switchport port-security violation [shutdown|restrict|protect]
- HP: port-security violation [shutdown|restrict|protect]
- Dell: port-security violation [shutdown|restrict|protect]
- MikroTik: /interface ethernet switch port-security-mode=[mode]
```

### **Access Control Lists**
```
Create ACL:
- Cisco: access-list [number] [permit|deny] [source] [destination]
- HP: access-list [number] [permit|deny] [source] [destination]
- Dell: access-list [number] [permit|deny] [source] [destination]
- MikroTik: /ip firewall filter add chain=[chain] src-address=[address] action=[action]

Apply ACL to Interface:
- Cisco: ip access-group [number] [in|out]
- HP: ip access-group [number] [in|out]
- Dell: ip access-group [number] [in|out]
- MikroTik: /ip firewall filter add chain=[chain] in-interface=[interface] action=[action]
```

### **User Management**
```
Create User:
- Cisco: username [name] privilege [level] secret [password]
- HP: username [name] privilege [level] secret [password]
- Dell: username [name] privilege [level] secret [password]
- MikroTik: /user add name=[name] password=[password] group=[group]

Set Enable Password:
- Cisco: enable secret [password]
- HP: enable secret [password]
- Dell: enable secret [password]
- MikroTik: /user set [number] password=[password]
```

---

## 🔍 Monitoring and Troubleshooting

### **System Information**
```
Show System Resources:
- Cisco: show processes cpu
- HP: show system resources
- Dell: show system resources
- MikroTik: /system resource print

Show Memory:
- Cisco: show memory statistics
- HP: show memory
- Dell: show memory
- MikroTik: /system resource print

Show Environment:
- Cisco: show environment
- HP: show environment
- Dell: show environment
- MikroTik: /system health print
```

### **Network Information**
```
Show ARP Table:
- Cisco: show arp
- HP: show arp
- Dell: show arp
- MikroTik: /ip arp print

Show MAC Address Table:
- Cisco: show mac address-table
- HP: show mac-address-table
- Dell: show mac-address-table
- MikroTik: /interface ethernet switch host print

Show IP Interface:
- Cisco: show ip interface brief
- HP: show ip interface brief
- Dell: show ip interface brief
- MikroTik: /ip address print
```

### **Connectivity Testing**
```
Ping:
- Cisco: ping [address]
- HP: ping [address]
- Dell: ping [address]
- MikroTik: /ping [address]

Traceroute:
- Cisco: traceroute [address]
- HP: traceroute [address]
- Dell: traceroute [address]
- MikroTik: /tool traceroute [address]

Telnet/SSH:
- Cisco: telnet [address] / ssh [address]
- HP: telnet [address] / ssh [address]
- Dell: telnet [address] / ssh [address]
- MikroTik: /tool telnet [address] / /tool ssh [address]
```

---

## 💾 Configuration Management

### **Configuration Backup**
```
Save Configuration:
- Cisco: copy running-config startup-config
- HP: write memory
- Dell: copy running-config startup-config
- MikroTik: /system backup save

Backup to TFTP:
- Cisco: copy running-config tftp://[server]/[file]
- HP: copy running-config tftp://[server]/[file]
- Dell: copy running-config tftp://[server]/[file]
- MikroTik: /export file=[filename]

Backup to Flash:
- Cisco: copy running-config flash:[file]
- HP: copy running-config flash:[file]
- Dell: copy running-config flash:[file]
- MikroTik: /export file=[filename]
```

### **Configuration Restoration**
```
Restore from Saved:
- Cisco: copy startup-config running-config
- HP: copy startup-config running-config
- Dell: copy startup-config running-config
- MikroTik: /import [filename]

Restore from TFTP:
- Cisco: copy tftp://[server]/[file] running-config
- HP: copy tftp://[server]/[file] running-config
- Dell: copy tftp://[server]/[file] running-config
- MikroTik: /import [filename]
```

### **Configuration Verification**
```
Show Startup Config:
- Cisco: show startup-config
- HP: show startup-config
- Dell: show startup-config
- MikroTik: /export

Show Running Config:
- Cisco: show running-config
- HP: show running-config
- Dell: show running-config
- MikroTik: /export

Compare Configurations:
- Cisco: show archive config differences
- HP: show config differences
- Dell: show config differences
- MikroTik: /export compare
```

---

## 🔧 Advanced Features

### **Spanning Tree Protocol**
```
Show Spanning Tree:
- Cisco: show spanning-tree
- HP: show spanning-tree
- Dell: show spanning-tree
- MikroTik: /interface ethernet switch spanning-tree print

Configure STP:
- Cisco: spanning-tree mode [mode]
- HP: spanning-tree mode [mode]
- Dell: spanning-tree mode [mode]
- MikroTik: /interface ethernet switch spanning-tree mode=[mode]
```

### **Link Aggregation**
```
Create Port Channel:
- Cisco: interface port-channel [number]
- HP: interface port-channel [number]
- Dell: interface port-channel [number]
- MikroTik: /interface bonding add name=[name]

Add Ports to Channel:
- Cisco: channel-group [number] mode [active|passive]
- HP: channel-group [number] mode [active|passive]
- Dell: channel-group [number] mode [active|passive]
- MikroTik: /interface bonding add slave=[interface]
```

### **Quality of Service**
```
Configure QoS:
- Cisco: class-map [name]
- HP: qos policy [name]
- Dell: qos policy [name]
- MikroTik: /queue simple add name=[name]

Apply QoS:
- Cisco: service-policy [name] [in|out]
- HP: qos policy [name] [in|out]
- Dell: qos policy [name] [in|out]
- MikroTik: /queue simple add interface=[interface]
```

---

## 📊 Logging and Debugging

### **Logging Configuration**
```
Enable Logging:
- Cisco: logging [address]
- HP: logging [address]
- Dell: logging [address]
- MikroTik: /system logging add action=remote remote=[address]

Show Logs:
- Cisco: show logging
- HP: show logging
- Dell: show logging
- MikroTik: /log print
```

### **Debug Commands**
```
Enable Debug:
- Cisco: debug [feature]
- HP: debug [feature]
- Dell: debug [feature]
- MikroTik: /tool sniffer start

Disable Debug:
- Cisco: no debug all
- HP: no debug all
- Dell: no debug all
- MikroTik: /tool sniffer stop
```

---

## ⚠️ Important Notes

### **Best Practices:**
- **Always backup** configuration before changes
- **Test commands** in non-production first
- **Document changes** thoroughly
- **Use descriptive names** for interfaces and VLANs
- **Monitor system resources** during configuration

### **Safety Commands:**
- **Reload:** Restart switch (use carefully)
- **Clear counters:** Reset interface statistics
- **Clear mac address-table:** Clear MAC address table
- **Clear arp-cache:** Clear ARP cache

### **Recovery Commands:**
- **Reload:** Restart switch
- **Copy startup-config running-config:** Restore saved config
- **Default interface:** Reset interface to defaults
- **No shutdown:** Enable interface

---

## 📚 Additional Resources

### **Vendor Documentation:**
- **Cisco:** Cisco IOS Configuration Guides
- **HP:** HP Switch Configuration Guides
- **Dell:** Dell Switch Configuration Guides
- **MikroTik:** MikroTik RouterOS Manual

### **Online Resources:**
- **Vendor Support:** Official support websites
- **Community Forums:** User communities
- **Configuration Examples:** Sample configurations
- **Troubleshooting Guides:** Common issues and solutions

---

**Note:** Commands may vary slightly between different versions and models of switches. Always refer to the specific device documentation for exact syntax. 