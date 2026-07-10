# ✅ Verification

## Verify Interface Status

```text
show ip interface brief
```

Expected Result

- All required interfaces are up/up

---

## Verify Routing Table

```text
show ip route
```

Expected Result

- Remote networks learned successfully

---

## Verify EIGRP

```text
show ip eigrp neighbors
```

Expected Result

- Neighbor relationships established

---

## Verify HSRP

```text
show standby brief
```

Expected Result

- One Active router
- One Standby router
- Virtual IP operational

---

## Connectivity Test

```text
ping

traceroute
```

Expected Result

- Successful communication between all networks.