# 🔐 Security Basic Lab

Enterprise Network Security Fundamentals using Cisco Packet Tracer

---

## 📖 Overview

이 프로젝트는 Cisco Packet Tracer를 이용하여 기업 네트워크를 구축하고
라우팅과 기본 보안 기능을 구현한 실습입니다.

구성한 내용은 실제 Cisco IOS 환경에서 자주 사용하는 기능을 중심으로 작성하였습니다.

### 주요 기능

- EIGRP Dynamic Routing
- Enterprise Backbone
- WAN Connectivity
- SSH Remote Management
- Telnet Authentication
- Standard ACL
- Extended ACL
- Login Security
- Syslog
- Router Hardening

---

## 🖼 Topology

```
docs/Topology.png
```

---

## 📂 Project Structure

```text
04_Security_Basic_Lab
│
├── README.md
├── configs
├── docs
├── screenshots
└── packettracer
```

---

## 🖥 Devices

| Device | Role |
|---------|------|
| ISP | ISP Router |
| Internet | Core Router |
| WAN | WAN Router |
| NY | Branch Router |
| R2 | Distribution Router |
| R3 | Secure Management Router |

---

## 🌐 Network

| Network | Purpose |
|----------|----------|
|10.1.1.0/24|ISP|
|10.1.2.0/24|Backbone|
|10.1.3.0/24|WAN|
|10.1.4.0/24|NY Office|
|10.1.5.0/24|LAN-A|
|10.1.6.0/24|LAN-B|
|10.1.7.0/24|LAN-C|
|10.1.8.0/24|Server|

---

## 🔒 Security Features

- SSH Version 2
- Local User Authentication
- Telnet Authentication
- Login Blocking
- Login Logging
- Password Policy
- Standard ACL
- Extended ACL
- Privilege Levels
- MOTD Banner
- Remote Syslog

---

## 📋 Verification

- EIGRP Neighbor 확인
- Ping Test
- Traceroute
- SSH Login
- Telnet Login
- ACL 동작 확인
- Syslog 확인

---

## 📁 Configuration Files

```text
configs
├── ISP.txt
├── Internet.txt
├── WAN.txt
├── NY.txt
├── R2.txt
└── R3.txt
```

---

## 🎯 Skills

- Cisco IOS
- EIGRP
- ACL
- SSH
- Telnet
- Router Security
- Syslog
- Network Troubleshooting