# 📐 Network Design

## Design Overview

This lab simulates a small enterprise network using Cisco Packet Tracer. The topology is designed to integrate multiple networking technologies into a single environment for hands-on practice.

The network includes:

- Internet connection
- Core network
- Multiple branch routers
- WAN connection
- Remote office (Tokyo)
- Gateway redundancy using HSRP

The primary objective is to understand how routing, subnetting, and gateway redundancy operate together in an enterprise network.

---

# Network Topology

```
                ISP
                 |
             Internet
             /      \
         Core SW1  Core SW2
          /   \      /   \
        R2    R3   WAN   R4
         |      |    |     \
      LAN A  LAN B TOKYO    R5
                               |
                            LAN C
```

---

# Design Goals

This lab focuses on the following objectives:

- Practice subnetting using VLSM
- Configure dynamic routing with EIGRP
- Implement gateway redundancy with HSRP
- Verify connectivity between multiple networks
- Simulate a simple enterprise network

---

# Network Hierarchy

The topology loosely follows a hierarchical design.

## Edge

- ISP
- Internet Router

Responsible for external network connectivity.

---

## Distribution

- Core SW1
- Core SW2

Responsible for interconnecting routers and distributing traffic.

---

## Access

- R2
- R3
- R4
- R5
- TOKYO

Provide connectivity to end-user LANs.

---

# Design Notes

This topology is intended for learning purposes.

Some design choices were made to simplify configuration:

- Every subnet uses a /28 prefix.
- Packet Tracer limitations require HSRP instead of VRRP.
- EIGRP is selected to practice dynamic routing.
- The focus is on understanding protocol behavior rather than reproducing a production environment.

---

# Key Technologies

| Technology | Purpose |
|------------|---------|
|VLSM|Subnetting|
|EIGRP|Dynamic Routing|
|HSRP|Gateway Redundancy|
|Cisco Packet Tracer|Simulation Platform|