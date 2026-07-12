# Chapter 02. Packet Tracer - Basic DNS Lab

> **도메인 이름이 어떻게 IP 주소로 변환되는지 직접 구축하고 확인해 봅니다.**

---

# 학습 목표

이번 실습에서는 다음 내용을 학습합니다.

- DNS Server 구축
- Web Server 구축
- PC 설정
- DNS Record 등록
- Domain으로 웹 접속
- Simulation Mode에서 DNS Query 분석

---

# 실습 토폴로지

```

           +------------------+
           |      PC0         |
           |192.168.10.10/24  |
           +--------+---------+
                    |
                    |
          +---------+----------+
          |      Switch        |
          |      2960          |
          +---+------------+---+
              |            |
              |            |
     +--------+--+      +--+--------+
     | DNS Server|      |Web Server |
     |192.168.10.2|     |192.168.10.3|
     +-----------+      +-----------+

```

---

# IP 주소 설계

| 장비 | IP 주소 | 역할 |
|------|---------|------|
| DNS Server | 192.168.10.2 | DNS 서비스 |
| Web Server | 192.168.10.3 | HTTP 서비스 |
| PC0 | 192.168.10.10 | Client |

---

# 이번 실습에서 사용하는 도메인

```

www.company.com

```

DNS는

```

www.company.com

↓

192.168.10.3

```

으로 변환하도록 설정합니다.

---

# 실습 순서

① Switch 배치

② DNS Server 배치

③ Web Server 배치

④ PC 배치

⑤ 케이블 연결

⑥ IP 설정

⑦ DNS 설정

⑧ HTTP 확인

⑨ Simulation Mode 분석
