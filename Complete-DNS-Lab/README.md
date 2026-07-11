# DNS Basic Lab

> DNS(Domain Name System)의 기본 원리부터 Cisco Packet Tracer 기반 실습까지 진행하는 네트워크 기초 Lab입니다.

---

# 1. Introduction

인터넷에서 사용자는 웹사이트 접속 시 사람이 기억하기 쉬운 Domain Name을 사용합니다.

예:

```
www.naver.com
```

하지만 실제 네트워크 통신에서는 IP Address를 기반으로 데이터가 전달됩니다.

예:

```
223.130.195.95
```

DNS(Domain Name System)는 사람이 사용하는 Domain Name을 컴퓨터와 네트워크 장비가 사용하는 IP Address로 변환하는 핵심 서비스입니다.

이번 Lab에서는 DNS의 개념부터 실제 패킷 흐름까지 단계적으로 학습합니다.

---

# 2. Learning Path

DNS 학습 과정:

```
01. DNS Theory

        ↓

02. DNS Server Setup
(Packet Tracer)

        ↓

03. DNS Query Analysis
(Packet Tracer)

        ↓

04. Real DNS Server
(EVE-NG / BIND)
```

---

# 3. Lab Contents

## Chapter 01. DNS Theory

📂 `01_DNS_Theory`

DNS의 기본 개념과 동작 원리를 학습합니다.

학습 내용:

- DNS가 필요한 이유
- Domain Name과 IP Address 관계
- DNS 동작 과정
- Resolver
- Recursive Query
- Iterative Query
- DNS Server 구조
- Root DNS
- TLD DNS
- Authoritative DNS
- Resource Record
- A / AAAA / CNAME / MX / NS / PTR / TXT
- TTL
- DNS 보안 개념

목표:

DNS가 단순한 이름 변환 서비스가 아니라 인터넷 인프라의 핵심 시스템임을 이해합니다.

---

# Chapter 02. Packet Tracer DNS Setup

📂 `02_PacketTracer_DNS_Setup`

Cisco Packet Tracer 환경에서 기본 DNS 서비스를 구축합니다.

Topology:

```
              PC1
               |
               |
              SW1
            /     \
          DNS1    WEB1
```

구성 내용:

- Client PC 구성
- DNS Server 구성
- Web Server 구성
- DNS Service 활성화
- A Record 등록
- Client DNS 설정
- Domain 기반 Web 접속 확인


실습 목표:

```
www.company.com

        ↓ DNS

192.168.10.3
```

Domain Name이 IP Address로 변환되는 기본 과정을 확인합니다.

---

# Chapter 03. Packet Tracer DNS Query Analysis

📂 `03_PacketTracer_DNS_Analysis`

Packet Tracer Simulation Mode를 이용하여 DNS 패킷 흐름을 분석합니다.

분석 범위:

```
ARP

↓

DNS Query

↓

DNS Response
```

학습 내용:

- ARP Request
- ARP Reply
- DNS Query 생성 과정
- UDP 53 Port
- DNS Server 응답 과정
- Domain → IP 변환 과정


중요한 패킷 흐름:

```
PC

↓

ARP
(DNS Server MAC 확인)

↓

DNS Query
(UDP 53)

↓

DNS Server

↓

DNS Response

↓

IP Address 획득
```

---

# 4. Network Concept

## DNS 동작 기본 구조

```
Client

↓

Resolver

↓

Recursive DNS Server

↓

Root DNS

↓

TLD DNS

↓

Authoritative DNS

↓

IP Address Response
```

---

# 5. DNS 주요 Record

| Record | 설명 |
|---|---|
| A | Domain → IPv4 Address |
| AAAA | Domain → IPv6 Address |
| CNAME | Domain Alias |
| MX | Mail Server 지정 |
| NS | Name Server 지정 |
| PTR | Reverse DNS |
| TXT | Text 정보 및 인증 |
| SOA | Zone Authority 정보 |

---

# 6. Packet Tracer Lab Environment

사용 장비:

| Device | Role |
|---|---|
| PC | DNS Client |
| Switch | Layer 2 Network |
| DNS Server | Name Resolution |
| Web Server | Application Server |

Network:

```
192.168.10.0/24
```

Address:

| Device | IP |
|---|---|
| PC1 | 192.168.10.10 |
| DNS1 | 192.168.10.2 |
| WEB1 | 192.168.10.3 |

---

# 7. Practical Troubleshooting

DNS 장애 발생 시 확인 순서:

```
1. Physical Link 확인

2. IP Configuration 확인

3. ARP Table 확인

4. DNS Server Reachability 확인

5. DNS Query 확인

6. DNS Response 확인
```

대표적인 장애:

- 잘못된 DNS Server 설정
- A Record 오류
- DNS 서비스 중단
- TTL Cache 문제
- 잘못된 Domain 설정

---

# 8. Real World Extension

Packet Tracer에서는 DNS 기본 동작을 학습했습니다.

실제 운영 환경에서는 다음 요소가 추가됩니다.

```
EVE-NG

↓

Linux DNS Server

↓

BIND

↓

Zone File

↓

Master / Slave DNS

↓

Zone Transfer

↓

DNSSEC

↓

Split Horizon DNS
```

---

# 9. Learning Goal

이번 DNS Basic Lab을 통해 다음 역량을 목표로 합니다.

✅ DNS 기본 원리 이해  
✅ Domain Resolution 과정 이해  
✅ DNS Server 구성 경험  
✅ Packet 분석 능력 향상  
✅ 네트워크 장애 분석 기반 확보  

---

# 10. Reference

관련 학습:

- TCP/IP Network
- OSI Model
- UDP/TCP
- ARP
- Application Layer Protocol
- Network Troubleshooting

---

# Author

Network Lab Study
