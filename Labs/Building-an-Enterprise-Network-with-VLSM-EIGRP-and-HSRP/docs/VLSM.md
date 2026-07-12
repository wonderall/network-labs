# 📐 VLSM Addressing

## Overview

This lab uses **Variable Length Subnet Mask (VLSM)** to divide the 11.1.1.0/24 network into multiple /28 subnets.

Although VLSM allows different subnet sizes based on host requirements, this lab uses a consistent **/28 prefix** to simplify subnet calculations and routing configuration.

---

## Addressing Plan

| Network | Purpose |
|---------|---------|
|11.1.1.0/28|ISP|
|11.1.1.16/28|Core SW1|
|11.1.1.32/28|Core SW2|
|11.1.1.48/28|WAN|
|11.1.1.64/28|Tokyo LAN|
|11.1.1.80/28|LAN A|
|11.1.1.96/28|LAN B|
|11.1.1.112/28|LAN C|

---

## Why /28?

- Practice subnetting
- Keep the topology simple
- Provide enough host addresses for each segment
- Make routing verification easier

---

## Skills Learned

- Network Address Calculation
- Broadcast Address Calculation
- Host Range Calculation
- CIDR
- VLSM