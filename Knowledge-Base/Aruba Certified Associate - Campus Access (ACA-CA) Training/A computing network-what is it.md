# 컴퓨터 네트워크(Computer Network) 기초 정리

> 강의 내용 요약 및 학습 노트

---

# 1. 컴퓨터 네트워크란?

컴퓨터 네트워크(Computer Network, Computing Network)는 **두 대 이상의 컴퓨터나 네트워크 장치(Device)를 서로 연결하여 데이터를 주고받을 수 있도록 만든 시스템**이다.

오늘날 대부분의 서비스는 네트워크를 기반으로 동작한다.

예를 들어,

- 웹 브라우징
- 이메일
- 파일 공유
- 클라우드 서비스
- SNS
- 인터넷 뱅킹
- 온라인 게임

모두 컴퓨터 네트워크를 이용한다.

컴퓨터 네트워크는 크게 두 가지 기본 요소로 구성된다.

- **노드(Node)**
- **링크(Link)**

그리고 링크를 통해 데이터를 전달할 때 **통신 프로토콜(Communication Protocol)**을 사용한다.

---

# 2. 컴퓨터 네트워크의 기본 구성

```
           Link
 PC ---------------- Router
  │                    │
  │                    │
Switch ------------ Server
```

위 그림에서

- PC
- Router
- Switch
- Server

모두 **노드(Node)** 이며,

이들을 연결하는 선이 **링크(Link)** 이다.

링크를 통해 데이터(Packet)가 이동한다.

---

# 3. 컴퓨터 네트워크 사용 예

예를 들어 사용자가 스마트폰으로 사진을 촬영했다고 가정해 보자.

사진은 스마트폰 내부 저장소에 저장된다.

하지만 친구에게 보내거나 SNS에 업로드하려면 네트워크가 필요하다.

데이터는 다음과 같이 이동한다.

```
Smartphone
      │
      ▼
Wi-Fi / LTE / 5G
      │
      ▼
Internet
      │
      ▼
SNS Server
      │
      ▼
다른 사용자
```

즉,

네트워크가 없으면 자신의 장치 내부에서만 데이터를 사용할 수 있으며 다른 사용자와 공유할 수 없다.

---

# 4. 컴퓨터 네트워크의 4가지 구성 요소

컴퓨터 네트워크는 크게 다음 네 가지 요소로 구성된다.

1. Devices (장치)
2. Links (링크)
3. Communication Protocols (통신 프로토콜)
4. Network Security (네트워크 보안)

---

# 4.1 Devices (장치)

장치(Device)는 네트워크에 연결되는 모든 장비를 의미한다.

이를 **노드(Node)** 라고도 한다.

대표적인 장치는 다음과 같다.

- PC
- Laptop
- Smartphone
- Server
- Router
- Layer 2 Switch
- Layer 3 Switch
- Gateway
- Firewall
- Wireless Access Point

최근에는 가상 환경에서도 장치가 존재한다.

예를 들어

- Virtual Router
- Virtual Firewall
- Virtual Machine
- Virtual Switch

등도 모두 네트워크 장치에 포함된다.

---

## 대표 장비 역할

|장비|역할|
|-----|-----|
|PC|사용자 장치|
|Server|서비스 제공|
|Router|서로 다른 네트워크 연결|
|Switch|같은 LAN 내부 장치 연결|
|Gateway|다른 네트워크와 연결|
|Firewall|보안 정책 적용|

---

# 4.2 Links (링크)

링크(Link)는 장치와 장치를 연결하는 매체이다.

링크는 크게 두 종류가 있다.

- Wired
- Wireless

---

## Wired (유선)

유선 연결 방식이다.

대표적인 매체

- UTP Cable
- STP Cable
- Optical Fiber
- Phone Line

예시

```
PC -------- Switch
```

### 장점

- 높은 속도
- 안정적인 통신
- 낮은 지연시간(Low Latency)
- 전파 간섭이 거의 없음

### 단점

- 케이블 설치 필요
- 이동이 어려움

---

## Wireless (무선)

무선은 케이블 대신 전파(Radio Wave) 또는 전자기파(Electromagnetic Signal)를 사용한다.

대표적인 기술

- Wi-Fi
- Bluetooth
- LTE
- 5G
- Zigbee

