# Enterprise Network using Cisco Packet Tracer

> A CCNA-level enterprise network project demonstrating secure inter-branch connectivity, dynamic routing, gateway redundancy, Layer 2 security, and centralized network management using Cisco enterprise technologies.

---

# 📌 Overview

This project simulates a secure enterprise network connecting a **Main Branch** and a **Branch Office** through an ISP using **GRE Tunnel**. The topology follows Cisco's **Hierarchical Network Design Model**, consisting of Core, Distribution, and Access Layers.

The network was built using **Cisco Packet Tracer** to demonstrate practical enterprise networking concepts, including routing, switching, redundancy, network security, and centralized management.

---

# 🎯 Objectives

* Build a scalable enterprise network.
* Provide secure communication between branches.
* Implement dynamic routing.
* Provide gateway redundancy.
* Secure Layer 2 infrastructure.
* Secure remote device management.
* Protect against common Layer 2 attacks.
* Implement Internet connectivity using PAT.
* Restrict management access using ACLs.
* Demonstrate enterprise troubleshooting.

---

# 🏗️ Network Topology

## Main Branch

* Cisco 2911 Router
* 2 × Cisco Catalyst 3560 Layer 3 Switches
* 4 × Cisco Catalyst 2960 Layer 2 Switches
* DHCP/DNS Server
* Internal Server
* Guest Wireless Access Point
* Management Switch
* HR VLAN
* Accounting VLAN
* IT VLAN

---

## Branch Office

* Cisco 2911 Router
* 2 × Cisco Catalyst 3560 Layer 3 Switches
* 4 × Cisco Catalyst 2960 Layer 2 Switches
* DHCP for the Branch
* Guest Wireless Access Point
* Management Switch
* HR VLAN
* Accounting VLAN
* IT VLAN

---

## WAN

* ISP Router
* GRE Tunnel
* OSPF Routing

---

# 🚀 Technologies Implemented

* ✅ VLAN Segmentation
* ✅ Inter-VLAN Routing
* ✅ GRE Tunnel
* ✅ OSPF
* ✅ HSRP
* ✅ Rapid PVST+
* ✅ Root Primary / Root Secondary
* ✅ PortFast
* ✅ BPDU Guard
* ✅ Port Security
* ✅ DHCP Snooping
* ✅ Dynamic ARP Inspection (DAI)
* ✅ ACL
* ✅ PAT
* ✅ SSH Version 2
* ✅ Guest Wireless VLAN
* ✅ VLAN 999 for Unused Ports

---

# 🌐 VLAN Design

| VLAN     | Department   |
| -------- | ------------ |
| VLAN 10  | HR           |
| VLAN 20  | Accounting   |
| VLAN 30  | IT           |
| VLAN 40  | Servers      |
| VLAN 999 | Unused Ports |

---

# 🔒 Security Features

The network incorporates multiple Cisco security technologies to secure both management access and user traffic.

* SSH Version 2
* Local User Authentication
* RSA Encryption
* Enable Secret Passwords
* ACL-protected SSH Access
* Port Security
* DHCP Snooping
* Dynamic ARP Inspection
* BPDU Guard
* PortFast
* VLAN Segmentation
* VLAN 999 for Unused Ports
* PAT

---

# 🔑 SSH Access Policy

## Main Branch IT

The Main Branch IT department acts as the centralized administration team.

Allowed SSH Access:

* Main Branch Layer 2 Switches
* Main Branch Layer 3 Switches
* Branch Layer 2 Switches
* Branch Layer 3 Switches

---

## Branch Office IT

Allowed SSH Access:

* Branch Layer 2 Switches
* Branch Layer 3 Switches

Denied:

* Main Branch Switches

SSH access is controlled through Access Control Lists applied to the VTY lines.

---

# 👤 SSH Management Accounts

## Main Branch

| Device            | Username | Password | Enable Secret | Management IP  |
| ----------------- | -------- | -------- | ------------- | -------------- |
| Management Switch | MNGT1    | MNGT1    | secretMNGT1   | 192.168.3.8    |
| Core Switch 1     | CORE1    | CORE1    | secretCORE1   | Layer 3 Switch |
| Core Switch 2     | CORE2    | CORE2    | secretCORE2   | Layer 3 Switch |
| HR Switch         | adminHR  | adminHR  | secretHR      | 192.168.1.9    |
| Accounting Switch | adminACC | adminACC | secretACC     | 192.168.2.9    |
| IT Switch         | adminIT1 | adminIT1 | secretIT      | 192.168.3.9    |

---

## Branch Office

| Device            | Username    | Password    | Enable Secret | Management IP  |
| ----------------- | ----------- | ----------- | ------------- | -------------- |
| Management Switch | MNGTb1      | MNGTb1      | secretMNGTb1  | 192.168.30.8   |
| Core Switch 1     | adminCORE1b | adminCORE1b | secretCORE1b  | Layer 3 Switch |
| Core Switch 2     | adminCORE2b | adminCORE2b | secretCORE2b  | Layer 3 Switch |
| HR Switch         | adminHRb    | adminHRb    | secretHRb     | 192.168.10.9   |
| Accounting Switch | adminACCb   | adminACCb   | secretACCb    | 192.168.20.9   |
| IT Switch         | adminITb    | adminITb    | secretITb     | 192.168.30.9   |

