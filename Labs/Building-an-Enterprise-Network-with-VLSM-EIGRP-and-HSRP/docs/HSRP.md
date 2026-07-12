# 🔁 HSRP

## Overview

Hot Standby Router Protocol (HSRP) provides gateway redundancy for end devices.

Packet Tracer does not support VRRP, so HSRP is used to demonstrate First Hop Redundancy Protocol (FHRP).

---

## Topology

```
        R4 (Active)
           |
      Virtual IP
           |
        R5 (Standby)
```

---

## Purpose

If the Active router fails, the Standby router automatically takes over the virtual gateway.

This minimizes network downtime.

---

## Verification

```text
show standby brief
```

---

## Skills Learned

- Active Router
- Standby Router
- Virtual Gateway
- Failover
- Gateway Redundancy