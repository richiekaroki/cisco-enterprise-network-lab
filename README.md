# cisco-enterprise-network-lab
Cisco Enterprise Network Lab Multi-VLAN Infrastructure with VoIP and Wireless

# FSNA Enterprise Network Lab
### Built with Cisco Packet Tracer

---

## Overview

A complete enterprise network simulation built 
from scratch covering switching, routing, VoIP, 
wireless and network security. This lab demonstrates 
hands-on proficiency with Cisco IOS and core 
networking concepts equivalent to CCNA level knowledge.

---

## Network Topology
```
[NOC PC]──[FSNA-SW1]──[FSNA-RTR]
              |    \──[FSNA-WAP]~~~[Tablet]
          [User A]
          [Phone A]
              |
          [FSNA-SW2]──[Web Server]
              |
          [User B]
          [Phone B]
```

---

## Devices Used

| Device | Model | Role |
|---|---|---|
| FSNA-RTR | Cisco 2811 | Router — gateway and call manager |
| FSNA-SW1 | Cisco 3560-24PS | Core switch — root bridge |
| FSNA-SW2 | Cisco 2960-24TT | Access switch |
| FSNA-WAP | AccessPoint-PT | Wireless access point |
| User A | PC-PT | Data VLAN end device |
| User B | PC-PT | Data VLAN end device |
| NOC PC | PC-PT | Management VLAN admin station |
| Phone A | Cisco 7960 | VoIP phone — extension 1001 |
| Phone B | Cisco 7960 | VoIP phone — extension 1002 |
| Tablet | TabletPC-PT | Wireless end device |
| Web Server | Server-PT | Internal web server |

---

## VLAN Design

| VLAN | Name | Subnet | Purpose |
|---|---|---|---|
| 100 | MANAGEMENT | 192.168.100.0/24 | Network admin access |
| 150 | VOICE | 192.168.150.0/24 | VoIP phones |
| 200 | DATA | 192.168.200.0/24 | End user devices |

---

## What Was Configured

### Switching
- VLAN segmentation across 3 VLANs
- 802.1Q trunk links between switches
- Trunk link from SW1 to router
- MLS QoS for voice traffic prioritization
- Spanning Tree Protocol — SW1 as root bridge
- Access ports with data and voice VLAN assignment

### Routing
- Router on a Stick — subinterfaces for all 3 VLANs
- Inter-VLAN routing verified across all subnets
- Static default route to ISP gateway

### DHCP
- DHCP pool DATA serving 192.168.200.0/24
- DHCP pool VOICE serving 192.168.150.0/24
- Excluded addresses 192.168.200.1 to .50
- DNS server 8.8.8.8 assigned to all clients

### Security
- Enable secret password on all devices
- Service password encryption enabled
- SSH version 1.99 configured on all devices
- RSA keys generated at 2048 bits
- Named standard ACL restricting VTY access
- Only Management VLAN 192.168.100.0/24 can SSH

### VoIP
- Cisco Unified Communications via telephony-service
- Two ephone-dn directory numbers configured
- Extension 1001 — Phone A
- Extension 1002 — Phone B
- Phones registered and verified calling each other

### Wireless
- SSID FSNA-Lab configured on WAP
- WPA2-PSK authentication
- Tablet connected wirelessly via DHCP

---

## Verification Results

| Test | Result |
|---|---|
| User A DHCP | 192.168.200.51 ✅ |
| User B DHCP | 192.168.200.52 ✅ |
| Tablet DHCP wireless | 192.168.200.53 ✅ |
| Phone A DHCP voice | 192.168.150.12 ✅ |
| Phone B DHCP voice | 192.168.150.11 ✅ |
| NOC PC static | 192.168.100.10 ✅ |
| Inter-VLAN ping | All VLANs reachable ✅ |
| Web Server browsing | Accessible from all PCs ✅ |
| Phone A calls Phone B | Connected ✅ |
| Phone B calls Phone A | Connected ✅ |
| SSH access | Working from Management VLAN ✅ |

---

## Skills Demonstrated

- Cisco IOS CLI configuration
- VLAN design and implementation
- Inter-VLAN routing
- DHCP server configuration
- Network security with ACLs
- SSH hardening
- Spanning Tree Protocol
- Cisco VoIP telephony
- Wireless network configuration
- Network troubleshooting and verification

---

## Tools Used

- Cisco Packet Tracer 8.x
- Cisco IOS CLI

---

## Author

**Richard Karoki**
[LinkedIn](https://linkedin.com/in/richard-karoki-007)
[Email](mailto:karokirichard522@gmail.com)

---

## Related Certifications Being Pursued

- CompTIA Security+
- Cisco CCNA
