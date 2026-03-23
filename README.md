# 안녕하세요, 김영준입니다 👋

> 데이터 정합성과 시스템 안정성에 집착하는 백엔드 개발자입니다.  
> 단순히 동작하는 것에 만족하지 않고, 장애 상황까지 설계합니다.

<br>

## 🛠 Tech Stack

**Backend**  
![Java](https://img.shields.io/badge/Java-007396?style=flat-square&logo=openjdk&logoColor=white)
![Spring Boot](https://img.shields.io/badge/Spring_Boot-6DB33F?style=flat-square&logo=springboot&logoColor=white)

**Database**  
![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=flat-square&logo=mysql&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat-square&logo=postgresql&logoColor=white)
![Redis](https://img.shields.io/badge/Redis-DC382D?style=flat-square&logo=redis&logoColor=white)

<br>

## 📂 Projects

### 🔖 KEEPING
> QR 기반 디지털 장부 선결제 서비스 `2025.08 ~ 2025.10` `2026.01 ~ 2026.02`

- 모놀리스에서 QR 결제 서버를 분리하고 **ACL 패턴** 적용 → 배포 독립성 확보
- Webhook 기반 Push 캐싱(Event-Driven)으로 결제 응답시간 **86% 단축** (1,923ms → 262ms)
- 멱등성 키 + 상태 플래그 기반 **3단계 자동 복구 전략** 설계 → 추가 인프라 비용 없이 데이터 정합성 보장
- B-Tree 복합 인덱스 최적화 → 10만건 데이터 탐색 성능 **98% 개선** (2,075ms → 24ms)
- Micrometer Tracing으로 분산 서비스 간 **End-to-End TraceId 추적** 환경 구축 → 장애 분석 시간 83% 단축

<br>

### 🦎 REPTOPIA
> 파충류 이력 관리 기반 신뢰 거래 플랫폼 `2025.10 ~ 2025.12`

- **CQRS + Facade 패턴** 도입으로 순환 참조 및 도메인 강결합 해소
- Event-Driven 아키텍처로 Side-effect 처리 전환 → 도메인 간 결합도 50% 감소, 코드 40% 감축
- Elasticsearch 없이 **PostgreSQL GIN / GiST 인덱스**만으로 Full-text 검색 파이프라인 구축

<br>

### 🍉 MelonMe *(개발 중)*
> 현재 진행 중인 프로젝트

<br>

## 📊 GitHub Stats

<img height="160" src="https://github-readme-stats.vercel.app/api?username=welikeWatermelon&show_icons=true&theme=default&hide_border=true&count_private=true" />
<img height="160" src="https://github-readme-stats.vercel.app/api/top-langs/?username=welikeWatermelon&layout=compact&theme=default&hide_border=true" />

<br>

## 📬 Contact

[![Gmail](https://img.shields.io/badge/bill5500@naver.com-03C75A?style=flat-square&logo=naver&logoColor=white)](mailto:bill5500@naver.com)
[![GitHub](https://img.shields.io/badge/welikeWatermelon-181717?style=flat-square&logo=github&logoColor=white)](https://github.com/welikeWatermelon)
