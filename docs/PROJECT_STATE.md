# Project State

최종 갱신: 2026-10-19 (Asia/Seoul)

## 현재 위치

- Phase 1 — 프로젝트 기반 준비 / Repository·협업환경 구성 진행 중.
- 개발환경 확인 완료: 사용자가 첫 컨테이너 실행에 성공했고 Codex가 Docker 엔진·이미지를 재점검했다.
- 현재 폴더는 아직 Git Repository가 아니다. 초기 README, `.gitignore`, PR 템플릿과 상태 문서를 준비했으며 첫 Commit은 사용자가 변경 목록을 확인하고 직접 경험할 예정이다.
- 애플리케이션, Build 설정, DB, Migration, Test, CI, 배포환경은 아직 없다.

## 사용자와 확정한 방향

- 숙박 예약 웹서비스를 만들며 전체 웹서비스 개발 Lifecycle을 경험한다.
- 주요 기능: 회원 인증·인가, 숙소·객실 조회, 예약·취소, 예약 기간 중복 검증, 리뷰·평균 별점 관리.
- 핵심 학습 목표: 예약 트랜잭션, JPA 비관적 락을 통한 동시성 제어, 실제 DB 기반 동시 예약 통합 테스트.
- 개발 속도를 높이기 위해 CRUD, DTO, Mapper, 파일 생성, 단순 설정, 코드 조사, 테스트 실행, 오류 수정 등은 Codex가 적극 처리한다.
- 학습 가치가 높은 새로운 실무 절차는 사용자가 한 번 직접 경험하고 이후 반복 작업은 자동화한다.
- 중요한 요구사항·설계·기술 선택은 사용자와 결정한다. 확정 범위 안의 사소한 구현은 자율적으로 처리하고 관련 작업은 안전한 단위로 묶는다.
- Test, 실제 검증, Review, 상태 기록과 Lifecycle 완료 조건을 생략하지 않는다.

## 개발환경 점검 결과

아래는 2026-10-19에 실행한 명령의 결과다. 설치 확인과 실제 동작 확인을 구분한다.

| 항목 | 확인 결과 | 근거 |
| --- | --- | --- |
| OS | macOS 27.0.1 / Apple Silicon arm64 | `sw_vers`, `uname -sm` |
| Git | 2.56.0 실행 가능 | `git --version` |
| Git 기본 설정 | 작성자 이름·이메일 설정 있음, 초기 기본 Branch `main` | `git config --get` 조회 |
| 현재 Git Repository | 미초기화 | `git status --short --branch`에서 `not a git repository` |
| GitHub CLI | 2.102.0 설치, 인증 API 호출 성공 | 네트워크 접근을 허용한 `gh api user --jq .login` → `yeochang-yoon` |
| JDK | mise로 관리되는 Temurin 21.0.11, 컴파일·실행 성공 | `java -version`, `javac -version`, 임시 Java 파일의 `javac` → `java` 실행 |
| IDE | IntelliJ IDEA 및 VS Code 앱 설치 확인 | `/Applications`, `~/Applications`의 앱 이름 조회. IDE 내 JDK 연결은 미확인 |
| Docker CLI | 29.8.2 설치 | `docker --version` |
| Docker Compose | v5.5.0 설치 | `docker compose version` |
| Docker Runtime | OrbStack 서버 29.8.2 / aarch64 연결 성공, 첫 컨테이너 실행 성공 | 사용자 실행 결과 `Hello from Docker!`, Codex의 `docker info` 및 `docker image inspect hello-world` 성공 |
| SSH | OpenSSH 10.3p1 실행 가능 | `ssh -V`. GitHub SSH 연결은 미검증이며 원격 연결 방식은 미정 |

주의할 점:

- 제한된 실행환경의 `gh auth status`는 토큰 오류를 보고했으나, 네트워크 접근을 허용한 실제 API 호출은 성공했다. 이 결과만으로 재로그인이 필요하다고 판단하지 않는다.
- `/usr/libexec/java_home -V`는 JDK를 찾지 못했지만 PATH의 mise JDK로 컴파일·실행에 성공했다. 재설치는 필요하지 않으며 IDE 설정 시 실제 JDK 경로를 확인한다.
- 도구 버전은 설치 현황이다. 프로젝트의 Spring/Build Tool/DB 버전 및 Frontend 기술 선택을 확정한 것이 아니다.
- 최초 Docker 실행은 엔진 소켓이 없어 실패했으나 이후 사용자 실행은 성공했다. Codex의 재점검은 로컬 소켓 접근을 허용한 환경에서 수행했다.

## 이번 작업의 검증 및 Review

- `AGENTS.md`, `docs/DEVELOPMENT_PROCESS.md`를 읽고 실제 파일 목록과 대조했다.
- Java 임시 파일을 `/private/tmp`에 생성하여 컴파일·실행했다. 출력: `JDK compile/run OK: 21.0.11+10-LTS`.
- GitHub 실제 인증 API 조회 성공. Docker도 사용자 실행 결과와 엔진·이미지 조회 성공을 확인하여 개발환경 확인을 완료했다.
- Review: 사용자의 주요 기능·학습 목표·자동화 선호를 기록했고, 미확정 기술이나 요구사항을 확정으로 기록하지 않았다.
- 초기 README와 PR 템플릿을 준비했다. 협업 기본안은 `main` + 작업 Branch, Issue → PR → Review → 사용자 확인 후 Merge이며 Squash Merge를 제안한다.
- `.gitignore`는 OS·IDE·빌드 산출물·로컬 환경설정·키·로그를 제외하고 환경설정 예제 파일은 허용한다. `/private/tmp`의 임시 Git Repository와 현재 작업 폴더를 사용한 `git check-ignore --no-index -v --non-matching --stdin`으로 `.DS_Store`, IDE 파일, 빌드 산출물, `.env`, `.env.local`, 키 파일 제외와 환경설정 예제·README·PR 템플릿·Gradle Wrapper JAR 허용을 확인했다. 프로젝트 자체의 Git 초기화는 아직 수행하지 않았다.
- 애플리케이션이 없으므로 애플리케이션 Test/Build/CI 결과는 없다.

## 바로 다음 작업

1. 사용자가 `git init -b main` → 초기 파일을 명시한 `git add` → `git diff --cached`로 첫 변경을 검토 → 최초 Commit을 경험한다. 이후 Codex가 Commit 및 `.gitignore` 동작을 확인한다.
2. 원격 저장소 기본안은 `yeochang-yoon/stay-reservation-service`다. 사용자에게 Public / Private 선택을 받아 확정한 뒤 원격 생성·연결·첫 Push를 진행한다. 공개 범위는 아직 미정이며, 첫 Push 전에 포함 파일과 Secret 제외 여부를 확인한다.
3. Repository 구성 완료 조건을 확인한 뒤 Kickoff → MVP 요구사항 → 초기 설계 순서로 진행한다. 기능 목록은 방향이 정해진 상태이며 구체적인 예약·취소·리뷰 정책은 아직 미정이다.

원격 저장소 생성·공개, Push, Merge, 배포는 아직 수행하지 않았다.
