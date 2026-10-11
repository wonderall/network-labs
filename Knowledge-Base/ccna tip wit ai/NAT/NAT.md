
<img width="200" height="150" alt="animation-6gmh2ajh329" src="https://github.com/user-attachments/assets/310f2c4d-7243-429d-bafd-75f170f51c98" />

## IP 주소 고갈, NAT가 해결해 줄게! (feat. 스태틱 NAT)
인터넷을 사용하다 보면 우리는 수많은 기기와 연결돼. 그런데 이 모든 기기가 고유한 주소(IP 주소)를 가지고 있어야 한다면 어떨까? 마치 전 세계 모든 사람이 각자의 집 주소를 가지고 있듯이 말이야. 문제는 이 주소의 개수가 한정되어 있다는 거야. 그래서 등장한 기술이 바로 **NAT(Network Address Translation)**야. NAT는 마치 우리 집 대문 역할을 하는 것처럼, 내부의 여러 기기가 하나의 공용 주소를 통해 외부와 소통할 수 있게 해주는 마법 같은 기술이지. 이번 시간에는 NAT 중에서도 가장 기본이 되는 **스태틱 NAT**에 대해 애니메이션과 함께 쉽고 재미있게 알아보자!


## 1. IP 주소 고갈, 왜 문제일까?
<svg viewBox="0 0 800 600" xmlns="http://www.w3.org/2000/svg" preserveAspectRatio="xMidYMid meet">
  <!-- 배경 -->
  <rect width="800" height="600" fill="#f8f7f4" />

  <!-- 제목 -->
  <text x="400" y="44" text-anchor="middle" font-family="'Pretendard', sans-serif" font-size="24" font-weight="700" fill="#0a0a0a">IPv4 주소 고갈과 IPv6의 무한한 확장성</text>

  <!-- 아이콘 정의 -->
  <defs>
    <g id="phone">
      <rect x="-10" y="-18" width="20" height="36" rx="4" fill="none" stroke="currentColor" stroke-width="2"/>
      <circle cx="0" cy="12" r="2" fill="currentColor"/>
    </g>
    <g id="laptop">
      <rect x="-18" y="-12" width="36" height="22" rx="2" fill="none" stroke="currentColor" stroke-width="2"/>
      <line x1="-22" y1="12" x2="22" y2="12" stroke="currentColor" stroke-width="2" stroke-linecap="round"/>
    </g>
    <g id="iot">
      <circle cx="0" cy="0" r="12" fill="none" stroke="currentColor" stroke-width="2"/>
      <circle cx="0" cy="0" r="3" fill="currentColor"/>
      <path d="M -6 -6 Q 0 -10 6 -6" fill="none" stroke="currentColor" stroke-width="1.5"/>
    </g>
  </defs>

  <!-- IPv4 섹션 -->
  <g id="ipv4-group">
    <text x="230" y="160" text-anchor="middle" font-family="'Pretendard', sans-serif" font-size="18" font-weight="700" fill="#737373">IPv4 (약 43억 개)</text>
    <rect x="100" y="180" width="260" height="320" rx="8" fill="#f5f5f4" stroke="#e5e5e5" stroke-width="2" stroke-dasharray="8 4"/>
    
    <!-- 기존 블록들 (거의 가득 참) -->
    <g fill="#737373" opacity="0.6">
      <rect x="110" y="440" width="50" height="50" rx="4"/>
      <rect x="170" y="440" width="50" height="50" rx="4"/>
      <rect x="230" y="440" width="50" height="50" rx="4"/>
      <rect x="290" y="440" width="50" height="50" rx="4"/>
      
      <rect x="110" y="380" width="50" height="50" rx="4"/>
      <rect x="170" y="380" width="50" height="50" rx="4"/>
      <rect x="230" y="380" width="50" height="50" rx="4"/>
      <rect x="290" y="380" width="50" height="50" rx="4"/>

      <rect x="110" y="320" width="50" height="50" rx="4"/>
      <rect x="170" y="320" width="50" height="50" rx="4"/>
      <rect x="230" y="320" width="50" height="50" rx="4"/>
      <rect x="290" y="320" width="50" height="50" rx="4"/>

      <rect x="110" y="260" width="50" height="50" rx="4"/>
      <rect x="170" y="260" width="50" height="50" rx="4"/>
      <rect x="230" y="260" width="50" height="50" rx="4"/>
    </g>

    <!-- 마지막 남은 블록 채워짐 -->
    <rect x="290" y="260" width="50" height="50" rx="4" fill="#7c3aed" opacity="0">
      <animate attributeName="opacity" from="0" to="1" dur="1s" begin="1s" fill="freeze" />
    </rect>

    <!-- 연결 시도하는 기기 -->
    <g color="#7c3aed">
      <use href="#phone" x="230" y="100">
        <animateTransform attributeName="transform" type="translate" from="0 0" to="0 120" dur="1.5s" begin="2s" fill="freeze" />
      </use>
    </g>

    <!-- 경고 메시지 -->
    <g opacity="0">
      <rect x="140" y="210" width="180" height="40" rx="20" fill="#e11d48"/>
      <text x="230" y="230" text-anchor="middle" dominant-baseline="middle" font-family="'Pretendard', sans-serif" font-size="16" font-weight="700" fill="white">주소 부족 (Full)</text>
      <animate attributeName="opacity" from="0" to="1" dur="0.5s" begin="3.5s" fill="freeze" />
    </g>
  </g>

  <!-- IPv6 섹션 -->
  <g id="ipv6-group" opacity="0">
    <animate attributeName="opacity" from="0" to="1" dur="1s" begin="4.5s" fill="freeze" />
    <text x="570" y="160" text-anchor="middle" font-family="'Pretendard', sans-serif" font-size="18" font-weight="700" fill="#7c3aed">IPv6 (약 340간 개)</text>
    <rect x="440" y="180" width="260" height="320" rx="8" fill="#f5f5f4" stroke="#7c3aed" stroke-width="2"/>
    
    <!-- 광활한 그리드 배경 -->
    <pattern id="grid" width="20" height="20" patternUnits="userSpaceOnUse">
      <path d="M 20 0 L 0 0 0 20" fill="none" stroke="#e5e5e5" stroke-width="0.5"/>
    </pattern>
    <rect x="445" y="185" width="250" height="310" fill="url(#grid)" />

    <!-- 기기들이 자유롭게 연결되는 애니메이션 -->
    <g color="#7c3aed">
      <!-- 기기 1 -->
      <g>
        <use href="#phone" x="500" y="50" opacity="0.8"/>
        <animateMotion path="M 0 0 L 0 200" dur="3s" begin="5s" repeatCount="indefinite" />
      </g>
      <!-- 기기 2 -->
      <g>
        <use href="#laptop" x="570" y="50" opacity="0.8"/>
        <animateMotion path="M 0 0 L 0 250" dur="4s" begin="5.5s" repeatCount="indefinite" />
      </g>
      <!-- 기기 3 -->
      <g>
        <use href="#iot" x="640" y="50" opacity="0.8"/>
        <animateMotion path="M 0 0 L 0 300" dur="3.5s" begin="6s" repeatCount="indefinite" />
      </g>
      <!-- 기기 4 -->
      <g>
        <use href="#phone" x="540" y="50" opacity="0.8"/>
        <animateMotion path="M 0 0 L 0 180" dur="2.5s" begin="6.5s" repeatCount="indefinite" />
      </g>
    </g>

    <!-- 성공 메시지 -->
    <g>
      <rect x="480" y="210" width="180" height="40" rx="20" fill="#059669"/>
      <text x="570" y="230" text-anchor="middle" dominant-baseline="middle" font-family="'Pretendard', sans-serif" font-size="16" font-weight="700" fill="white">무한한 연결 가능</text>
    </g>
  </g>

  <!-- 하단 설명 -->
  <text x="400" y="550" text-anchor="middle" font-family="'Pretendard', sans-serif" font-size="14" fill="#737373">IPv4의 한계를 넘어, IPv6는 모든 사물에 고유 주소를 부여할 수 있는 공간을 제공합니다.</text>
