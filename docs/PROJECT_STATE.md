# Project State

최종 갱신: 2026-10-19 (Asia/Seoul)

## 현재 Lifecycle와 작업

- **Phase 2 — MVP 요구사항 정의 / 정책 검수 대기**.
- 개발환경·Repository / 협업환경·Project Kickoff 완료. 상세 요구사항·초기 설계·구현은 아직 완료하지 않았다.
- 현재 작업은 [Issue #5](https://github.com/yeochang-yoon/stay-reservation-service/issues/5), Branch docs/5-mvp-requirements의 [REQUIREMENTS.md](REQUIREMENTS.md)다. POL-01~12와 기능/수용 기준은 사용자 검수 대기다.
- 로컬/원격 main에는 PR #4까지 반영됐으며 현재 요구사항 초안과 상태 갱신은 별도 작업 Branch에서 진행한다.
- 애플리케이션·Build 설정·DB·Migration·기능 Test·CI·배포환경은 아직 없다.

## 사용자와 확정한 방향과 범위

- 실제 숙박 플랫폼의 비즈니스 문제를 참고하되 독립적인 Backend 중심 웹서비스를 설계·개발·배포·운영한다. 자동화·속도 향상은 핵심 도메인 축소의 근거가 아니다.
- 사용자는 Java/Spring 게시판·기본 CRUD·JPA·기본 Git 경험이 있다. Codex가 조사·구현·설정·Git·Issue/Branch/Commit/Push/PR·검증·오류 수정·문서 작업을 주도하고 사용자가 중요한 결정과 결과를 검수한다.
- Backend의 예약·재고·가격·권한·예외·데이터 무결성·실제 DB 통합 테스트를 중요하게 다룬다. Frontend는 주요 기능을 실제 이용·검증할 수준으로 만들며 외관은 후순위다.
- 2026-10-19 사용자가 [Kickoff](KICKOFF.md)의 개정 범위를 승인했다. 객실 타입별 다수/날짜 재고, 검색·가격, 예약·결제·취소, 숙소 관리자 공급 운영, 권한, 이용·리뷰, 동시성·무결성 검증을 첫 버전에 포함한다.
- 국내·원화·박 단위·예약당 한 타입의 객실 1개·단순한 초기 요금/취소 정책 경계에 동의했다. 후속 기능은 Kickoff의 제한·확장 경로를 따른다.
- PG 테스트 환경 연동과 실패 재현용 모의 응답 테스트 병행을 승인했다. **PG 사업자와 연동 방식은 미정**이다. 실제 승인·조회·취소·알림·접근 조건을 확인하고 설계하며 미지원 기능을 가정하지 않는다.
- **범위 승인은 상세 Business Rule·수치·상태 전이·DB·ERD·API·트랜잭션·락 설계 승인이 아니다.** 요구사항의 정책 검수와 이후 설계를 별도로 진행한다.
- Test·실제 검증·Review·CI·Lifecycle 완료 조건을 생략하지 않는다. 중요한 정책·기술·아키텍처는 검수받고 Merge·중요 GitHub 설정·운영 배포·데이터 삭제 등은 구체적인 승인을 받는다.
- 보고는 완료한 작업 / 다음 작업 / 내 확인이 필요한 사항으로 구분한다. 일반적인 확인/진행/계속은 별도 결정이 필요 없는 다음 작업 진행이며 미제시 위험 작업의 포괄 승인이 아니다.

## Git·협업 상태와 완료 근거

- 저장소: [yeochang-yoon/stay-reservation-service](https://github.com/yeochang-yoon/stay-reservation-service), **Private**, 기본 Branch main. origin은 HTTPS이며 gh 인증 helper로 Push/Fetch한다.
- 초기 Commit 3bb164c, PR #2의 진행 방식 문서 통합 daf6eb1. README·Git 제외 규칙·PR 템플릿과 Issue → Branch → Commit → Push → PR → Review → 승인 후 Merge 흐름을 실제 확인했다.
- [PR #4](https://github.com/yeochang-yoon/stay-reservation-service/pull/4)의 최초 축소안은 사용자가 승인하지 않았다. 실제 숙박 도메인으로 개정한 966fb2b를 검수한 후 범위 및 조건부 Squash Merge를 승인했다.
- Merge 직전 HEAD 966fb2b2fe5fc5fa09263d017b2359e30babcaeb, Markdown 4개 변경, 깨끗한 작업 폴더, Diff 검사·로컬 링크 7개·Lifecycle 미변경을 재확인했다.
- PR #4를 Ready로 전환하고 검토한 HEAD를 조건으로 Squash Merge했다. GitHub MERGED와 Issue #3 CLOSED를 확인했다.
- Merge Commit: **b618ce22c589dbcd3bcc400de58158f57c48e0b3**. Fetch → main 전환 → Fast-forward 후 로컬 main·origin/main·GitHub API SHA가 일치했다.
- 현재 요구사항 작업은 동기화된 main에서 새 Branch로 시작했다. 새 PR의 Merge 승인은 아직 없다.

## 개발환경 확인 결과

아래는 개발환경 확인 단계에서 실제 실행한 결과다. 현재 설치를 반복 점검하거나 재설치하지 않는다.

| 항목 | 확인 결과 |
| --- | --- |
| OS | macOS 27.0.1, Apple Silicon arm64 |
| Git / GitHub | Git 2.56.0, gh 2.102.0, 계정 API 조회 및 실제 Push/Fetch 성공 |
| JDK | mise Temurin 21.0.11, 임시 파일 javac/java 컴파일·실행 성공 |
| IDE | IntelliJ IDEA·VS Code 설치 확인. IDE 내 JDK 설정은 아직 미확인 |
| Docker | CLI/서버 29.8.2, Compose v5.5.0, OrbStack/aarch64. 사용자 hello-world 성공 및 엔진/이미지 재확인 |
| SSH | OpenSSH 10.3p1. GitHub 연결은 HTTPS를 사용하므로 SSH 인증은 불필요 |

제한된 환경의 gh 인증 오류는 네트워크 접근 허용 후 실제 조회로 해소됐다. macOS java_home은 JDK를 찾지 못했으나 mise JDK로 컴파일·실행 성공했다. 불필요한 재로그인·재설치가 필요하다고 판단하지 않는다. 도구 설치 버전은 프로젝트 기술 선택 확정이 아니다.

## 이번 요구사항 초안의 내용과 미확정 사항

- 승인 범위에서 도출되는 필수 불변 조건, 역할별 입력/출력·Validation, 기능 요구사항 ID, 업무 상태 전이, 정상·실패·권한·시간 경계·동시성 시나리오와 수용 기준을 연결한다.
- POL-01~12: 날짜/예약 한도, 인원/예약자, 공급 변경, 가격 재동의/고정, 선점/만료, 늦은/불확실 결제, 취소 금액, 재고 반환/환불 시점, 실제 이용/노쇼, 리뷰/평점, 관리자/사업자 취소, 탈퇴/기록을 추천·대안과 함께 검수받는다.
- 10분 선점·30일 리뷰 등 제안 수치는 아직 미확정이다. 취소 공제율표, 노쇼/조기퇴실, 항목별 보존 기간 등 미정 값도 남아 있다. 구조에 동의한 것만으로 숫자·예외를 확정하지 않는다.
- PG-GATE에서 실제 테스트 환경의 지원 기능·접근·정당성 확인·재시도/만료 제약을 설계 단계의 증거 확보 작업으로 인계한다. 특정 PG나 웹훅/서명을 가정하지 않는다.
- DB·트랜잭션·락 설계와 애플리케이션 구현을 시작하지 않았다. 현재 기능 검증 표는 향후 수용 기준이며 실행 결과가 아니다.

## 이번 문서 검증과 Review

- PR #4의 문서 검증과 Merge·동기화 결과는 위 실제 근거로 확인했다.
- 요구사항 초안의 로컬 문서 링크 12개, 고유 ID/상호 참조, Markdown 4개 변경 범위, Lifecycle 미변경과 main 동기화를 검증했다. 33개 기능 요구사항·8개 불변 조건·12개 정책안·25개 수용 시나리오를 연결했다.
- 자체 Review에서 Kickoff 핵심 범위와 추적표, 실패/권한/시간/동시성 경계, 취소·재예약 위험, 테스트/운영 데이터 분리, PG 미지원 기능 비가정과 미확정 정책 표시를 대조했다.
- 애플리케이션 Test/Build/CI 결과는 없다. 문서 검증을 기능 검증으로 보고하지 않는다.

## 다음 작업과 완료 조건

1. 요구사항 초안·범위 승인 기록·상태 문서의 통합 조건은 검증·Commit·Push·Draft PR 준비, 중요한 정책 검수와 별도 Merge 승인이다.
2. POL-01~12와 미정 수치·예외, 입력 제한·보존·상태 전이의 충돌을 해결하고 수용 기준을 확정한다. 필요한 개정과 Review를 반복한다.
3. 첫 Backend 기능을 선택할 정도로 요구사항이 명확한지 완료 조건을 확인한다. 별도 Merge 승인 후 통합하며 초기 설계 → Backend 기반 구축 순서로 진행한다.
4. PG 선정은 실제 지원 근거를 확보한 설계 단계에서 결정한다. CI는 절차의 해당 시점에 실제 성공·실패를 검증하며 도입한다.
