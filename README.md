# VLAN-Routing-Lab
Project for VLAN and inter-VLAN Routing

Devices:

1 × Cisco 2960 Switch

1 × Cisco 1841 Router

2 × PCs

Connections:

PC0 → Switch Fa0/1

PC1 → Switch Fa0/2

Switch Fa0/24 → Router Fa0/0

PC Configs:

PC0 IP: 192.168.10.10, Subnet: 255.255.255.0, Gateway: 192.168.10.1

PC1 IP: 192.168.20.10, Subnet: 255.255.255.0, Gateway: 192.168.20.1

Switch Config (VLAN & Trunk):

bash
Copy
Edit
vlan 10
vlan 20

interface fastethernet0/1
 switchport mode access
 switchport access vlan 10

interface fastethernet0/2
 switchport mode access
 switchport access vlan 20

interface fastethernet0/24
 switchport mode trunk
Router Config (Subinterfaces):

bash
Copy
Edit
interface fastethernet0/0.10
 encapsulation dot1Q 10
 ip address 192.168.10.1 255.255.255.0

interface fastethernet0/0.20
 encapsulation dot1Q 20
 ip address 192.168.20.1 255.255.255.0

interface fastethernet0/0
 no shutdown
Save your file as:
vlan-routing-lab.pkt


# VLAN + Inter-VLAN Routing Lab (Router-on-a-Stick)

This project demonstrates basic VLAN segmentation and inter-VLAN routing using the "router-on-a-stick" method.

---

## 🧠 Objectives

- Practice VLAN creation and port assignments
- Configure trunk link between switch and router
- Set up router subinterfaces for inter-VLAN communication
- Test network connectivity using ICMP (ping)

---

## 🧱 Topology

[PC0] -- Fa0/1 --
| Fa0/0.10 & 0.20
[SWITCH] -- Fa0/24 -- [ROUTER]
|
[PC1] -- Fa0/2 --/

yaml
Copy
Edit

---

## 📦 IP Addressing

| Device | IP Address     | Subnet Mask     | Gateway         |
|--------|----------------|-----------------|-----------------|
| PC0    | 192.168.10.10  | 255.255.255.0   | 192.168.10.1    |
| PC1    | 192.168.20.10  | 255.255.255.0   | 192.168.20.1    |

---

## 🔧 Configuration Summary

### Switch

```bash
vlan 10
vlan 20

interface fa0/1
 switchport mode access
 switchport access vlan 10

interface fa0/2
 switchport mode access
 switchport access vlan 20

interface fa0/24
 switchport mode trunk
Router
bash
Copy
Edit
interface fa0/0.10
 encapsulation dot1Q 10
 ip address 192.168.10.1 255.255.255.0

interface fa0/0.20
 encapsulation dot1Q 20
 ip address 192.168.20.1 255.255.255.0

interface fa0/0
 no shutdown
✅ Test Results
From PC0:

bash
Copy
Edit
ping 192.168.20.10
Reply from 192.168.20.10: bytes=32 time<1ms TTL=128
🧠 Skills Practiced
VLAN and port isolation

Switch trunking

Router subinterfaces

Inter-VLAN routing

Basic troubleshooting and packet flow

📁 Files
vlan-routing-lab.pkt – Packet Tracer simulation file

README.md – Project overview and configuration guide
