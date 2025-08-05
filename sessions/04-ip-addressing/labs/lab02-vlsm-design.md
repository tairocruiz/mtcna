# Lab 02: VLSM Design

## 🎯 Objective
Learn to design and implement Variable Length Subnet Masking (VLSM) schemes for complex network requirements. Develop skills in efficient IP address allocation and hierarchical network design.

## 🛠️ Prerequisites
- Understanding of basic subnetting concepts
- Knowledge of binary and decimal conversion
- Familiarity with CIDR notation
- Calculator and subnetting tools

## 📋 Lab Overview
This lab will help you:
1. Design VLSM schemes for complex network requirements
2. Implement hierarchical addressing plans
3. Optimize IP address allocation
4. Create route summarization strategies
5. Document network addressing schemes

---

## Part 1: VLSM Design Fundamentals

### Step 1: VLSM Planning Process
**Understand the systematic approach to VLSM design:**

#### **Design Steps**
```
1. Requirements Analysis:
   - Identify all network segments
   - Determine host requirements
   - Consider growth factors
   - Plan for future expansion

2. Network Hierarchy:
   - Define network layers
   - Establish addressing hierarchy
   - Plan route summarization points
   - Design security boundaries

3. Subnet Allocation:
   - Sort requirements by size
   - Allocate largest subnets first
   - Use smallest possible masks
   - Avoid address waste

4. Documentation:
   - Create addressing plan
   - Document subnet assignments
   - Plan for management
   - Establish naming conventions
```

#### **VLSM Best Practices**
```
Efficiency Principles:
- Start with largest subnets
- Use smallest possible masks
- Plan for growth
- Document everything

Hierarchical Design:
- Geographic hierarchy
- Functional hierarchy
- Security hierarchy
- Management hierarchy

Addressing Strategy:
- Consistent numbering
- Logical grouping
- Easy summarization
- Clear documentation
```

### Step 2: Requirements Analysis
**Practice analyzing network requirements:**

#### **Exercise 1: Small Enterprise Requirements**
```
Analyze the following requirements:

Company: TechCorp
Network: 192.168.0.0/16

Departments:
- IT Department: 100 hosts
- Sales Department: 50 hosts
- Marketing Department: 25 hosts
- HR Department: 15 hosts
- Finance Department: 20 hosts

Infrastructure:
- Server Farm: 200 hosts
- Management Network: 10 hosts
- Guest Network: 30 hosts
- Point-to-Point Links: 5 links (2 hosts each)

Growth Plan:
- 20% growth per year
- New branch office in 2 years
- Additional departments planned
```

#### **Exercise 2: Large Enterprise Requirements**
```
Analyze the following requirements:

Company: GlobalCorp
Network: 10.0.0.0/8

Headquarters:
- Main Building: 500 hosts
- Data Center: 1000 hosts
- Management: 50 hosts

Regional Offices (5 locations):
- Each office: 200 hosts
- Each management: 10 hosts

Branch Offices (20 locations):
- Each branch: 50 hosts
- Each management: 5 hosts

Infrastructure:
- WAN Links: 30 point-to-point links
- DMZ Networks: 10 networks (20 hosts each)
- Backup Networks: 5 networks (100 hosts each)

Future Plans:
- 10 new branch offices
- Cloud migration
- IoT expansion
```

---

## Part 2: Hierarchical Addressing Design

### Step 1: Network Hierarchy Planning
**Design hierarchical addressing schemes:**

#### **Exercise 3: Geographic Hierarchy**
```
Design a geographic hierarchy for GlobalCorp:

Level 1: Continent
- North America: 10.1.0.0/16
- Europe: 10.2.0.0/16
- Asia: 10.3.0.0/16

Level 2: Country
- North America - USA: 10.1.0.0/20
- North America - Canada: 10.1.16.0/20

Level 3: Region
- USA - East: 10.1.0.0/22
- USA - West: 10.1.4.0/22
- USA - Central: 10.1.8.0/22

Level 4: City/Location
- East - NYC: 10.1.0.0/24
- East - Boston: 10.1.1.0/24
- West - LA: 10.1.4.0/24
- West - Seattle: 10.1.5.0/24
```

