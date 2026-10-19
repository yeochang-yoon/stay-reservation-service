# Stay Reservation Service

실제 숙박 예약 플랫폼의 비즈니스 문제를 참고하여 독립적인 숙박 예약 웹서비스를 설계·개발·배포·운영합니다. Backend의 예약·재고·가격·권한·데이터 정합성을 중심으로 전체 Lifecycle을 경험합니다. 반복 작업은 자동화하되 서비스의 핵심 도메인을 과도하게 축소하지 않습니다.

## 주요 기능과 학습 목표

- 회원 인증·인가
- 숙소 및 객실 조회
- 객실 타입·날짜별 재고·가격 관리와 지역·날짜·인원 검색
- 예약·취소 및 예약 기간 중복 검증
- 예약·결제·취소·이용 상태와 숙소 관리자 권한
- 리뷰 및 평균 별점 관리
- 예약 트랜잭션, JPA 비관적 락을 활용한 동시성 제어
- 실제 RDBMS 기반 동시 예약 통합 테스트

첫 서비스 버전의 범위와 PG 테스트 연동·실패 재현용 모의 응답 테스트 병행은 [Kickoff](docs/KICKOFF.md)에서 승인됐습니다. 구체적인 비즈니스 정책은 [MVP 요구사항](docs/REQUIREMENTS.md)에서 검수 중이며 기술 구성은 설계 단계에서 결정합니다. PG 사업자와 연동 방식은 실제 테스트 환경의 지원 기능·접근 조건을 확인한 뒤 선택합니다.

## 현재 상태와 문서

개발환경·Repository / 협업환경·Project Kickoff를 마쳤으며 MVP 요구사항을 정의하고 있습니다. PR #4는 승인에 따라 Squash Merge했고 애플리케이션과 DB는 아직 생성하지 않았습니다.

- [작업 지침](AGENTS.md)
- [전체 개발 절차](docs/DEVELOPMENT_PROCESS.md)
- [현재 프로젝트 상태와 다음 작업](docs/PROJECT_STATE.md)
- [Project Kickoff 확정 범위](docs/KICKOFF.md)
- [MVP 요구사항과 정책 검수안](docs/REQUIREMENTS.md)

Build / Test / 실행 명령은 Backend 개발 기반 구축 후 실제 검증 결과와 함께 추가합니다.

## 협업 방식

1. GitHub Issue에 문제와 완료 조건을 기록합니다.
2. `main`에서 작업 Branch를 만듭니다. 이름은 `feat/<주제>`, `fix/<주제>`, `chore/<주제>`처럼 목적을 드러냅니다.
3. 관련 구현·Test·문서를 함께 변경하고 작업에 맞는 검증을 실행합니다.
4. Diff를 확인하고 Commit / Push 후 PR을 작성합니다. Commit 메시지는 `feat:`, `fix:`, `docs:`, `chore:` 등으로 변경 목적을 표시합니다.
5. PR의 Diff와 검증 근거를 Review하고 수정합니다. CI 도입 후에는 CI 결과도 확인합니다.
6. 사용자 확인 후 Merge합니다. Merge 방식의 기본안은 PR 하나를 Commit 하나로 남기는 Squash Merge입니다.

초기 문서와 저장소 기반은 최초 Commit으로 기록하고, 이후 변경부터 Branch / PR 흐름을 적용합니다. 간단한 Issue는 별도 템플릿 없이 목적과 완료 조건을 본문에 작성합니다.

조사·구현·설정·Git·PR 생성·검증은 Codex가 주도하고 사용자는 중요한 결정과 결과를 검수합니다. Merge, 중요한 GitHub 설정 변경, 운영 배포 및 데이터 삭제는 사용자 승인 후 진행합니다. 반복 작업은 자율적으로 처리하되 Test / CI / Review와 Lifecycle 완료 조건을 유지합니다.

DB 비밀번호, Token, API Key 등 Secret은 Commit하지 않습니다. 로컬 값은 Git에서 제외한 파일이나 환경변수로 관리하며, 설정 예제에는 실제 Secret을 넣지 않습니다.
