# 🚦 EIGRP

## Overview

Enhanced Interior Gateway Routing Protocol (EIGRP) is used as the dynamic routing protocol for all routers.

Every router belongs to **Autonomous System 100**.

---

## Configuration

```cisco
router eigrp 100
network 11.0.0.0
```

---

## How EIGRP Works

1. Discover neighbors
2. Exchange routing information
3. Calculate the best path using DUAL
4. Install routes into the routing table

---

## Verification

```text
show ip eigrp neighbors

show ip route

show ip protocols
```

---

## Skills Learned

- Neighbor Discovery
- Route Advertisement
- DUAL Algorithm
- Successor Route
- Feasible Successor