#### **Exercise 4: Functional Hierarchy**
```
Design a functional hierarchy for TechCorp:

Level 1: Network Type
- Production: 192.168.0.0/17
- Management: 192.168.128.0/18
- Infrastructure: 192.168.192.0/18

Level 2: Security Zone
- Production - Trusted: 192.168.0.0/18
- Production - DMZ: 192.168.64.0/18
- Management - Admin: 192.168.128.0/19
- Management - Monitoring: 192.168.160.0/19

Level 3: Department/Function
- Trusted - IT: 192.168.0.0/20
- Trusted - Sales: 192.168.16.0/20
- Trusted - Marketing: 192.168.32.0/20
- DMZ - Web: 192.168.64.0/20
- DMZ - Email: 192.168.80.0/20
```

### Step 2: Address Allocation Strategy
**Plan efficient address allocation:**

#### **Exercise 5: Allocation Planning**
```
Plan address allocation for TechCorp:

Phase 1: Current Requirements
- Allocate subnets for current needs
- Reserve space for growth
- Plan for future expansion

Phase 2: Growth Planning
- Identify growth areas
- Reserve address blocks
- Plan for new locations

Phase 3: Optimization
- Review allocation efficiency
- Consolidate if possible
- Plan for renumbering if needed
```

---

## Part 3: VLSM Implementation

### Step 1: Small Enterprise VLSM
**Implement VLSM for TechCorp:**

#### **Exercise 6: TechCorp VLSM Design**
```
Design VLSM scheme for TechCorp (192.168.0.0/16):

Large Subnets (Allocate First):
- Server Farm (200 hosts): ________
- IT Department (100 hosts): ________

Medium Subnets:
- Sales Department (50 hosts): ________
- Guest Network (30 hosts): ________
- Finance Department (20 hosts): ________

Small Subnets:
- Marketing Department (25 hosts): ________
- HR Department (15 hosts): ________
- Management Network (10 hosts): ________

Point-to-Point Links:
- P2P Link 1: ________
- P2P Link 2: ________
- P2P Link 3: ________
- P2P Link 4: ________
- P2P Link 5: ________

Reserved Space:
- Future Growth: ________
- New Departments: ________
- Additional Infrastructure: ________
```

### Step 2: Large Enterprise VLSM
**Implement VLSM for GlobalCorp:**

#### **Exercise 7: GlobalCorp VLSM Design**
```
Design VLSM scheme for GlobalCorp (10.0.0.0/8):

Headquarters:
- Data Center (1000 hosts): ________
- Main Building (500 hosts): ________
- Management (50 hosts): ________

Regional Offices (5 locations):
- Regional 1 (200 hosts): ________
- Regional 2 (200 hosts): ________
- Regional 3 (200 hosts): ________
- Regional 4 (200 hosts): ________
- Regional 5 (200 hosts): ________

Branch Offices (20 locations):
- Branch 1-20 (50 hosts each): ________
- (List all 20 subnets)

Infrastructure:
- WAN Links (30 P2P): ________
- DMZ Networks (10 networks): ________
- Backup Networks (5 networks): ________

Reserved Space:
- Future Growth: ________
- New Locations: ________
- Cloud Migration: ________
```

---

## Part 4: Route Summarization

### Step 1: Basic Route Summarization
**Practice route summarization techniques:**

#### **Exercise 8: Simple Summarization**
```
Summarize the following routes:

Routes:
- 192.168.1.0/24
- 192.168.2.0/24
- 192.168.3.0/24
- 192.168.4.0/24

Summary Route: ________
```

#### **Exercise 9: Complex Summarization**
```
Summarize the following routes:

Routes:
- 10.1.0.0/24
- 10.1.1.0/24
- 10.1.2.0/24
- 10.1.3.0/24
- 10.1.4.0/24
- 10.1.5.0/24
- 10.1.6.0/24
- 10.1.7.0/24
- 10.1.8.0/24
- 10.1.9.0/24
- 10.1.10.0/24
- 10.1.11.0/24
- 10.1.12.0/24
- 10.1.13.0/24
- 10.1.14.0/24
- 10.1.15.0/24

Summary Route: ________
```

