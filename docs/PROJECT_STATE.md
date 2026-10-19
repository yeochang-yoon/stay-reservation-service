# Project State

최종 갱신: 2026-10-19 (Asia/Seoul)

## 현재 위치

- Phase 1 — 프로젝트 기반 준비 / **Project Kickoff 범위 개정안 검수 대기**.
- 개발환경 확인 완료: 사용자가 첫 컨테이너 실행에 성공했고 Codex가 Docker 엔진·이미지를 재점검했다.
- 사용자가 로컬 Git 초기화·Staging·첫 Commit을 완료했다. 초기 Commit은 `3bb164c` (`chore: initialize project documentation`)다.
- 원격은 `https://github.com/yeochang-yoon/stay-reservation-service.git`, 공개 범위는 사용자 결정에 따라 Private이다. 이미 존재하던 빈 원격에 Codex가 `main` 첫 Push와 upstream 연결을 완료했다.
- Repository / 협업환경 구성 완료: 초기 문서·Git 제외 규칙·PR 템플릿, Issue → Branch → Commit → Push → PR → Review → 사용자 승인 후 Merge 흐름을 실제로 확인했다.
- [PR #2](https://github.com/yeochang-yoon/stay-reservation-service/pull/2)는 사용자 조건부 승인에 따라 문서 4개·검증 통과를 재확인하고 Squash Merge했다. Merge Commit은 `daf6eb1`이며 로컬 main·origin/main·GitHub API의 main SHA가 동일함을 확인했다. 연결된 Issue #1도 종료됐다.
- 현재 작업은 [Issue #3](https://github.com/yeochang-yoon/stay-reservation-service/issues/3), Branch `docs/3-project-kickoff`의 [Kickoff 개정안](KICKOFF.md)이다. [PR #4](https://github.com/yeochang-yoon/stay-reservation-service/pull/4)의 기존 축소안과 Merge는 사용자가 승인하지 않았다. 같은 PR을 Draft로 전환하고 개정안을 반영해 검수받으며 Merge는 수행하지 않는다.
- 애플리케이션, Build 설정, DB, Migration, Test, CI, 배포환경은 아직 없다.

## 사용자와 확정한 방향

- 실제 숙박 플랫폼의 비즈니스 문제를 참고하되 독립적인 숙박 예약 웹서비스를 설계·개발·배포·운영한다. 속도 향상은 작업 자동화의 목표이며 핵심 도메인 축소의 근거가 아니다.
- Backend 중심으로 현실적인 예약·재고·가격·권한·예외·데이터 무결성·통합 테스트를 다룬다. Frontend는 실제 주요 기능을 이용·검증할 수 있게 만들고 시각적 완성도는 후순위로 둔다.
- 주요 기능: 회원 인증·인가, 숙소·객실 조회, 예약·취소, 예약 기간 중복 검증, 리뷰·평균 별점 관리.
- 핵심 학습 목표: 예약 트랜잭션, JPA 비관적 락을 통한 동시성 제어, 실제 DB 기반 동시 예약 통합 테스트.
- 사용자는 Java / Spring 게시판, 기본 CRUD, Controller-Service-Repository, JPA와 기본 Git 작업을 경험했다.
- Codex가 조사·구현·설정·Git·Issue / Branch / Commit / Push / PR 생성·Test 실행·오류 수정·문서 갱신을 직접 주도한다. 사용자 직접 실행이 반드시 필요한 경우 또는 사용자가 원하는 경우에만 수동 작업을 안내한다.
- 사용자는 중요한 결정과 설계·구현·검증 결과를 검수한다. 새로운 주제도 무조건 수동 실습으로 넘기지 않는다. 핵심 학습 목표는 설계 근거와 실제 DB 기반 테스트 결과를 검수할 수 있게 한다.
- 중요한 요구사항·설계·기술 선택은 사용자와 결정한다. 확정 범위 안의 사소한 구현은 자율적으로 처리하고 관련 작업은 안전한 단위로 묶는다.
- Test, 실제 검증, Review, 상태 기록과 Lifecycle 완료 조건을 생략하지 않는다.
- `확인`, `진행`, `계속` 응답은 별도 의사결정이 필요 없는 다음 작업을 자율 진행하라는 뜻이다. 중요한 GitHub 설정·Merge·운영 배포·데이터 삭제 등은 구체적인 사용자 승인을 받는다.
- 보고는 **완료한 작업 / 다음 작업 / 내 확인이 필요한 사항**으로 구분하고, 마지막 항목에는 결정·승인이 필요한 이유와 추천안을 제시한다.

## 현재 검수할 범위 개정안

- 기존 실물 객실 1개·결제 없는 즉시 확정·초기 데이터만 제공하는 축소안은 미채택이다. 핵심 도메인을 유지한 범위를 다시 검토한다.
- 추천: 객실 타입별 날짜 수량 재고와 판매 중지, 지역·기간·인원 검색, 날짜·인원별 가격과 예약 당시 조건 보존, 예약·결제·만료·취소·환불 정합성.
- 숙소 관리자 역할과 담당 숙소·타입·재고·가격·예약·실제 이용 관리, 최소 서비스 관리자 기능, 이용 완료 연계 리뷰·평점을 포함하도록 제안한다.
- 결제는 PG 테스트 연동과 지연·중복·실패·응답 유실·취소 실패를 재현하는 모의 응답 테스트 병행을 추천한다. 자체 모의 결제만 제공·현장결제·실결제의 장단점과 한계도 비교했다. 결제 방식과 PG 사업자는 미확정이다.
- 첫 버전 경계 추천은 국내·원화·박 단위·예약당 한 타입의 객실 1개다. 타입별 공급 수량은 여러 개이며 날짜별 재고 문제를 유지한다. 호실별 PMS·일괄 다객실·다중 요금제·PG 실결제/정산·외부 채널 연동은 제한과 도입 경로를 명시한 후속 범위로 제안한다.
- 모든 개정 범위는 사용자 검수 대기다. 날짜·인원·취소·리뷰·데이터 보존의 상세 Business Rule과 ERD·API·기술·트랜잭션/락 설계는 뒤 단계에서 결정한다. 현재는 구현하지 않는다.

## 개발환경 점검 결과

아래는 2026-10-19에 실행한 명령의 결과다. 설치 확인과 실제 동작 확인을 구분한다.

| 항목 | 확인 결과 | 근거 |
| --- | --- | --- |
| OS | macOS 27.0.1 / Apple Silicon arm64 | `sw_vers`, `uname -sm` |
| Git | 2.56.0 실행 가능 | `git --version` |
| Git 기본 설정 | 작성자 이름·이메일 설정 있음, 초기 기본 Branch `main` | `git config --get` 조회 |
| 현재 Git Repository | `main` 초기 Commit 완료, Private 원격 Push 성공 | `git log`, `git ls-files`, `git push -u origin main`, GitHub API의 원격 main SHA 확인 |
| GitHub CLI | 2.102.0 설치, 인증 API 호출 성공 | 네트워크 접근을 허용한 `gh api user --jq .login` → `yeochang-yoon` |
| JDK | mise로 관리되는 Temurin 21.0.11, 컴파일·실행 성공 | `java -version`, `javac -version`, 임시 Java 파일의 `javac` → `java` 실행 |
| IDE | IntelliJ IDEA 및 VS Code 앱 설치 확인 | `/Applications`, `~/Applications`의 앱 이름 조회. IDE 내 JDK 연결은 미확인 |
| Docker CLI | 29.8.2 설치 | `docker --version` |
| Docker Compose | v5.5.0 설치 | `docker compose version` |
| Docker Runtime | OrbStack 서버 29.8.2 / aarch64 연결 성공, 첫 컨테이너 실행 성공 | 사용자 실행 결과 `Hello from Docker!`, Codex의 `docker info` 및 `docker image inspect hello-world` 성공 |
| SSH | OpenSSH 10.3p1 실행 가능 | `ssh -V` 실행. 현재 원격 연결은 HTTPS와 gh 인증 helper를 사용하므로 GitHub SSH 연결은 불필요 |

주의할 점:

- 제한된 실행환경의 `gh auth status`는 토큰 오류를 보고했으나, 네트워크 접근을 허용한 실제 API 호출은 성공했다. 이 결과만으로 재로그인이 필요하다고 판단하지 않는다.
- `/usr/libexec/java_home -V`는 JDK를 찾지 못했지만 PATH의 mise JDK로 컴파일·실행에 성공했다. 재설치는 필요하지 않으며 IDE 설정 시 실제 JDK 경로를 확인한다.
- 도구 버전은 설치 현황이다. 프로젝트의 Spring/Build Tool/DB 버전 및 Frontend 기술 선택을 확정한 것이 아니다.
- 최초 Docker 실행은 엔진 소켓이 없어 실패했으나 이후 사용자 실행은 성공했다. Codex의 재점검은 로컬 소켓 접근을 허용한 환경에서 수행했다.

## 누적 검증 및 Review

- `AGENTS.md`, `docs/DEVELOPMENT_PROCESS.md`를 읽고 실제 파일 목록과 대조했다.
- Java 임시 파일을 `/private/tmp`에 생성하여 컴파일·실행했다. 출력: `JDK compile/run OK: 21.0.11+10-LTS`.
- GitHub 실제 인증 API 조회 성공. Docker도 사용자 실행 결과와 엔진·이미지 조회 성공을 확인하여 개발환경 확인을 완료했다.
- 초기 Commit의 추적 대상이 문서·설정 6개 파일뿐임을 `git ls-files`와 `git show --stat HEAD`로 확인했다.
- GitHub API로 Private, 기본 Branch `main`, Issue 활성화, Squash Merge 지원을 확인했다. 협업 기본안은 `main` + 작업 Branch, Issue → PR → Review → 사용자 승인 후 Merge다. 저장소 설정은 변경하지 않았다.
- AGENTS.md, DEVELOPMENT_PROCESS.md, README에 Codex 주도·사용자 검수의 역할 분담을 반영했다. Diff Review에서 Lifecycle 순서·완료 조건·안전 원칙을 유지하고 미확정 기술이나 요구사항을 확정으로 기록하지 않았음을 확인했다.
- `.gitignore`는 OS·IDE·빌드 산출물·로컬 환경설정·키·로그를 제외하고 환경설정 예제 파일은 허용한다. 임시 Git Repository에서 예제 파일·README·PR 템플릿·Gradle Wrapper JAR 허용을 확인했고 실제 프로젝트의 `git check-ignore -v`로 `.DS_Store`, `.env`, `.env.local`, IDE 파일 제외를 재확인했다.
- 상태 문서를 포함한 `git diff --check`와 로컬 Markdown 링크 3개 검증 통과. 개발 절차의 3~33절이 기존 내용과 동일하고 변경 대상이 Markdown 4개뿐임을 확인했다.
- 애플리케이션이 없으므로 애플리케이션 Test/Build/CI 결과는 없다.

## PR #4 최초안까지의 검증 이력

- PR #2 Merge 직전 검토한 HEAD가 `6a35002`와 동일하고 작업 폴더가 깨끗하며 변경 대상이 Markdown 4개뿐임을 재검증했다. Diff 검사·문서 링크 검사와 개발 절차 3~33절 보존 검사를 통과했다.
- 검토한 HEAD를 조건으로 Squash Merge했다. GitHub에서 `MERGED`, Issue #1 `CLOSED`, Merge Commit `daf6eb15636f8f2dabca084b88ae2cdc9b42a990`를 확인했다.
- Fetch → main 전환 → Fast-forward 동기화 성공. 다음 작업 Branch는 동기화한 main에서 만들었다.
- Kickoff는 범위 제안이며 아직 완료가 아니다. 로컬 문서 링크 7개와 변경 범위 Markdown 4개를 검증했고 개발 절차 문서가 main과 동일함을 확인했다. Diff 자체 Review에서 확정된 방향과 추천안을 구분하고 상세 정책·기술 선택을 뒤 단계로 남겼음을 확인했다.

## 이번 개정의 근거와 검증

- Booking.com 공개 재고·검색·주문 문서와 토스페이먼츠 멱등 요청·테스트 키 문서를 조사했다. 외부 기능의 도메인 근거이며 특정 서비스의 내부 아키텍처를 확인한 것은 아니다. 출처는 KICKOFF.md의 해당 설명에 연결했다.
- 기능별 비즈니스 역할·제외 영향, 포함/제외 판단, 결제 대안, 확장 경로와 검증 목표를 개정했다. 구현 방식이나 세부 정책을 확정하지 않는다.
- 개정 문서의 Diff 검사, 로컬 Markdown 링크 7개, 변경 범위 Markdown 4개, 개발 절차 문서와 main 미변경 검증을 통과했다. 외부 출처는 공개자료 조사로 확인했다.
- 자체 Review에서 요청한 목표·역할·시나리오·기능별 역할/제외 영향·도메인 문제·첫 버전/후속 범위·검증 기준과 상세 정책/설계 유보를 대조했다. 애플리케이션 Test/Build/CI는 실행하지 않았으며 향후 수용 기준과 실제 결과를 구분했다.

## 바로 다음 작업

1. 같은 Issue #3 / PR #4에 개정안·프로젝트 방향·상태를 반영하고 문서 검증·자체 Review 결과를 보고한다. 현재 Merge 승인은 없으며 추가 승인 없이 Merge하지 않는다.
2. 사용자가 서비스 범위와 결제 대안을 검수·결정한다. 변경이 필요하면 Kickoff를 계속 개정한다.
3. 범위 확정 후 별도 Merge 승인을 받아 통합하고 Kickoff 완료 조건을 확인한다. 그다음 MVP 요구사항 → 초기 설계 → Backend 기반 구축으로 진행한다.

Kickoff 변경의 Merge 및 애플리케이션 구현·배포는 아직 수행하지 않았다. CI는 Build / Test 방법이 정해진 뒤 절차 문서의 해당 단계에서 실제 성공·실패를 검증하며 도입한다.
