# Case 09 - Genian NAC 동일 IP 중복 등록

## 개요
- **장비** : Genian NAC
- **증상** : 동일한 IP 주소가 2개의 올라옴
- **특이사항** : 두 Host의 **MAC 주소도 동일**하게 표시됨

---

## 장애 현상
- Genian NAC에서 동일한 IP가 중복으로 올라옴

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
- 동작 모드 host에서 inactive로 변경
- 다 노드 삭제 후 다시 올라오면 다시 등록 or 30일 기달려 자동 정리 or 노드맞아 센서가 정책서버로 잡혀있는것만 삭제 후 다시 등록

---

## 원인 분석

| 항목 | 내용 |
|------|------|
| 장애 증상 | 동일한 IP가 2개가 모니터로 올라옴 |
| 원인 | Policy Server 동작 모드가 `Host` |
| 해결 방법 | 동작 모드를 `Inactive`로 변경 |
| 추가 조치 | 정책 서버 IP로 등록된 센서 노드 삭제 또는 30일 Aging 대기 |

---

## Lessons Learned
- Genian NAC 구축 시 Policy Server의 **동작모드 inactive Mode**
- Policy Server를 Host로 동작시키면 센서처럼 동작 하여 동일 IP 두개 보임
