# 📚 Lessons Learned

This lab provided practical experience in designing and configuring a small enterprise network.

---

# Technical Skills

During this lab, I practiced:

- Designing IP addressing using VLSM
- Configuring EIGRP routing
- Implementing HSRP redundancy
- Building a multi-router topology
- Verifying routing and connectivity

---

# What I Learned

## VLSM

I improved my understanding of subnet calculations, host allocation, and efficient IP address planning.

---

## EIGRP

I learned how routers establish neighbor relationships and exchange routing information automatically.

I also verified routing tables and EIGRP neighbors using Cisco IOS commands.

---

## HSRP

Although Packet Tracer supports HSRP instead of VRRP, I was able to understand the concept of First Hop Redundancy Protocol (FHRP).

I verified:

- Active Router
- Standby Router
- Virtual IP
- Failover behavior

---

## Verification

The following commands were used throughout the lab.

```
show ip route
show ip interface brief
show ip protocols
show ip eigrp neighbors
show standby brief
```

These commands helped verify routing information and protocol operation.

---

# Challenges

Some configuration errors prevented connectivity during the initial setup.

Troubleshooting included:

- Verifying interface status
- Checking IP addressing
- Reviewing routing tables
- Confirming EIGRP neighbor relationships

This process reinforced the importance of systematic troubleshooting.

---

# Future Improvements

Possible extensions for this topology include:

- OSPF implementation
- Route summarization
- ACL configuration
- NAT
- IPv6
- VRRP on real Cisco or multi-vendor equipment
- Redistribution between routing protocols

---

# Summary

This lab combined several important networking concepts into one topology.

Rather than configuring each technology separately, it demonstrated how subnetting, routing, and gateway redundancy work together to build a functional enterprise network.