</svg>

옛날에는 IP 주소가 넉넉할 줄 알았어. 마치 작은 마을에 집이 몇 채 없어서 주소가 충분했던 것처럼 말이야. 하지만 인터넷이 폭발적으로 성장하면서 전 세계 모든 기기가 IP 주소를 필요로 하게 됐지. 우리가 쓰는 **IPv4 주소**는 32비트 크기라서 약 43억 개 정도밖에 만들 수 없어 . 이건 마치 43억 개의 집 주소만 만들 수 있는데, 전 세계 수십억 명의 사람들이 각자 여러 개의 기기를 쓰는 상황과 같아. 결국, 주소가 부족해지는 **IP 고갈 문제**가 발생한 거야 .

이 문제를 해결하기 위해 여러 방법이 나왔어.


- **서브네팅(Subnetting)**: 큰 네트워크를 작은 네트워크로 쪼개서 IP 주소를 효율적으로 사용하는 방법이야 . 마치 큰 땅을 여러 필지로 나누는 것과 같지.
- **CIDR(Classless Inter-Domain Routing)**: IP 주소를 더 유연하게 쪼개서 사용하는 기술이야 . 예전에는 피자를 똑같은 크기로만 잘랐다면, CIDR은 먹는 사람 수에 따라 피자 조각 크기를 다르게 자르는 것과 비슷해 .
- **DHCP(Dynamic Host Configuration Protocol)**: IP 주소를 필요한 기기에만 잠시 빌려주고, 사용하지 않을 때는 회수해서 다른 기기에 다시 빌려주는 기술이야 . 마치 도서관에서 책을 빌려주고 반납받는 것처럼 말이야.
- **사설 IP(Private IP)**: 회사나 집 같은 내부 네트워크에서만 자유롭게 사용할 수 있는 IP 주소 대역이야 . 이 주소는 인터넷에서는 사용할 수 없어. 마치 우리 집 안에서만 통하는 우리 가족만의 비밀 주소 같은 거지 .
- **IPv6**: IPv4의 한계를 극복하기 위해 나온 차세대 IP 주소 체계야. 128비트 크기라서 거의 무한대에 가까운 주소를 만들 수 있어 . 마치 우주 전체에 집 주소를 부여할 수 있는 것과 같아.
이런 노력에도 불구하고, 당장 IPv4 주소 고갈 문제를 해결하기 위해 가장 널리 쓰이는 기술 중 하나가 바로 **NAT**야.