### Step 2: Hierarchical Summarization
**Design hierarchical route summarization:**

#### **Exercise 10: Geographic Summarization**
```
Design route summarization for GlobalCorp:

North America Routes:
- 10.1.0.0/24 (NYC)
- 10.1.1.0/24 (Boston)
- 10.1.4.0/24 (LA)
- 10.1.5.0/24 (Seattle)

North America Summary: ________

Europe Routes:
- 10.2.0.0/24 (London)
- 10.2.1.0/24 (Paris)
- 10.2.2.0/24 (Berlin)

Europe Summary: ________

Asia Routes:
- 10.3.0.0/24 (Tokyo)
- 10.3.1.0/24 (Singapore)
- 10.3.2.0/24 (Sydney)

Asia Summary: ________

Global Summary: ________
```

---

## Part 5: Advanced VLSM Scenarios

### Step 1: Multi-Tier Network Design
**Design complex multi-tier networks:**

#### **Scenario 1: Data Center Design**
```
Design VLSM for a data center:

Network: 172.16.0.0/16

Requirements:
- Web Servers: 500 hosts
- Application Servers: 300 hosts
- Database Servers: 200 hosts
- Storage Network: 100 hosts
- Management Network: 50 hosts
- Backup Network: 100 hosts
- DMZ: 50 hosts
- Load Balancers: 20 hosts
- Monitoring: 10 hosts
- Point-to-Point Links: 10 links

Design your VLSM scheme:

Large Subnets:
- Web Servers: ________
- Application Servers: ________
- Database Servers: ________

Medium Subnets:
- Storage Network: ________
- Backup Network: ________
- DMZ: ________

Small Subnets:
- Management Network: ________
- Load Balancers: ________
- Monitoring: ________

P2P Links: ________
```

#### **Scenario 2: Campus Network Design**
```
Design VLSM for a university campus:

Network: 10.0.0.0/8

Requirements:
- Student Housing: 2000 hosts
- Academic Buildings: 1000 hosts
- Library: 500 hosts
- Administration: 200 hosts
- Research Labs: 300 hosts
- Guest Network: 100 hosts
- Faculty Housing: 500 hosts
- Sports Complex: 200 hosts
- Medical Center: 300 hosts
- Parking/Transportation: 100 hosts

Design your VLSM scheme:

Very Large Subnets:
- Student Housing: ________

Large Subnets:
- Academic Buildings: ________
- Library: ________
- Faculty Housing: ________

Medium Subnets:
- Research Labs: ________
- Medical Center: ________
- Sports Complex: ________

Small Subnets:
- Administration: ________
- Guest Network: ________
- Parking/Transportation: ________
```

### Step 2: Growth Planning
**Plan for network growth and expansion:**

#### **Exercise 11: Growth Planning**
```
Plan for TechCorp growth:

Current State:
- 5 departments
- 1 server farm
- 5 P2P links

Growth Plan (3 years):
- 3 new departments (30 hosts each)
- 1 new branch office (100 hosts)
- 2 new server farms (200 hosts each)
- 10 additional P2P links
- Cloud migration (reserve space)

Reserved Address Blocks:
- New Departments: ________
- Branch Office: ________
- Server Farms: ________
- P2P Links: ________
- Cloud Migration: ________
- Future Expansion: ________
```

---

## Part 6: Documentation and Management

### Step 1: Addressing Documentation
**Create comprehensive addressing documentation:**