예시

```
Smartphone )))))
          Wi-Fi
             │
          Access Point
```

### 장점

- 이동 가능
- 설치가 간편
- 스마트폰 사용 가능

### 단점

- 전파 간섭 가능
- 유선보다 속도가 낮을 수 있음
- 보안 관리가 중요

---

# 4.3 Communication Protocols (통신 프로토콜)

프로토콜(Protocol)은

> **장치들이 서로 데이터를 주고받기 위해 반드시 따라야 하는 규칙(Rules)**

이다.

사람들이 같은 언어를 사용해야 대화할 수 있는 것처럼,

컴퓨터도 같은 프로토콜을 사용해야 통신할 수 있다.

대표적인 프로토콜

- TCP
- UDP
- IP
- HTTP
- HTTPS
- FTP
- SSH
- DNS
- DHCP
- ICMP

---

## TCP/IP Protocol Suite

현재 인터넷에서 사용하는 표준 프로토콜이다.

TCP/IP는 4개의 계층으로 구성된다.

|계층|역할|
|------|------|
|Application Layer|사용자 프로그램과 통신|
|Transport Layer|종단 간 데이터 전송|
|Internet Layer|IP 주소를 이용한 라우팅|
|Network Access Layer|실제 물리적 데이터 전송|

---

### 계층 구조

```
Application Layer
        │
Transport Layer
        │
 Internet Layer
        │
Network Access Layer
```

각 계층은 자신만의 역할을 수행하며 협력하여 데이터를 전달한다.

---

# 4.4 Network Security (네트워크 보안)

현대의 네트워크에서는 보안(Security)이 매우 중요하다.

목적

- 해킹 방지
- 악성코드 차단
- 비인가 사용자 차단
- 중요 정보 보호
- 서비스 안정성 확보

---

## Firewall

Firewall은 허용된 통신만 통과시키고 나머지는 차단하는 보안 장비이다.

```
Internet
    │
Firewall
    │
Internal Network
```

Firewall은 네트워크의 출입문 역할을 수행한다.

---

## IDS (Intrusion Detection System)

침입 탐지 시스템

역할

- 공격 탐지
- 로그 기록
- 관리자에게 경고

IDS는 공격을 탐지만 수행한다.

---

## IPS (Intrusion Prevention System)

침입 방지 시스템

역할

- 공격 탐지
- 공격 차단
- 패킷 삭제
- 연결 종료

IDS보다 한 단계 발전된 보안 시스템이다.

---

# 5. 컴퓨터 네트워크 전체 구조

```
                    Computer Network
                           │
        ┌──────────────────┼──────────────────┐
        │                  │                  │
     Devices             Links           Protocols
      (Node)       (Wired/Wireless)       (TCP/IP)
        │
        └──────────────────┐
                           │
                  Network Security
             Firewall / IDS / IPS
```

---

# 6. 핵심 용어 정리

|용어|설명|
|------|------|
|Node|네트워크에 연결된 장치|
|Device|네트워크 장비|
|Link|장치를 연결하는 매체|
|Protocol|통신 규칙|
|Packet|네트워크를 통해 전달되는 데이터|
|Firewall|네트워크 접근 제어 장비|
|IDS|침입 탐지 시스템|
|IPS|침입 방지 시스템|

---

# 7. 핵심 요약

- 컴퓨터 네트워크는 여러 장치를 연결하여 데이터를 주고받는 시스템이다.
- 네트워크는 **노드(Node)** 와 **링크(Link)** 로 구성된다.
- 링크는 **유선(Wired)** 과 **무선(Wireless)** 으로 나뉜다.
- 데이터는 **프로토콜(Protocol)** 이라는 규칙에 따라 전송된다.
- 인터넷에서는 **TCP/IP Protocol Suite**가 가장 널리 사용된다.
- TCP/IP는 **Application, Transport, Internet, Network Access**의 4계층으로 구성된다.
- 네트워크를 안전하게 운영하기 위해 **Firewall, IDS, IPS**와 같은 보안 장비를 사용한다.

---

# 참고

이 문서는 **컴퓨터 네트워크 기초(Network Fundamentals)** 강의 내용을 기반으로 정리한 학습 노트이다.