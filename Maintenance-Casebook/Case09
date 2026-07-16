# Case 10 - Genian NAC 동일 IP 중복 등록

## 개요
- **장비** : Genian NAC
- **증상** : 동일한 IP 주소가 2개의 Host로 등록됨
- **특이사항** : 두 Host의 **MAC 주소도 동일**하게 표시됨

---

## 장애 현상
- Genian NAC에서 동일한 IP가 중복으로 등록됨
- 동일한 MAC 주소를 가진 Host가 2개로 인식되어 관리 대상이 중복 생성됨

---

## 원인
정책 서버(Policy Server)의 **동작 모드(Operation Mode)** 가 **Host** 로 설정되어 있어 발생한 현상.

---

## 조치 내용

### 1. 정책 서버 동작 모드 변경
- 기존 : `Host`
- 변경 : `Inactive`

`Inactive`로 변경하면 정책 서버가 Host로 등록되지 않아 동일 IP 중복 등록 현상이 발생하지 않음.

### 2. 기존 중복 데이터 정리
각 노드를 확인하여 **정책 서버 IP 주소로 센싱되어 등록된 Host** 를 삭제.

또는

약 **30일이 지나면 자동으로 Aging되어 삭제**됨.

---

## 결과
- 동일 IP 중복 등록 현상 해결
- 정책 서버가 Host로 인식되지 않음
- 중복 Host 정보 제거 완료(또는 Aging 대기)

---

## 원인 분석

| 항목 | 내용 |
|------|------|
| 장애 증상 | 동일한 IP가 2개의 Host로 등록 |
| MAC 주소 | 동일 |
| 원인 | Policy Server 동작 모드가 `Host` |
| 해결 방법 | 동작 모드를 `Inactive`로 변경 |
| 추가 조치 | 정책 서버 IP로 등록된 Host 삭제 또는 30일 Aging 대기 |

---

## Lessons Learned
- Genian NAC 구축 시 Policy Server의 **Operation Mode**를 반드시 확인한다.
- Policy Server를 Host로 동작시키면 자기 자신을 Host로 센싱하여 중복 등록이 발생할 수 있다.
- 장애 발생 시 동일한 **IP와 MAC**이 중복 등록되어 있는지 먼저 확인하면 원인 분석에 도움이 된다.
