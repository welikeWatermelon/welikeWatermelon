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
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat-square&logo=postgresql&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=flat-square&logo=mysql&logoColor=white)
![Redis](https://img.shields.io/badge/Redis-DC382D?style=flat-square&logo=redis&logoColor=white)

<br>

## 📂 Projects

### 🍈 MelonMe

> 인지 발달 치료사를 위한 치료 자료 공유 및 커뮤니티 플랫폼 `2026.01 ~ 2026.07`
> `Java` `Spring Boot` `Spring AI` `JPA` `PostgreSQL` `Redis`
> 백엔드 2 · 프론트 1 · 클라우드 2 · 디자이너 1 · PM 1
> 🔗 [melonnetherapists.com](https://www.melonnetherapists.com/) · MAU 29 → 타겟 10,000명 기준 인프라 설계

**담당** · 검색 · SSE 실시간 처리 · 운영/JVM 튜닝 · Claude Code 협업 환경

#### 검색 성능

- Full Table Scan과 정확 일치 검색의 한계를 **pg_trgm + GIN 인덱스**로 개선, 부분 문자열 검색에서도 인덱스 적용 → 응답 시간 **47% 단축**
- 검색 로직을 **Strategy 패턴**으로 추상화 → 데이터 증가·유사어 요구 시 `pgvector + OpenAI 임베딩 + HNSW`로 코드 수정 없이 전환 가능. 외부 검색 엔진 없이 성능 개선과 비용 절감

#### SSE 대규모 연결

- 톰캣 thread-per-request 구조에서 동시 SSE 연결이 **~6,000에서 OOM으로 다운**되는 문제를 **네티 event-loop 분리**로 해결 → 최대 동시 연결 **6,000 → 20,000+ (3.3배)**, 부하 시 스레드 **218 → 19 (91% 감소)**

#### 아키텍처 · 운영 안정성

- 도메인 간 순환 참조를 **Facade 패턴 + 도메인 Event**로 의존 방향 정리, DDD 원칙에 맞는 도메인 경계 확보
- `application.yml`에 **DB 연결 획득/쿼리 실행 이중 fail-fast 타임아웃** 적용 → 슬로우 쿼리·커넥션 풀 고갈의 장애 전파 차단
- JVM에 **OOM 힙덤프 자동 생성 + GC 로깅** 도입 → 장애 사후 분석과 GC 관측 가능

#### Claude Code 협업 환경

- main 브랜치에서 작업 명령 시 **다른 브랜치로 이동을 제안하는 보호 게이트** 설계 → 운영 코드 직접 변경 차단
- AI 코드 변경을 감지해 **날짜/명령/응답을 기록하는 로그 구조** 구축 → 모든 변경 내역 추적 가능

<br>

### 🔖 KEEPING

> QR 기반 디지털 장부 선결제 서비스 `2025.10 ~ 2025.12`
> `Java` `Spring Boot` `JPA` `MySQL` `Redis` `AWS`
> 백엔드 3 · 프론트 3

**담당** · QR 결제 서버 분리 · 캐싱 · 분산 환경 정합성

#### 성능

- QR 결제·지갑 서비스가 한 서버에 묶여 발생한 부하를 **서버 분리 + Redis 캐싱(Webhook 즉시 갱신)** 으로 해결 → 결제 저하 비율 **4.2배 → 1.74배**, 응답 시간 **1,084ms → 262ms**
- 커넥션 풀 부재로 인한 TIME_WAIT 누적·포트 고갈 위험을 **HttpClient5 커넥션 풀 + 벌크헤드**로 해소, **리틀의 법칙**으로 풀 크기 산정, `ss`·`tcpdump`로 연결 재사용 검증

#### 분산 환경 정합성

- 서버 분리로 발생한 중복 결제·잔액 차감 실패를 **멱등키 기반 중복 차단 + 미확정 상태 자동 복구**로 해결
- 매장별 선결제 포인트를 **충전 단위(Lot) FIFO 원장 + 조건부 원자 차감(단일 UPDATE 검증) + 비관락**으로 관리 → 동시 결제에도 정확한 잔액/유효기간 보장
- Webhook 메시지 순서 역전으로 오래된 데이터가 최신을 덮어쓰는 문제를 **버전 기반 순서 판별 + tombstone**으로 해결 → 캐시-원본 최종 일관성 보장
- 외부 PG(토스) 환불이 로컬 회수보다 먼저 실행돼 자금이 새는 경로를 **Saga 패턴(로컬 선커밋 → 외부 호출) + 멱등키·재시도**로 차단, 충전은 적립 실패 시 결제 취소로 설계 → 분산 트랜잭션 정합성 확보

#### 장애 격리 · 알림

- **Resilience4j 서킷브레이커**를 결제 쓰기/읽기/복구 경로별 독립 차단기로 분리, slow-call 기반 선제 감지로 타임아웃 누적 전 fail-fast → 장애 격리와 상태 복구 동시 확보
- 접속 상태별 알림 누락을 **SSE + FCM + DB 저장, 재연결 시 유실 이벤트 재전송**으로 해결 → 전 상태에서 알림 도달 보장

<br>

## 📬 Contact

[![Gmail](https://img.shields.io/badge/bill5500@naver.com-03C75A?style=flat-square&logo=naver&logoColor=white)](mailto:bill5500@naver.com)
<br>
