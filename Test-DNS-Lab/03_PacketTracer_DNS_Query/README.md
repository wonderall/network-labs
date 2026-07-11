# Chapter 03. Packet Tracer DNS Query Analysis

> Packet Tracer Simulation Mode를 이용하여 DNS Name Resolution 과정을 패킷 단위로 분석합니다.

---

# 1. 실습 목적

Chapter 02에서는 DNS Server를 구성하고 Domain Name 기반 접속을 확인했습니다.

이번 실습에서는 사용자가 도메인을 입력했을 때 실제 네트워크에서 어떤 패킷이 발생하는지 분석합니다.

이번 Lab의 분석 범위는 다음과 같습니다.

```
ARP

↓

DNS Query

↓

DNS Response
```

이번 실습에서는 DNS 이름 해석 과정까지만 확인하며, TCP 연결 및 HTTP 통신 분석은 별도 Web Lab에서 진행합니다.

---

# 2. 실습 환경

Chapter 02와 동일한 네트워크 환경을 사용합니다.

```
              PC1
               |
               |
              SW1
            /     \
          DNS1    WEB1
```

---

# 3. IP Address 구성

| 장비 | IP Address | 역할 |
|---|---|---|
| PC1 | 192.168.10.10/24 | Client |
| DNS1 | 192.168.10.2/24 | DNS Server |
| WEB1 | 192.168.10.3/24 | Web Server |

---

# 4. Simulation Mode 설정

Packet Tracer 우측 하단에서 모드를 변경합니다.

```
Realtime

↓

Simulation
```

---

# 5. Event Filter 설정

이번 실습에서는 DNS 동작 확인이 목적이므로 필요한 프로토콜만 활성화합니다.

활성화:

```
ARP

DNS
```

비활성화:

```
TCP

HTTP

ICMP
```

---

# 6. Domain 요청 발생

PC1에서 Web Browser를 실행합니다.

주소 입력:

```
www.company.com
```

입력 후 Simulation Mode에서 패킷 흐름을 확인합니다.

---

# 7. Step 1 - ARP Request

DNS Query를 보내기 전에 먼저 ARP 과정이 발생합니다.

## 왜 ARP가 먼저 발생할까?

PC는 DNS Server의 IP 주소는 알고 있습니다.

설정된 DNS Server:

```
192.168.10.2
```

하지만 Ethernet 통신을 하기 위해서는 목적지 MAC Address가 필요합니다.

즉,

IP 주소는 알고 있지만 MAC 주소를 모르는 상태입니다.

따라서 PC는 먼저 ARP Request를 전송합니다.

---

## ARP Request

PC에서 전송:

```
Who has 192.168.10.2?
```

의미:

```
192.168.10.2 IP 주소를 사용하는 장비의 MAC Address를 알려주세요.
```

---

# 8. Step 2 - ARP Reply

DNS Server는 자신의 MAC Address를 응답합니다.

응답:

```
192.168.10.2 is xx:xx:xx:xx:xx:xx
```

이제 PC는 DNS Server로 Ethernet Frame을 전달할 수 있습니다.

---

# 9. Step 3 - DNS Query

ARP 과정이 완료되면 실제 DNS Query가 발생합니다.

패킷 방향:

```
PC1

↓

DNS1
```

---

## DNS Query Packet 정보

Source:

```
192.168.10.10
```

Destination:

```
192.168.10.2
```

Protocol:

```
DNS
```

Transport:

```
UDP
```

Port:

```
53
```

---

## DNS Query 내용

PC는 DNS Server에게 질문합니다.

```
www.company.com의 IP 주소를 알려주세요.
```

DNS Server는 자신이 가지고 있는 DNS Record를 검색합니다.

---

# 10. Step 4 - DNS Response

DNS Server는 등록된 A Record를 확인합니다.

등록 정보:

```
www.company.com

↓

192.168.10.3
```

그리고 PC에게 결과를 전달합니다.

패킷 방향:

```
DNS1

↓

PC1
```

---

## DNS Response 내용

응답:

```
www.company.com = 192.168.10.3
```

이제 PC는 Domain Name을 IP Address로 변환했습니다.

---

# 11. 전체 DNS 동작 흐름

전체 과정:

```
사용자

↓

Domain 입력

↓

PC DNS Cache 확인

↓

ARP
(DNS Server MAC 확인)

↓

DNS Query
(UDP 53)

↓

DNS Server 조회

↓

DNS Response

↓

Domain → IP 변환 완료
```

---

# 12. DNS 핵심 이론

## DNS는 Application Layer 서비스

DNS는 OSI 모델 기준 Layer 7(Application Layer)에서 동작합니다.

```
Application Layer

↓

DNS
```

---

## DNS 기본 Port

일반적인 DNS Query:

```
UDP 53
```

사용

UDP를 사용하는 이유:

- 빠른 응답
- 연결 과정 없음
- 작은 요청/응답 구조

---

## TCP 53을 사용하는 경우

일부 상황에서는 TCP를 사용합니다.

예:

- Zone Transfer
- DNSSEC
- 큰 DNS Response

---

# 13. ARP와 DNS 관계

DNS는 IP 기반 서비스입니다.

하지만 실제 Ethernet 환경에서는 MAC Address가 필요합니다.

따라서 같은 네트워크에서는 다음 순서로 진행됩니다.

```
ARP

↓

DNS Query

↓

DNS Response
```

ARP는 DNS 서비스가 아니라 Ethernet 통신을 위한 사전 과정입니다.

---

# 14. 실무 적용

현장에서 다음과 같은 장애 문의가 발생할 수 있습니다.

```
인터넷이 안 됩니다.
웹사이트 접속이 안 됩니다.
```

사용자는 웹 장애라고 생각하지만 실제 원인은 DNS일 수 있습니다.

장애 분석 순서:

```
1. Link 상태 확인

2. IP 설정 확인

3. ARP 확인

4. DNS Server 접근 확인

5. DNS Query 확인

6. DNS Response 확인
```

네트워크 엔지니어는 단순히 Ping 성공 여부만 보는 것이 아니라 DNS 동작 과정을 이해하고 분석할 수 있어야 합니다.

---

# 15. 실습 결과 정리

이번 Lab에서 확인한 내용:

✅ Packet Tracer Simulation Mode 사용  
✅ ARP Request / Reply 확인  
✅ DNS Query 확인  
✅ UDP 53 Port 확인  
✅ DNS Response 확인  
✅ Domain Name → IP Address 변환 과정 이해  

---

# 16. 다음 단계

이번 Packet Tracer 실습에서는 DNS의 기본 동작만 확인했습니다.

다음 단계에서는 EVE-NG 환경으로 확장하여 실제 DNS 서버를 구축합니다.

예정 실습:

- Linux DNS Server 구축
- BIND 설치
- Zone File 구성
- A / CNAME / MX Record 설정
- Master / Slave DNS 구성
- Zone Transfer 분석
- DNS 보안 설정