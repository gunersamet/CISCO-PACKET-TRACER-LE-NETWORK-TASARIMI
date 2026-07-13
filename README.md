# CISCO-PACKET-TRACER-LE-NETWORK-TASARIMI
This project is a small-scale enterprise network simulation designed on Cisco Packet Tracer, implementing VLAN segmentation and inter-VLAN routing using a router-on-a-stick method.




# VLAN-Based Enterprise Network Design — Cisco Packet Tracer

This project is a small-scale enterprise network simulation built in Cisco Packet Tracer, implementing VLAN segmentation with inter-VLAN routing via the router-on-a-stick method.

## 🖧 Topology

| Device | Type | Role |
|---|---|---|
| Router0 | Cisco 2911 | Inter-VLAN routing (router-on-a-stick) |
| Switch0, Switch1, Switch2 | L2 Switch | VLAN access switches |
| Server0, Server1 | Server | Service servers |
| MUHASEBE_PC | PC | Accounting department client |
| MİSAFIR_PC | Laptop | Guest network client |
| NORMAL_PC | PC | General user client |

## 🌐 VLAN and IP Plan

| VLAN | Segment | Subnet | Gateway |
|---|---|---|---|
| VLAN 10 | Accounting | 192.168.10.0/24 | 192.168.10.1 |
| VLAN 20 | General Users | 192.168.20.0/24 | 192.168.20.1 |
| VLAN 30 | Servers | 192.168.30.0/24 | 192.168.30.1 |
| VLAN 40 | Guest | 192.168.40.0/24 | 192.168.40.1 |

On the router, the `GigabitEthernet0/0` interface is divided into subinterfaces (one per VLAN, using dot1Q encapsulation) — a router-on-a-stick design.

## 🔒 Access Control List (ACL)

An extended ACL named `MISAFIR_ENGEL` (Turkish for "guest block") is defined to prevent the guest network (VLAN 40) from reaching the accounting network (VLAN 10):

```
ip access-list extended MISAFIR_ENGEL
 deny ip 192.168.40.0 0.0.0.255 192.168.10.0 0.0.0.255
 permit ip any any
```

This ACL is applied inbound on `GigabitEthernet0/0.40`. As a result, devices on the guest VLAN cannot reach the accounting VLAN, while access to all other networks remains open.

## ⚙️ Technologies / Concepts Used

- VLAN segmentation (802.1Q trunking)
- Inter-VLAN routing via router-on-a-stick
- Extended ACL for restricting access between network segments
- Layered (hierarchical) network topology

## 📁 Files

- `SAMETGUNER_NETWORK_PROJE_1.pkt` — Cisco Packet Tracer project file

## ▶️ How to Run

1. Download and install [Cisco Packet Tracer](https://www.netacad.com/courses/packet-tracer).
2. Open the `.pkt` file in Packet Tracer.
3. Inspect the network configuration via each device's CLI/Config tab.
4. Use Simulation mode to observe packet flow step by step.

## 📌 Notes

This project was created as part of a computer networks course assignment, and is intended to demonstrate VLAN-based network segmentation and basic access control principles in practice.
