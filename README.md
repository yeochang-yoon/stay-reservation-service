# Stay Reservation Service

숙박 예약 웹서비스를 개발하며 요구사항, 설계, 개발, 검증, 협업, 배포, 운영 및 변경의 전체 Lifecycle을 경험하는 프로젝트입니다.

## 주요 기능과 학습 목표

- 회원 인증·인가
- 숙소 및 객실 조회
- 예약·취소 및 예약 기간 중복 검증
- 리뷰 및 평균 별점 관리
- 예약 트랜잭션, JPA 비관적 락을 활용한 동시성 제어
- 실제 RDBMS 기반 동시 예약 통합 테스트

구체적인 MVP 정책과 기술 구성은 요구사항·설계 단계에서 결정합니다.

## 현재 상태와 문서

개발환경 확인을 마쳤으며 Repository / 협업환경을 구성하고 있습니다. 애플리케이션과 DB는 아직 생성하지 않았습니다.

- [작업 지침](AGENTS.md)
- [전체 개발 절차](docs/DEVELOPMENT_PROCESS.md)
- [현재 프로젝트 상태와 다음 작업](docs/PROJECT_STATE.md)

Build / Test / 실행 명령은 Backend 개발 기반 구축 후 실제 검증 결과와 함께 추가합니다.

## 협업 방식

1. GitHub Issue에 문제와 완료 조건을 기록합니다.
2. `main`에서 작업 Branch를 만듭니다. 이름은 `feat/<주제>`, `fix/<주제>`, `chore/<주제>`처럼 목적을 드러냅니다.
3. 관련 구현·Test·문서를 함께 변경하고 작업에 맞는 검증을 실행합니다.
4. Diff를 확인하고 Commit / Push 후 PR을 작성합니다. Commit 메시지는 `feat:`, `fix:`, `docs:`, `chore:` 등으로 변경 목적을 표시합니다.
5. PR의 Diff와 검증 근거를 Review하고 수정합니다. CI 도입 후에는 CI 결과도 확인합니다.
6. 사용자 확인 후 Merge합니다. Merge 방식의 기본안은 PR 하나를 Commit 하나로 남기는 Squash Merge입니다.

초기 문서와 저장소 기반은 최초 Commit으로 기록하고, 이후 변경부터 Branch / PR 흐름을 적용합니다. 간단한 Issue는 별도 템플릿 없이 목적과 완료 조건을 본문에 작성합니다.

DB 비밀번호, Token, API Key 등 Secret은 Commit하지 않습니다. 로컬 값은 Git에서 제외한 파일이나 환경변수로 관리하며, 설정 예제에는 실제 Secret을 넣지 않습니다.
