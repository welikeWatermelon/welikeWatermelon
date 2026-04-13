# 안녕하세요, 김영준입니다 👋

> 데이터 정합성과 시스템 안정성에 집착하는 백엔드 개발자입니다.  
> 단순히 동작하는 것에 만족하지 않고, 장애 상황까지 설계합니다.

Velog : [https://velog.io/@k_joon_
](https://velog.io/@k_joon_/posts)
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

- 모놀리스 서버에서 QR 결제 서버를 분리하고 **ACL 패턴** 적용 → 배포 독립성 확보
- Webhook 기반 Push 캐싱(Event-Driven)으로 결제 응답시간 **86% 단축** (1,923ms → 262ms)
- 멱등성 키 + 상태 플래그 기반 **3단계 자동 복구 전략** 설계 → 추가 인프라 비용 없이 데이터 정합성 보장
- B-Tree 복합 인덱스 최적화 → 데이터 탐색 성능 **98% 개선** (2,075ms → 24ms)
- Micrometer Tracing으로 분산 서비스 간 **End-to-End TraceId 추적** 환경 구축 → 장애 분석 시간 83% 단축

<br>

### 🦎 REPTOPIA
> 파충류 이력 관리 기반 신뢰 거래 플랫폼 `2025.10 ~ 2025.12`

**구현 기능**
- **CQRS + Facade 패턴** 도입으로 순환 참조 및 도메인 강결합 해소
- Event-Driven 아키텍처로 Side-effect 처리 전환 → 도메인 간 결합도 50% 감소, 코드 40% 감축
- Elasticsearch 없이 PostgreSQL GIN / GiST 인덱스만으로 검색 파이프라인 구축, 추가 인프라 비용 없이 검색 성능 확보

<br>

### 🍈 MellonMe *(개발 중 - CLAUDE AI 적극 활용)*
>치료사 전용 커뮤니티 플랫폼 `2026.03 ~`

**CLAUDE CODE**
- 도메인별 `/slash command` 17개 구축 (탐색 12 + 코드 생성 4 + 커밋 자동화 1) → 에이전트가  
컨벤션을 자동 참조하며 일관된 코드 생성
- 계층형 `CLAUDE.md`로 도메인별 컨텍스트 분리 (엔티티 규칙, DDD 경계 원칙, DTO/서비스       
컨벤션) → 불필요한 토큰 소비 제거
- Pre-commit Hook으로 시크릿 하드코딩 자동 차단 (`application-local.yaml` 스테이징 감지 +   
password/secret 패턴 검사)
- `PROGRESS.md` 기반 SubAgents → Team Agents 인수인계 구조 설계 → 세션 종료 후에도 컨텍스트 
재탐색 없이 즉시 작업 재개

**구현 기능**
- PostgreSQL `pg_trgm` GIN 인덱스 기반 **관련도 검색** 구축 — `similarity` 점수 + `ILIKE`   
병렬 조건으로 초성/텍스트 통합 검색, `numeric(10,8)` 캐스팅으로 커서 정밀도 보장
- **인기순 피드 무한스크롤** — `(popularityScore, id)` 복합 커서 기반 페이지네이션,
반응/스크랩 토글 시 점수 실시간 갱신
- **SSE 실시간 알림** — `@TransactionalEventListener` + `@Async` 전용 스레드풀,
Last-Event-ID 기반 유실 이벤트 자동 복구, 사용자당 다중 탭 커넥션 지원

<br>

## Claude Code Tokens Usage

![Claude Token Usage](https://raw.githubusercontent.com/welikeWatermelon/claude-usage/main/token-heatmap.svg)

<br>

## 🏆 Baekjoon

[![Solved.ac Profile](https://mazassumnida.wtf/api/v2/generate_badge?boj=bill5500&v=1)](https://solved.ac/bill5500)

<br>

## 📬 Contact

[![Gmail](https://img.shields.io/badge/bill5500@naver.com-03C75A?style=flat-square&logo=naver&logoColor=white)](mailto:bill5500@naver.com)
<br>
[![GitHub](https://img.shields.io/badge/welikeWatermelon-181717?style=flat-square&logo=github&logoColor=white)](https://github.com/welikeWatermelon)
