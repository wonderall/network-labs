# Network Design

## Design Goals

- 높은 가용성
- 장애 발생 시 서비스 지속
- 확장 가능한 구조
- 실제 기업망과 유사한 설계

---

## Building A

Layer2 중심의 Campus Network

적용 기술

- End-to-End VLAN
- PVST+
- Rapid STP
- EtherChannel
- HSRP
- EIGRP

특징

- VLAN이 모든 Access Switch까지 유지
- STP 기반 Loop 방지

---

## Building B

Distribution Layer에서 Routing 수행

적용 기술

- Local VLAN
- EtherChannel
- HSRP
- EIGRP

특징

- Layer3 Distribution
- STP 의존도 감소
- Broadcast Domain 축소

---

## Building C

Layer3 Switching 기반

적용 기술

- VLAN
- EIGRP

특징

- 모든 Routing을 L3 Switch 수행
- 간단한 구조