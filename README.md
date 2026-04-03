# FSNA Enterprise Network Lab

A complete enterprise network simulation built in Cisco Packet Tracer, covering switching,
routing, VoIP, wireless, and network security. Demonstrates hands-on proficiency with
Cisco IOS and core networking concepts at CCNA level.

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

## Devices

| Device     | Model           | Role                            |
|------------|-----------------|---------------------------------|
| FSNA-RTR   | Cisco 2811      | Router — gateway & call manager |
| FSNA-SW1   | Cisco 3560-24PS | Core switch — STP root bridge   |
| FSNA-SW2   | Cisco 2960-24TT | Access switch                   |
| FSNA-WAP   | AccessPoint-PT  | Wireless access point           |
| User A/B   | PC-PT           | Data VLAN end devices           |
| NOC PC     | PC-PT           | Management VLAN admin station   |
| Phone A/B  | Cisco 7960      | VoIP phones (ext. 1001 / 1002)  |
| Tablet     | TabletPC-PT     | Wireless end device             |
| Web Server | Server-PT       | Internal web server             |

---

## VLAN Design

| VLAN | Name       | Subnet           | Purpose          |
|------|------------|------------------|------------------|
| 100  | MANAGEMENT | 192.168.100.0/24 | Network admin    |
| 150  | VOICE      | 192.168.150.0/24 | VoIP phones      |
| 200  | DATA       | 192.168.200.0/24 | End user devices |

---

## Configuration Summary

### Switching
- VLAN segmentation across 3 VLANs with 802.1Q trunk links
- MLS QoS for voice traffic prioritization
- Spanning Tree Protocol with SW1 as root bridge
- Access ports assigned to data and voice VLANs

### Routing
- Router-on-a-Stick with subinterfaces for all 3 VLANs
- Inter-VLAN routing verified across all subnets
- Static default route to ISP gateway

### DHCP
- Separate pools for DATA (192.168.200.0/24) and VOICE (192.168.150.0/24)
- Excluded addresses: 192.168.200.1–.50
- DNS: 8.8.8.8 assigned to all clients

### Security
- Enable secret and `service password-encryption` on all devices
- SSH v1.99 with 2048-bit RSA keys on all devices
- Named standard ACL restricting VTY access to Management VLAN only (192.168.100.0/24)

### VoIP
- Cisco Unified Communications via `telephony-service`
- Two ephone-dn entries: ext. 1001 (Phone A) and ext. 1002 (Phone B)
- Phones registered and verified calling each other

### Wireless
- SSID: `FSNA-Lab` with WPA2-PSK authentication
- Tablet connected wirelessly via DHCP

---

## Verification Results — Lab 1

| Test                     | Result               |
|--------------------------|----------------------|
| User A DHCP              | 192.168.200.51 ✅    |
| User B DHCP              | 192.168.200.52 ✅    |
| Tablet DHCP (wireless)   | 192.168.200.53 ✅    |
| Phone A DHCP (voice)     | 192.168.150.12 ✅    |
| Phone B DHCP (voice)     | 192.168.150.11 ✅    |
| NOC PC (static)          | 192.168.100.10 ✅    |
| Inter-VLAN ping          | All VLANs reachable ✅ |
| Web server browsing      | Accessible from all PCs ✅ |
| Phone A → Phone B call   | Connected ✅         |
| Phone B → Phone A call   | Connected ✅         |
| SSH from Management VLAN | Working ✅           |

---

## Lab 2 — FSNA SQC Real Exam (NGT Academy)

Completed the official Full Stack Network Associate Skills Qualification Check from NGT Academy
under real exam conditions using a pre-built topology extended with ISP, PSTN, and DNS infrastructure.

### Additional Devices

| Device          | Role                               |
|-----------------|------------------------------------|
| SP-RTR          | ISP router (pre-configured)        |
| PSTN / PSTN-SW  | Public Switched Telephone Network  |
| PSTN Test       | External test phone                |
| Web/DNS Server  | Internet web and DNS (8.8.8.8)     |

### Additional Skills Demonstrated
- WAN link configuration (G0/1 to ISP)
- Internet access via NAT through ISP router
- PSTN external call to 888-555-1111
- DNS resolution via Web/DNS Server

### Verification Results

| Test                      | Result |
|---------------------------|--------|
| User A / User B DHCP      | ✅     |
| Tablet wireless           | ✅     |
| Phone A registered (1001) | ✅     |
| Phone B registered (1002) | ✅     |
| PSTN call (8885551111)    | ✅     |
| Browse www.google.com     | ✅     |
| Ping between all PCs      | ✅     |

**File:** `guide_SQC.pka`

---

## Tools

- Cisco Packet Tracer 8.x
- Cisco IOS CLI

---

## Certifications in Progress

- CompTIA Security+
- Cisco CCNA

---

## Author

**Richard Karoki**
[LinkedIn](https://linkedin.com/in/richard-karoki-007) · [Email](mailto:karokirichard522@gmail.com)