## 2. NAT, 우리 집 대문지기!


NAT는 **네트워크 주소 변환(Network Address Translation)**의 줄임말이야 . 쉽게 말해, 우리 집 안에서 쓰는 주소(사설 IP)를 외부 인터넷에서 통하는 주소(공인 IP)로 바꿔주는 기술이지. 마치 우리 집 안에 여러 가족 구성원(사설 IP)이 있는데, 외부 우체부(인터넷)는 우리 집 대문(NAT 장비)의 주소(공인 IP)만 알고 편지를 배달하는 것과 같아.

NAT는 크게 두 가지 주소를 변경해.


- **출발지 주소(Source Address)**: 내부에서 외부로 나갈 때, 사설 IP를 공인 IP로 바꿔줘 .
- **목적지 주소(Destination Address)**: 외부에서 내부로 들어올 때, 공인 IP를 다시 사설 IP로 바꿔줘 .
이렇게 주소를 바꿔주는 덕분에 우리는 몇 안 되는 공인 IP 주소로도 수많은 내부 기기가 인터넷을 사용할 수 있게 돼. 마치 하나의 대문으로 온 가족이 드나드는 것처럼 말이야.

NAT는 크게 세 가지 방식으로 나눌 수 있어 .


- **스태틱 NAT(Static NAT)**: 1대1로 고정해서 주소를 바꿔주는 방식이야 .
- **다이나믹 NAT(Dynamic NAT)**: 여러 개의 사설 IP가 여러 개의 공인 IP 중 하나를 동적으로 할당받아 사용하는 방식이야 .
- **PAT(Port Address Translation)**: 하나의 공인 IP로 여러 사설 IP가 동시에 인터넷을 사용할 수 있게 해주는 방식이야. 포트 번호를 이용해서 구분하기 때문에 **NAT 오버로드**라고도 불려 .
이번 시간에는 이 중에서 **스태틱 NAT**에 대해 더 자세히 알아볼 거야.