---

# 🛡️ Enterprise Security Implementation

## Port Security

* Sticky MAC Address
* Maximum MAC Address = 1
* Violation Mode = Shutdown

---

## DHCP Snooping

Protects the network from rogue DHCP servers by allowing DHCP responses only from trusted interfaces.

---

## Dynamic ARP Inspection (DAI)

Protects against:

* ARP Spoofing
* ARP Poisoning
* Man-in-the-Middle attacks

DAI validates ARP packets using the DHCP Snooping Binding Table.

---

## BPDU Guard

Automatically disables PortFast ports receiving BPDUs to prevent unauthorized switches.

---

## PortFast

Configured on all user-facing interfaces for immediate forwarding.

---

## VLAN 999 (Unused Ports)

All unused switch interfaces are configured with the following:

* Assigned to VLAN 999
* Configured as Access Ports
* Administratively Shutdown

Benefits

* Prevents unauthorized physical access
* Removes unused ports from production VLANs
* Reduces the attack surface
* Follows Cisco security best practices

---

## PAT

Allows multiple private IP addresses to share a single public IP address.

---

## ACL

ACLs are implemented to:

* Restrict SSH management
* Filter inter-VLAN traffic
* Protect internal resources
* Control network access

---

# 🌐 Routing & Redundancy

## GRE Tunnel

Provides logical connectivity between both branches through the ISP.

Benefits

* Supports OSPF
* Secure private routing
* Site-to-site connectivity

---

## OSPF

Configured to dynamically exchange routes between branches.

Benefits

* Fast convergence
* Automatic route learning
* Scalable routing

---

## HSRP

Provides gateway redundancy.

Benefits

* Active/Standby Gateway
* Automatic Failover
* High Availability

---

## Rapid PVST+

Configured with:

* Root Primary
* Root Secondary

Provides:

* Loop Prevention
* Stable Topology
* Redundant Links

---

# 🛠️ Challenges Encountered

| Challenge                                        | Solution                                                                                        |
| ------------------------------------------------ | ----------------------------------------------------------------------------------------------- |
| PC9 could not ping the Branch router.            | Verified gateway configuration, GRE Tunnel, and OSPF routing.                                   |
| VLANs were not configured on the switch.         | Created VLANs and configured trunk/access ports.                                                |
| PCs could not ping the Layer 3 switch.           | Configured SVIs with IP addresses and enabled inter-VLAN routing.                               |
| Branch communication failed after enabling PAT.  | Configured NAT Exemption (No-NAT) for GRE Tunnel traffic.                                       |
| Additional VLANs were added.                     | Updated VLAN database, SVIs, HSRP, OSPF, DHCP, and ACL configurations.                          |
| Added Guest Wireless Access Point.               | Created Guest VLAN and isolated traffic using ACLs.                                             |
| Wireless clients failed to receive IP addresses. | Reset AP connection and verified DHCP, VLAN, trunk ports, DHCP Snooping, and DAI configuration. |
| HSRP continuously changed Active/Standby.        | Configured STP Root Primary and Root Secondary for every VLAN.                                  |
| Unexpected STP blocking.                         | Adjusted bridge priorities for predictable Root Bridge selection.                               |

---

# 💡 Skills Demonstrated

* Enterprise Network Design
* VLAN Configuration
* Inter-VLAN Routing
* GRE Tunnel
* OSPF
* HSRP
* Rapid PVST+
* STP Optimization
* VLAN Hardening
* Port Security
* DHCP Snooping
* Dynamic ARP Inspection
* ACL Configuration
* PAT Configuration
* SSH Configuration
* Enterprise Troubleshooting

---

# 🖥️ Software

* Cisco Packet Tracer
* Cisco IOS
* Git
* GitHub

---

# 📂 Repository Structure

```text
Enterprise-Network/
│
├── README.md
├── Enterprise_Network.pkt
├── configs/
│   ├── routers/
│   ├── layer3-switches/
│   └── layer2-switches/
├── screenshots/
│   ├── topology.png
│   ├── main.png
│   ├── branch.png


```

---

# 📚 Lessons Learned

* GRE tunnels require NAT Exemption for private inter-site traffic.
* Proper SVI configuration is essential for inter-VLAN routing.
* HSRP stability depends on proper STP root bridge placement.
* DHCP Snooping and DAI work together to secure Layer 2 communication.
* VLAN 999 is an effective method for securing unused switch ports.
* SSH provides secure remote administration compared to Telnet.
* Proper network planning reduces troubleshooting time and improves scalability.

---

# 👨‍💻 Author

**Angelo Adame**
---

# ⭐ Project Highlights

This project demonstrates the implementation of a secure, scalable, and highly available enterprise network using Cisco technologies. It integrates **GRE Tunnel, OSPF, HSRP, Rapid PVST+, Port Security, DHCP Snooping, Dynamic ARP Inspection (DAI), ACLs, PAT, SSH, and VLAN 999 for unused ports** to provide resilient routing, secure Layer 2 communication, gateway redundancy, and centralized network management.

The project also documents real-world troubleshooting scenarios encountered during deployment, showcasing practical problem-solving skills and hands-on experience with enterprise networking. It serves as a comprehensive portfolio project aligned with CCNA-level networking concepts and Cisco best practices.
