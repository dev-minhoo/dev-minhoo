## 권민후 · Backend Engineer

전자금융 도메인에서 정산·이체 트랜잭션을 다루는 6년차 백엔드 개발자입니다. "빠르게"보다 "틀리지 않게"가 먼저인 시스템을 주로 만들어 왔습니다.

### 주로 다뤄온 문제
- 되돌릴 수 없는 외부 연동에서의 멱등성 확보와 실패 지점별 보상 트랜잭션
- 대량 배치의 부분 실패 분리 · 선별 재처리 · 진행률 노출
- 외부 금융기관 잔액과 내부 원장의 대사, 기록 누락 자동 판정·보정
- 표준 스펙 기반 외부 연동과 OAuth 인증 서버 구축·운영
- 상환 스케줄 산출 등 금액 계산 로직의 경계 조건(말일 · 윤년 · 단수 처리)

`Java` `Spring Boot` `Spring Security` `JPA` `MyBatis` `MySQL` `PostgreSQL` `Redis` `Docker` `JUnit`

---

### 지금 하고 있는 것 — 분산 환경으로 넓히기
단일 DB 트랜잭션으로 풀어온 정합성 문제를 분산 환경에서는 어떻게 푸는지 직접 구현하며 정리하고 있습니다. 실무 코드가 아니라 문제만 가져와 새로 만듭니다.

**[payment-settlement-core](https://github.com/dev-minhoo/payment-settlement-core)**
- **완료** 결제 중복 방지 3중 방어 — DB 조회 → Redis 선점(SET NX + Lua 원자적 해제) → DB 유니크 제약. 동시 50요청 → 결제 1건을 테스트로 검증
- **진행 중** AWS 배포 (EC2 + RDS)
- **다음** Outbox + Kafka 이벤트 → Saga 보상 → 정산 배치 · 대사

**[backend-notes](https://github.com/dev-minhoo/backend-notes)** — 메시지 큐 · 분산 락 · 멱등성 학습노트
