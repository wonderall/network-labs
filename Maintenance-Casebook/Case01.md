# VLAN 변경 작업 - PVID 불일치로 인한 통신 장애

## 작업 개요

부서 A가 다른 건물로 이동하여 부서 B와 동일한 네트워크 환경을 사용하게 되었다.

기존에는 서로 다른 서브넷과 VLAN을 사용하고 있었기 때문에, 이동한 부서 A의 네트워크 포트를 새로운 환경에 맞게 VLAN을 재구성해야 했다.

이에 따라 스위치에 신규 VLAN을 생성하고 해당 포트를 VLAN 멤버로 추가하였으나, 단말의 네트워크 통신이 이루어지지 않는 문제가 발생하였다.

---

## 작업 환경

- L2 Switch
- Access Port
- 신규 VLAN 생성
- 단말(PC)

---

## 증상

- 신규 VLAN 생성 완료
- 포트를 해당 VLAN의 멤버로 설정
- 단말 연결 상태 정상(Link Up)
- IP 설정 정상
- Gateway 통신 불가
- 동일 VLAN 내 통신 불가

---

## 원인 분석

초기에는 VLAN 생성 및 포트 멤버 설정을 확인하였으며, 설정상 이상은 발견되지 않았다.

이후 Access Port의 **PVID(Port VLAN ID)** 설정을 확인한 결과, 포트가 기존 VLAN의 PVID를 그대로 사용하고 있는 것을 확인하였다.

즉,

- VLAN Member : 신규 VLAN
- PVID : 기존 VLAN

으로 설정이 서로 일치하지 않아, 단말에서 들어오는 Untagged 패킷이 기존 VLAN으로 처리되고 있었다.

이로 인해 정상적인 VLAN 통신이 이루어지지 않았다.

---

## 조치 내용

- Access Port의 PVID를 신규 VLAN으로 변경
- VLAN Member와 PVID를 동일한 VLAN으로 설정
- 설정 적용 후 통신 테스트 수행

---

## 결과

- Gateway Ping 정상
- 동일 VLAN 통신 정상
- 네트워크 서비스 정상 이용 확인

---

## 트러블슈팅 과정

1. VLAN 생성 여부 확인
2. 포트 VLAN Member 확인
3. 포트 Link 상태 확인
4. IP 설정 확인
5. **PVID 설정 확인**
6. PVID 수정
7. 통신 정상 확인

---

## 배운 점

Access Port에서는 VLAN Member만 설정하는 것으로는 충분하지 않으며, **PVID 또한 동일한 VLAN으로 설정되어야 Untagged 패킷이 올바른 VLAN으로 처리된다.**

VLAN 변경 작업 시에는 다음 항목을 함께 확인하는 것이 중요하다.

- VLAN 생성 여부
- VLAN Member 설정
- PVID 설정
- 단말 IP 및 Gateway 설정
- 통신 테스트(Ping)

---

## 핵심 원인

**VLAN Member는 변경되었지만 PVID가 기존 VLAN으로 설정되어 있어 Untagged 패킷이 잘못된 VLAN으로 분류된 것이 통신 장애의 원인이었다.**