# Enterprise Network using Cisco Packet Tracer

> Enterprise Cisco Packet Tracer network implementing GRE Tunnel, OSPF, HSRP, SSH, VLANs, ACLs, PAT, DHCP Snooping, and Layer 2 security.

---

# 📌 Overview

This project simulates an enterprise network consisting of a **Main Branch** and a **Branch Office** connected through an ISP. The network follows Cisco's hierarchical design model (Core, Distribution, and Access layers) and focuses on high availability, security, redundancy, and centralized network management.

The network was developed using **Cisco Packet Tracer** to demonstrate real-world enterprise networking concepts aligned with the CCNA curriculum.

---

# 🏗️ Network Topology

The enterprise network consists of:

## Main Branch

* 2 Cisco 3560 Layer 3 Switches
* 4 Cisco 2960 Layer 2 Switches
* Cisco 2911 Router
* DHCP/DNS Server
* Additional Server
* Wireless Access Point
* HR Department
* Accounting Department
* IT Department
* Management Switch

## Branch Office

* 2 Cisco 3560 Layer 3 Switches
* 4 Cisco 2960 Layer 2 Switches
* Cisco 2911 Router
* DHCP for Branch
* Wireless Access Point
* HR Department
* Accounting Department
* IT Department
* Management Switch

Both sites communicate through an ISP using a **GRE Tunnel**, while **OSPF** dynamically exchanges routes between branches.

---

# 🚀 Technologies Implemented

* ✅ GRE Tunnel
* ✅ OSPF Dynamic Routing
* ✅ HSRP Gateway Redundancy
* ✅ Rapid PVST+
* ✅ Root Primary / Secondary Election
* ✅ PortFast
* ✅ BPDU Guard
* ✅ Port Security
* ✅ DHCP Snooping
* ✅ Port Address Translation (PAT)
* ✅ Access Control Lists (ACL)
* ✅ SSH Version 2
* ✅ Guest Wireless VLAN

---

# 🔒 Security Features

The network is secured using multiple Cisco security technologies.

* SSH Version 2
* Local User Authentication
* RSA Encryption
* Enable Secret Passwords
* ACL-based SSH Restrictions
* Port Security
* DHCP Snooping
* BPDU Guard
* PAT
* VLAN Segmentation

---

# 🔑 SSH Access Policy

The Main Branch acts as the centralized network management site.

## Main Branch IT Administrators

Allowed to SSH into:

* All Main Branch Layer 2 Switches
* All Main Branch Layer 3 Switches
* All Branch Office Layer 2 Switches
* All Branch Office Layer 3 Switches

---

## Branch Office IT Administrators

Allowed to SSH into:

* Branch Office Layer 2 Switches
* Branch Office Layer 3 Switches

Not Allowed:

* Main Branch Switches

SSH access is restricted using Access Control Lists (ACLs) applied to the VTY lines.

---

# 👤 SSH Management Accounts (Lab Credentials)

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

> **Note:** These credentials are used for educational purposes within this Packet Tracer lab and should not be used in production environments.

---

# 🌐 Technologies Used

| Technology               | Description                                                                     |
| ------------------------ | ------------------------------------------------------------------------------- |
| GRE Tunnel               | Provides secure logical connectivity between the Main Branch and Branch Office. |
| OSPF                     | Dynamically exchanges routing information between sites.                        |
| HSRP                     | Provides gateway redundancy for user VLANs.                                     |
| Rapid PVST+              | Prevents Layer 2 loops while maintaining redundancy.                            |
| Root Primary / Secondary | Ensures predictable spanning-tree topology.                                     |
| PortFast                 | Speeds up access port initialization.                                           |
| BPDU Guard               | Protects edge ports from unauthorized switches.                                 |
| Port Security            | Restricts unauthorized devices on access ports.                                 |
| DHCP Snooping            | Prevents rogue DHCP servers.                                                    |
| PAT                      | Allows multiple hosts to share a single public IP address.                      |
| ACL                      | Controls traffic flow and restricts SSH access.                                 |
| SSH                      | Provides encrypted remote device management.                                    |

---

# 🛠️ Challenges Encountered

| Challenge                                                       | Resolution                                                                                                                   |
| --------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------- |
| PC9 could not ping the Branch router.                           | Verified default gateway configuration, OSPF routes, and GRE tunnel connectivity.                                            |
| VLANs were missing on an access switch.                         | Created VLANs, assigned access ports, and configured trunk links.                                                            |
| PCs could not reach the Layer 3 switch or router.               | Configured SVIs with IP addresses, enabled interfaces using `no shutdown`, and verified inter-VLAN routing.                  |
| Communication between branches failed after enabling NAT/PAT.   | Configured NAT Exemption (No-NAT) for traffic traversing the GRE tunnel.                                                     |
| Additional VLANs needed to be deployed.                         | Created VLANs across all switches and updated SVIs, DHCP scopes, HSRP, OSPF, and ACL configurations.                         |
| Added a Guest Wireless Access Point.                            | Created a dedicated Guest VLAN and isolated guest traffic using ACLs.                                                        |
| Wireless clients connected but failed to receive an IP address. | Reset the AP connection and verified VLAN assignment, DHCP configuration, trunk ports, and DHCP Snooping trusted interfaces. |
| HSRP continuously changed between Active and Standby states.    | Configured Root Primary and Root Secondary switches for all VLANs to stabilize STP and eliminate HSRP flapping.              |
| STP blocked unexpected trunk links.                             | Adjusted bridge priorities to establish predictable Root Bridge selection for every VLAN.                                    |

---

# 📚 Lessons Learned

This project reinforced several enterprise networking concepts:

* GRE tunnels require NAT Exemption for private inter-site communication.
* Every VLAN requires an SVI with an IP address to enable inter-VLAN routing.
* Stable HSRP operation depends on a properly designed STP topology.
* Root Bridge planning significantly improves network stability.
* DHCP Snooping requires trusted interfaces to permit legitimate DHCP traffic.
* ACLs provide fine-grained control over management and user traffic.
* SSH is a secure alternative to Telnet for remote device management.
* Proper planning of VLANs, IP addressing, and redundancy simplifies deployment and troubleshooting.

---

# 💡 Skills Demonstrated

* Enterprise Network Design
* VLAN Configuration
* Inter-VLAN Routing
* OSPF Configuration
* GRE Tunnel Deployment
* HSRP Configuration
* Spanning Tree Optimization
* Layer 2 Security
* ACL Configuration
* DHCP Snooping
* NAT/PAT Configuration
* SSH Configuration
* Enterprise Network Troubleshooting

---

# 🖥️ Software Used

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
├── screenshots/
│   ├── topology.png
│   ├── ospf-neighbor.png
│   ├── hsrp.png
│   ├── ssh.png
│   ├── port-security.png
│   └── dhcp-snooping.png
├── configs/
│   ├── routers/
│   ├── layer3-switches/
│   └── layer2-switches/
└── documentation/
    └── Enterprise_Network_Documentation.pdf
```

---

# 👨‍💻 Author

**Angelo Adame**

---

## ⭐ Project Highlights

This project demonstrates the implementation of a secure and resilient enterprise network using Cisco technologies. It showcases practical experience in network design, routing, switching, redundancy, Layer 2 security, remote management, and troubleshooting. The project serves as a portfolio piece reflecting hands-on skills expected of a Network Engineer and aligns with industry-standard CCNA enterprise networking practices.
