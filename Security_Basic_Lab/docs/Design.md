# 📐 Network Design

## Overview

본 실습은 Cisco Packet Tracer를 이용하여 기업(Enterprise) 네트워크를 가정하고 설계한 기본 보안(Network Security Fundamentals) 실습입니다.

단순한 라우팅 구성뿐만 아니라, 라우터 관리 보안과 접근 제어 기능을 함께 적용하여 실제 운영 환경과 유사한 구성을 목표로 하였습니다.

---

# Design Goals

- Enterprise Network 구조 이해
- EIGRP 기반 동적 라우팅 구성
- Router 간 WAN 연결
- Branch Office 연결
- 보안 기능 적용
- 안전한 원격 관리 구현

---

# Network Architecture

```
                 ISP
                  │
          10.1.1.0/24
                  │
             Internet
                  │
          10.1.2.0/24
     ┌────────┴────────┐
     │                 │
    WAN               R2
     │                 │
10.1.3.0/24      10.1.5.0/24
     │           10.1.6.0/24
     │
     NY
10.1.4.0/24

                  │
                 R3
          10.1.7.0/24
          10.1.8.0/24
```

---

# Device Roles

| Device | Role |
|---------|------|
| ISP | ISP Router |
| Internet | Enterprise Core Router |
| WAN | WAN Router |
| NY | Branch Router |
| R2 | Distribution Router |
| R3 | Secure Management Router |

---

# Routing Design

본 실습에서는 EIGRP AS 100을 사용하여 모든 네트워크를 동적으로 학습하도록 구성하였습니다.

### Advantages

- 빠른 수렴(Convergence)
- 자동 경로 학습
- 간단한 구성
- 확장 가능한 구조

---

# Security Design

각 Router마다 서로 다른 보안 기능을 적용하여 다양한 Cisco IOS Security 기능을 실습하였습니다.

## Internet Router

- Privilege Level 구성
- Command Authorization

---

## NY Router

- Login Block
- Password Policy
- Local User Authentication
- Extended ACL
- Remote Syslog

---

## R2

- Console Password
- Enable Password
- VTY Password
- Standard ACL
- MOTD Banner

---

## R3

- SSH Version 2
- Local User Authentication
- RSA Key
- Secure Remote Management

---

# Security Policy

관리자 접근은 인증된 사용자만 허용하며, 장비별 목적에 따라 접근 방식을 구분하였습니다.

| Device | Remote Access |
|---------|---------------|
| Internet | Privilege Level |
| NY | Telnet |
| R2 | Telnet + ACL |
| R3 | SSH Only |

---

# Design Considerations

설계 시 다음 사항을 고려하였습니다.

- 계층적 네트워크 구조
- 관리 네트워크 분리
- 동적 라우팅 적용
- 관리 접근 보안 강화
- 접근 제어(ACL)
- 로그 수집(Syslog)
- 관리 계정 보호

---

# Result

본 실습을 통해 다음 기능을 하나의 Enterprise Network에서 구현하였습니다.

- EIGRP Dynamic Routing
- Enterprise Backbone
- Branch Office Connectivity
- SSH Remote Management
- Telnet Authentication
- Standard ACL
- Extended ACL
- Login Security
- Privilege Levels
- Syslog Logging
- Cisco IOS Hardening

---

# Conclusion

본 프로젝트는 Cisco IOS의 기본 보안 기능과 Enterprise 네트워크 구성을 함께 실습하기 위한 프로젝트입니다.

라우팅, 접근 제어, 인증, 원격 관리, 로그 관리 기능을 통합하여 실제 운영 환경에서 사용되는 기본적인 네트워크 보안 기술을 학습할 수 있도록 설계하였습니다.