# Case 08. Aruba 7220 Controller 장애 분석 및 VRRP 기반 HA 구축

## 작업 개요

무선 AP를 다수 운영하는 사이트에서 갑자기 모든 AP의 무선 서비스가 중단되는 장애가 발생하였다.

현장에 방문하여 AP, PoE 스위치, Aruba Controller를 순차적으로 점검한 결과 Controller 장애를 확인하였으며, Controller를 재기동하여 서비스를 정상 복구하였다.

이후 동일 장애 발생 시 서비스 중단을 방지하기 위해 Aruba Mobility Master 환경에서 Aruba 7220 Controller를 VRRP 기반으로 이중화(HA) 구축하였다.

---

## 기존 구성

```text
                Mobility Master
                       │
               Aruba 7220 Controller
                       │
                 Core Switch
                       │
             ┌─────────┴─────────┐
             │         │         │
            AP1       AP2      AP...
```

- Controller 단일 운영
- Controller 장애 시 전체 AP 서비스 중단

---

## 장애 증상

- 다수의 AP 동시 서비스 중단
- 무선 단말 접속 불가
- AP PoE 정상 공급
- AP Link 정상
- 유선 네트워크 정상

---

## 장애 분석

먼저 AP와 연결된 PoE 스위치를 확인하였다.

다음 항목을 점검하였다.

- PoE 공급 상태
- Link 상태
- 인터페이스 상태

모두 정상으로 확인되었다.

이후 Aruba Controller 상태를 확인한 결과 Controller 장애가 발생하여 AP를 정상적으로 관리하지 못하고 있는 것을 확인하였다.

Controller를 재부팅한 후 AP가 다시 정상적으로 등록되었으며 무선 서비스가 복구되었다.

---

## 조치 내용

- Aruba Controller 상태 확인
- Controller 재부팅
- AP 재등록 확인
- 무선 서비스 정상 여부 확인

---

## 결과

- AP 정상 등록
- 무선 서비스 정상 복구
- 서비스 정상 운영

---

# 개선 작업

이번 장애를 계기로 Controller 단일 운영 구조의 위험성을 확인하였다.

동일 장애 발생 시 서비스 중단을 방지하기 위해 Aruba Mobility Master 환경에서 Aruba 7220 Controller를 추가하여 VRRP 기반 High Availability(HA)를 구축하였다.

---

## 개선 후 구성

```text
                        Mobility Master
                               │
              ┌────────────────┴────────────────┐
              │                                 │
      +------------------+             +------------------+
      | Aruba 7220 #1    |             | Aruba 7220 #2    |
      | Active           |             | Standby          |
      | 10.10.40.11      |             | 10.10.40.12      |
      +------------------+             +------------------+
              │                                 │
              └────────── VRRP ────────────────┘
                    Virtual IP : 10.10.40.10
                             │
                       Core Switch
                             │
                        AP 1 ~ AP N
```

---

## 구축 내용

- Aruba Mobility Master에서 Controller 관리
- HA Group 구성
- VRRP 구성
- Master Redundancy 구성
- Database Synchronization
- State Synchronization
- LMS / Backup LMS 설정

---

## 장애 전환(Failover) 테스트

Active Controller 장애를 가정하여 테스트를 수행하였다.

### 확인 내용

- VRRP Master 정상 변경
- Virtual IP 정상 이동
- AP 자동 재등록
- 무선 서비스 정상 유지

---

## 구축 결과

- Controller 이중화 완료
- VRRP 정상 동작
- AP Failover 정상
- 무선 서비스 연속성 확보
- 단일 장애 지점(SPOF) 제거

---

## 적용 기술

- Aruba Mobility Master
- Aruba 7220 Mobility Controller
- VRRP
- High Availability(HA)
- Master Redundancy
- State Synchronization
- Database Synchronization
- LMS / Backup LMS
- AP Failover

---

## 배운 점

- 다수의 AP가 동시에 장애를 일으키는 경우에는 AP 자체보다 Controller의 상태를 우선 확인해야 한다.
- Controller 단일 운영은 장애 발생 시 전체 무선 서비스 중단으로 이어질 수 있다.
- VRRP 기반 HA를 구축하여 Controller 장애 시 자동으로 Standby Controller가 서비스를 이어받을 수 있도록 개선하였다.
- 구축 후 실제 Failover 테스트를 수행하여 AP 자동 전환과 서비스 연속성을 확인하였다.

---

## 핵심 내용

**Aruba 7220 Controller 단일 운영 환경에서 Controller 장애로 인해 전체 AP 서비스가 중단되는 사례를 경험하였다. 장애 복구 후 Aruba Mobility Master 환경에서 VRRP 기반 HA를 구축하여 Controller 장애 시 AP가 자동으로 Standby Controller로 전환되도록 개선하였으며, 이를 통해 무선 네트워크의 가용성과 안정성을 향상시켰다.**

## 예시 구성(Config Example)

### Controller #1 (Active)

```bash
vlan 100
!

interface gigabitethernet 0/0/0
   switchport mode trunk
   switchport trunk allowed vlan 100,200,300
!

interface vlan 100
   ip address 10.10.40.11 255.255.255.0
!

database synchronize period 30
!

ha group-profile "HA-GROUP"
   state-sync
   pre-shared-key Example@123
   controller 10.10.40.11 role dual
   controller 10.10.40.12 role dual
!

ha group-membership "HA-GROUP"
!

master-redundancy
   master-vrrp 100
   peer-ip-address 10.10.40.12 ipsec Example@123
!

vrrp 100
   priority 110
   authentication Example@123
   ip address 10.10.40.10
   vlan 100
   preempt delay 0
!

ap system-profile "AP-PROFILE"
   lms-ip 10.10.40.11
   bkup-lms-ip 10.10.40.12
```

---

### Controller #2 (Standby)

```bash
vlan 100
!

interface gigabitethernet 0/0/0
   switchport mode trunk
   switchport trunk allowed vlan 100,200,300
!

interface vlan 100
   ip address 10.10.40.12 255.255.255.0
!

database synchronize period 30
!

ha group-profile "HA-GROUP"
   state-sync
   pre-shared-key Example@123
   controller 10.10.40.11 role dual
   controller 10.10.40.12 role dual
!

ha group-membership "HA-GROUP"
!

master-redundancy
   master-vrrp 100
   peer-ip-address 10.10.40.11 ipsec Example@123
!

vrrp 100
   priority 100
   authentication Example@123
   ip address 10.10.40.10
   vlan 100
   preempt delay 0
!

ap system-profile "AP-PROFILE"
   lms-ip 10.10.40.11
   bkup-lms-ip 10.10.40.12
```

---

## 주요 확인 명령어

```bash
show vrrp

show ha group-membership

show master-redundancy

show ap database

show ap active

show switches

show license

show running-config
```

---

## 동작 과정

```text
Controller #1 (Priority 110)
        │
        │ Master
        ▼
   Virtual IP
   10.10.40.10
        │
      AP 연결
        │
Controller 장애 발생
        │
        ▼
VRRP Master 변경
        │
Controller #2 (Priority 100)
        │
Virtual IP 이동
        │
AP 자동 재등록
        │
무선 서비스 지속
```

> **참고**
>
> 위 설정은 실제 운영 환경의 정보를 제거한 예시(Sanitized Configuration)이며, 실제 구축 시에는 VLAN ID, IP 주소, PSK, 인터페이스명 등을 운영 환경에 맞게 변경하여 적용하였다.
> 참고사이트 : https://www.youtube.com/watch?v=SLN8cLp-T9E