#### **Exercise 12: Documentation Template**
```
Create addressing documentation for TechCorp:

Network Overview:
- Total Network: ________
- Total Subnets: ________
- Total Hosts: ________
- Utilization: ________%

Subnet Assignments:
- Server Farm: ________ (200 hosts)
- IT Department: ________ (100 hosts)
- Sales Department: ________ (50 hosts)
- Marketing Department: ________ (25 hosts)
- HR Department: ________ (15 hosts)
- Finance Department: ________ (20 hosts)
- Guest Network: ________ (30 hosts)
- Management Network: ________ (10 hosts)

Infrastructure:
- P2P Link 1: ________ (2 hosts)
- P2P Link 2: ________ (2 hosts)
- P2P Link 3: ________ (2 hosts)
- P2P Link 4: ________ (2 hosts)
- P2P Link 5: ________ (2 hosts)

Reserved Space:
- Future Growth: ________
- New Departments: ________
- Additional Infrastructure: ________
```

### Step 2: Management Strategy
**Plan for ongoing management:**

#### **Exercise 13: Management Plan**
```
Create a management plan for the addressing scheme:

Monitoring:
- Address utilization tracking
- Subnet availability monitoring
- Growth trend analysis
- Performance monitoring

Maintenance:
- Regular address audits
- Subnet consolidation opportunities
- Documentation updates
- Policy reviews

Expansion:
- Growth forecasting
- Address block reservations
- Migration planning
- Renumbering strategies
```

---

## 📊 Lab Results Template

Fill out this template with your findings:

```
=== VLSM DESIGN LAB ===

Date: ________
Student: ________

Part 1: VLSM Planning
- Requirements Analysis: ________
- Hierarchy Design: ________
- Allocation Strategy: ________

Part 2: Hierarchical Addressing
- Geographic Hierarchy: ________
- Functional Hierarchy: ________
- Security Hierarchy: ________

Part 3: VLSM Implementation
- Small Enterprise Design: ________
- Large Enterprise Design: ________
- Address Efficiency: ________%

Part 4: Route Summarization
- Basic Summarization: ________
- Complex Summarization: ________
- Hierarchical Summarization: ________

Part 5: Advanced Scenarios
- Data Center Design: ________
- Campus Network Design: ________
- Growth Planning: ________

Part 6: Documentation
- Addressing Documentation: ________
- Management Strategy: ________
- Overall Design Quality: ________
```

---

## 🔍 Analysis Questions

1. **VLSM Efficiency:** How did VLSM improve address utilization compared to fixed-length subnetting?

2. **Hierarchical Design:** What benefits did hierarchical addressing provide in your designs?

3. **Route Summarization:** How did route summarization improve network performance and management?

4. **Growth Planning:** How did you accommodate future growth in your VLSM designs?

5. **Documentation:** What elements are essential in addressing documentation for network management?

---

## 🎓 Learning Outcomes

After completing this lab, you should understand:
- VLSM design principles and methodologies
- Hierarchical addressing strategies
- Route summarization techniques
- Growth planning and address reservation
- Network documentation and management
- Complex network design scenarios

---

## 🛠️ Recommended Tools

### **Design Tools:**
- **Network Design Software:** Professional tools
- **Spreadsheet Software:** Excel/Google Sheets
- **Subnet Calculators:** Online tools
- **Network Simulators:** Practice environments

### **Documentation Tools:**
- **Network Diagram Software:** Visio, Draw.io
- **Documentation Platforms:** Wiki, SharePoint
- **Version Control:** Git for configuration management
- **Project Management:** Planning and tracking

### **Management Tools:**
- **IP Address Management:** IPAM tools
- **Network Monitoring:** Performance tracking
- **Configuration Management:** Device management
- **Audit Tools:** Address utilization tracking

---

## ⚠️ Important Notes

### **Best Practices:**
- **Plan for growth** from the beginning
- **Document everything** thoroughly
- **Use consistent naming** conventions
- **Implement security** boundaries
- **Monitor and maintain** regularly

### **Common Pitfalls:**
- **Insufficient growth planning** leading to renumbering
- **Poor documentation** making management difficult
- **Inefficient allocation** wasting address space
- **Complex summarization** affecting routing
- **Security boundary confusion** in design

---

**Next Session:** [Session 05: Routing Fundamentals](../05-routing-basics/) 