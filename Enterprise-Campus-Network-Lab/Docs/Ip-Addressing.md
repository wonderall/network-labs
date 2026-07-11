# IP Address Plan

Base Network

```
11.1.1.0/24
```

Subnet

```
255.255.255.240 (/28)
```

| Network | Usage |
|----------|------|
|11.1.1.0/28|Core|
|11.1.1.16/28|L3 Links|
|11.1.1.32/28|Building A VLAN10|
|11.1.1.48/28|Building A VLAN20|
|11.1.1.64/28|Building B VLAN10|
|11.1.1.80/28|Building B VLAN20|
|11.1.1.96/28|HSRP|
|11.1.1.112/28|Building C L3|
|11.1.1.128/28|Routing|
|11.1.1.144/28|Routing|
|11.1.1.160/28|Building C VLAN10|
|11.1.1.176/28|Building C VLAN20|