# Cisco Catalyst C3750-X 비밀번호 초기화

## 1. Password Recovery ENABLED (기존 설정 보존)

```text
switch: flash_init
switch: load_helper
switch: dir flash:
switch: rename flash:config.text flash:config.text.old
switch: boot
```

부팅 후 `N` 입력:
```text
Continue with the configuration dialog? [yes/no]: N
```

설정 복구 및 비밀번호 변경:
```text
Switch> enable
Switch# rename flash:config.text.old flash:config.text
Switch# copy flash:config.text system:running-config
```

확인 메시지마다 Enter 입력 후:
```text
Switch# configure terminal
Switch(config)# enable secret 새비밀번호
Switch(config)# end
Switch# copy running-config startup-config
Switch# reload
```

## 2. Password Recovery DISABLED (기존 설정 삭제)

**주의: 기존 설정 파일과 VLAN 데이터베이스가 삭제됨.**

초기화 확인 메시지에서 `Y` 입력:
```text
Would you like to reset the system back to the default configuration (y/n)? Y
```

이후:
```text
Switch: load_helper
Switch: dir flash:
Switch: boot
```

부팅 후 `N` 입력:
```text
Continue with the configuration dialog? [yes/no]: N
```

비밀번호 변경 및 저장:
```text
Switch> enable
Switch# configure terminal
Switch(config)# enable secret 새비밀번호
Switch(config)# end
Switch# copy running-config startup-config
```

## 주의사항

- **ENABLED:** 기존 설정 파일을 복구하여 설정을 유지할 수 있음.
- **DISABLED:** `Y` 입력 시 기존 설정 및 VLAN 데이터베이스 삭제.
- 스택 구성은 모든 구성원이 초기화된 뒤 설정을 복구할 것.
- `새비밀번호`는 실제 사용할 비밀번호로 변경할 것.
- 복구 후 관리 VLAN 인터페이스가 `shutdown` 상태인지 확인할 것.
