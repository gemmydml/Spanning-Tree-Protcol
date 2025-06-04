# Spanning-Tree-Protcol# Spanning Tree Protocol (STP) – Complete Guide

## 📘 Introduction

In Ethernet networks, loops can cause major issues like broadcast storms and multiple frame copies, leading to network instability. The **Spanning Tree Protocol (STP)** is a Layer 2 protocol designed to prevent such loops by selectively blocking redundant paths until they are needed.

This repository provides a structured explanation of STP, the problem it solves, and a hands-on guide to implementing and testing it in a network topology.

---

## ❗ Problem Statement

In switched networks with redundant links, loops can form. Unlike routers, switches do not have a built-in loop prevention mechanism. This leads to problems such as:

- Broadcast storms (uncontrolled flooding of broadcast packets)
- Multiple frame transmission (same frame delivered multiple times)
- MAC table instability (switches receive frames on multiple interfaces)

These problems can bring down a network or severely degrade performance.

---

## ✅ Why STP Is the Solution

The **Spanning Tree Protocol**, standardized as IEEE 802.1D, addresses these challenges by:

- Electing a single **Root Bridge**
- Calculating the shortest path from all switches to the Root Bridge
- **Blocking** redundant paths while keeping one active to prevent loops
- **Automatically re-enabling** blocked paths if an active link fails

STP dynamically maintains a loop-free logical topology, improving network resilience and availability.

---

## 🔧 Implementation Guide

This guide will walk you through implementing STP in a basic network topology using **Cisco Packet Tracer**, but the logic applies to any managed switches.

### 🌐 Topology Setup

- 3 Switches: `SW1` (Root), `SW2`, `SW3`
- 3 PCs: `PC1`, `PC2`, `PC3`
- Connect as follows:
markdown
Copy code
 PC1         PC2         PC3
  |           |           |
 SW1 -------- SW2 ------- SW3
  \__________/ \_________/
yaml
Copy code

---

### 🪜 Step-by-Step Configuration (Cisco CLI)

1. **Assign Hostnames**
 ```bash
 SW1> enable
 SW1# configure terminal
 SW1(config)# hostname SW1
Repeat for SW2, SW3.

Set SW1 as Root Bridge

bash
Copy code
SW1(config)# spanning-tree vlan 1 priority 0
Verify STP Status
On each switch:

bash
Copy code
SW1# show spanning-tree
You should see:

SW1 as Root

Ports in Forwarding or Blocking state

Test Redundancy

Unplug a link between switches.

Observe STP unblocking alternate paths and traffic resuming.

Optional: Set PortFast on Access Ports

bash
Copy code
SW1(config)# interface fastethernet0/1
SW1(config-if)# spanning-tree portfast
🧪 Testing STP
Use ping between PCs to test connectivity.

Use show spanning-tree and show mac address-table to monitor STP behavior.

Simulate a link failure to observe STP reconvergence.

📚 Resources
Cisco STP Configuration Guide

IEEE 802.1D Standard

👨‍💻 Contributors
Your Name – @yourgithub

📜 License
This project is open-sourced under the MIT License.

yaml
Copy code

---

### 📁 Repository Structure

spanning-tree-protocol-guide/
├── README.md
├── diagrams/
│ └── stp-topology.png # Network topology image
├── configs/
│ ├── sw1-config.txt
│ ├── sw2-config.txt
│ └── sw3-config.txt
├── packet-tracer/
│ └── stp-simulation.pkt # Optional Packet Tracer file
└── LICENSE

yaml

---