## 3. 스태틱 NAT: 1대1 고정 매핑의 정석


**스태틱 NAT**는 이름처럼 **정적(Static)**으로, 즉 **고정적으로 1대1 매핑**을 해주는 방식이야 . 특정 사설 IP 주소는 항상 특정 공인 IP 주소로만 변환되도록 미리 정해두는 거지. 마치 우리 집 특정 방에 사는 사람이 항상 특정 대문으로만 드나들도록 정해두는 것과 같아.


- **장점**:
  - **양방향 통신 가능**: 외부에서 특정 공인 IP로 접속하면, 항상 정해진 내부 사설 IP로 연결되기 때문에 외부에서 내부 서버로 접속하는 것이 가능해 . 그래서 웹 서버나 블로그 서버처럼 외부에 서비스를 제공해야 하는 장비에 주로 사용돼 .
  - **항상 존재**: NAT 테이블에 항상 고정적으로 정보가 남아있어 . 마치 우리 집 대문 주소가 항상 똑같은 것처럼 말이야.

- **단점**:
  - **IP 주소 절약 효과 미미**: 1대1로 매핑하기 때문에 공인 IP 주소를 많이 절약할 수 없어 . 만약 내부 기기가 100대라면 공인 IP도 100개가 필요하게 되는 거지.
스태틱 NAT를 설정할 때는 **인사이드(Inside)**와 **아웃사이드(Outside)**라는 개념을 알아야 해 .


- **인사이드(Inside)**: 내부 네트워크 쪽을 의미해. 우리 집 안쪽이라고 생각하면 돼 .
- **아웃사이드(Outside)**: 외부 네트워크 쪽을 의미해. 우리 집 바깥쪽, 즉 인터넷이라고 생각하면 돼 .
그리고 주소를 표현할 때는 좀 더 세분화된 용어를 사용해 .


- **인사이드 로컬 주소(Inside Local Address)**: 내부 네트워크 안에서 바라본 사설 IP 주소야 .
- **인사이드 글로벌 주소(Inside Global Address)**: 외부 네트워크에서 바라본 공인 IP 주소야 .
예를 들어, 내부 IP가 10.1.1.1이고 이것이 200.1.1.1로 변환된다면, 10.1.1.1은 인사이드 로컬 주소, 200.1.1.1은 인사이드 글로벌 주소가 되는 거야.

스태틱 NAT는 설정이 매우 간단해 . 라우터 인터페이스에 인사이드/아웃사이드를 지정하고, ip nat inside source static [인사이드 로컬 주소] [인사이드 글로벌 주소] 명령어를 입력하면 끝이야 . 이렇게 설정된 NAT 테이블은 통신이 없어도 항상 존재하며, 통신이 발생하면 해당 통신에 대한 동적인 정보(다이나믹 엔트리)가 추가돼 . 이 동적인 정보는 일정 시간(기본 24시간) 동안 통신이 없으면 자동으로 삭제되지만, 스태틱으로 설정된 고정 매핑 정보는 계속 남아있어 .

스태틱 NAT는 IP 주소 절약 효과는 적지만, 외부에서 내부 서버로의 접근이 필요한 경우에 아주 유용하게 사용되는 중요한 기술이야.
