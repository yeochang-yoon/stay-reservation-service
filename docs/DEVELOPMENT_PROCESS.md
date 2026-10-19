# Web Service Development Process

## 1. 목적

이 문서는 하나의 웹서비스 프로젝트를 처음 시작하여 개발, 배포, 운영, 변경까지 진행할 때 따르는 **전체 Development Lifecycle과 프로젝트 공통 진행 원칙**을 정의한다.

프로젝트의 비즈니스 기능과 규모는 프로젝트마다 달라질 수 있다.

단순한 CRUD 서비스일 수도 있고, 예약·티켓팅처럼 더 복잡한 서비스일 수도 있다.

프로젝트의 기능이 단순하다는 이유로 개발 과정까지 생략하지 않는다.

목표는 원하는 기능을 가진 웹서비스를 만들면서 가능한 범위에서 실제 서비스 개발에 가까운 과정을 처음부터 끝까지 경험하는 것이다.

최종적으로 다음 흐름을 하나의 연결된 경험으로 만든다.

**개발환경 확인  
→ Repository / 협업환경 구성  
→ Kickoff  
→ 요구사항 정의  
→ 설계  
→ Backend 개발 기반 구축  
→ Backend 기능 개발  
→ Test / Review / CI 반복  
→ Backend 독립 검증  
→ Container  
→ Backend 배포  
→ Health / Logging / Monitoring  
→ Backend 운영  
→ Frontend 기술 선택  
→ Frontend 개발  
→ Backend / Frontend 통합  
→ 통합 검증  
→ 전체 웹서비스 배포  
→ 운영  
→ 기존 서비스 변경  
→ 재배포 / 운영 확인**

---

# 2. 프로젝트 전체 공통 원칙

## 2.1 현재 Lifecycle 단계에 집중한다

프로젝트는 현재 어느 Lifecycle 단계에 있는지 명확하게 유지한다.

각 단계에서는:

1. 현재 상태를 확인한다.

2. 이미 완료된 작업을 확인한다.

3. 현재 단계에서 필요한 작업을 진행한다.

4. 결과를 검증한다.

5. 완료 조건을 확인한다.

6. 완료 조건이 충족된 뒤 다음 단계로 이동한다.

현재 단계가 끝나지 않았다면 이유 없이 이후 단계의 작업을 먼저 진행하지 않는다.

---

## 2.2 필요한 개발 과정을 조용히 생략하지 않는다

프로젝트 규모가 작아도 필요한 개발 과정은 경험한다.

예를 들어 다음과 같은 방식으로 진행하지 않는다.

- 개발환경 확인 없이 바로 애플리케이션 구현

- Repository와 협업환경 준비 없이 기능 개발

- 요구사항 없이 Entity와 API부터 구현

- 필요한 설계 없이 코드부터 작성

- 테스트와 실제 검증 없이 구현 완료 처리

- Git / PR / Review 흐름 없이 계속 직접 main에 개발

- DB Schema 변경을 기존 DB 삭제로 해결

- 로컬 실행만 확인하고 프로젝트 종료

- 배포만 하고 운영 상태를 확인하지 않음

- 첫 배포 이후 서비스를 한 번도 변경하지 않음

- Backend만 완성하고 전체 웹서비스가 완료되었다고 판단

특정 단계를 생략하거나 크게 축소할 이유가 있다면 그 이유가 명확해야 한다.

---

## 2.3 프로젝트 전체를 한 번에 만들지 않는다

기능을 작은 작업 단위로 나누고 실제로 동작하는 결과를 반복해서 만든다.

기본적인 개발 흐름은 다음과 같다.

**작은 기능 선택  
→ 필요한 요구사항 / 설계 확인  
→ 구현  
→ 검증  
→ Review  
→ 통합  
→ 다음 기능**

한 번의 작업에서 프로젝트 전체를 구현하려 하지 않는다.

---

## 2.4 현재 필요하지 않은 기술은 미리 도입하지 않는다

기술은 실제 요구사항이나 해결해야 할 문제가 생겼을 때 도입한다.

현재 필요하지 않은 기술 때문에 개발을 중단하거나 구조를 불필요하게 복잡하게 만들지 않는다.

향후 검토할 가치가 있지만 지금 필요하지 않은 사항은 Backlog로 남길 수 있다.

---

## 2.5 구현 완료는 실제 검증 결과로 판단한다

코드가 작성되었다는 사실만으로 기능 완료로 판단하지 않는다.

현재 작업에 적절한 방법으로 실제 동작을 확인한다.

검증 방법은 상황에 따라 다음과 같을 수 있다.

- 자동화 Test

- Build

- 실제 HTTP 요청 / 응답

- 실제 DB 확인

- Migration 실행

- CI

- Container 실행

- Health Check

- 로그

- 배포된 환경의 실제 사용자 흐름

코드 작성자의 판단이나 단순 육안 검토만으로 동작을 보장하지 않는다.

---

# 3. 전체 Lifecycle

프로젝트는 기본적으로 다음 순서로 진행한다.

## Phase 1. 프로젝트 기반 준비

1. 개발환경 확인

2. Repository / 협업환경 구성

3. Project Kickoff

## Phase 2. 요구사항과 설계

4. MVP 요구사항 정의

5. 초기 설계

## Phase 3. Backend 개발

6. Backend 개발 기반 구축

7. 첫 Vertical Slice 개발

8. CI 기본 구성

9. Backend 기능 반복 개발

10. Backend 독립 검증 및 안정화

## Phase 4. Backend 배포와 운영

11. Container 구성

12. Backend 배포환경 구성

13. Backend Release / 배포

14. Health / Logging / Monitoring

15. Backend 운영 확인

## Phase 5. Frontend 개발

16. Frontend 기술 선택

17. Frontend 개발 기반 구축

18. Frontend 기능 개발

## Phase 6. 전체 웹서비스 통합

19. Backend / Frontend 통합

20. 통합 과정의 요구사항 변경

21. 전체 웹서비스 검증

## Phase 7. 전체 서비스 배포와 운영

22. 전체 웹서비스 배포

23. 운영 상태 확인

## Phase 8. 기존 서비스 변경

24. 배포 후 요구사항 변경

25. 기존 서비스 수정

26. Migration / Test / CI / 재배포

27. 운영 결과 확인

28. 문서 정리 및 회고

프로젝트 특성상 세부 순서는 조정될 수 있다.

하지만 전체 Lifecycle 경험의 목적을 훼손할 정도로 필요한 단계를 이유 없이 생략하지 않는다.

---

# 4. 개발환경 확인

## 목적

현재 개발 머신과 사용 가능한 도구를 파악하고 프로젝트를 정상적으로 진행할 수 있는 환경인지 확인한다.

애플리케이션부터 생성하지 않는다.

## 주요 작업

프로젝트에 필요한 범위에서 다음을 확인한다.

- 운영체제

- Git

- GitHub 사용 환경

- GitHub 인증

- JDK

- 사용할 수 있는 IDE

- Docker Runtime

- Docker Compose

- SSH

- 필요한 CLI

- 기타 현재 프로젝트에 필요한 개발 도구

Frontend 전용 환경은 실제 Frontend 단계가 되었을 때 필요한 수준으로 추가 확인한다.

## 진행 규칙

이미 설치되어 정상적으로 사용할 수 있는 도구를 이유 없이 다시 설치하지 않는다.

특정 IDE나 프로젝트 생성 방식을 미리 강제하지 않는다.

현재 환경에서 사용할 수 있는 도구를 먼저 파악하고 부족한 것만 준비한다.

## 완료 조건

다음 프로젝트 단계를 진행하는 데 필요한 기본 개발 도구와 현재 환경 상태를 알고 있으며 필요한 도구를 정상적으로 사용할 수 있다.

---

# 5. Repository / 협업환경 구성

## 목적

애플리케이션 코드뿐 아니라 Repository와 협업환경 역시 프로젝트의 일부로 처음부터 구성한다.

혼자 개발하더라도 실제 협업 프로젝트에서 사용하는 기본 흐름을 경험한다.

## 주요 작업

프로젝트 규모에 맞게 다음을 검토하고 구성한다.

- Git Repository

- GitHub Repository

- Repository 이름

- Public / Private

- 기본 Branch

- `.gitignore`

- README 초기 상태

- License 필요 여부

- Issue 관리 방식

- Branch 전략

- Branch naming

- Commit 방식

- Pull Request 방식

- Merge 방식

- PR Template 필요 여부

- Issue Template 필요 여부

- Label

- Repository Rules

- 기본 Secret 관리 원칙

## 진행 규칙

로컬에서 애플리케이션을 모두 만든 뒤 나중에 Repository를 붙이는 방식으로 생각하지 않는다.

반대로 실제 필요가 없는 복잡한 회사 규칙을 흉내내기 위해 과도한 협업 규칙을 추가하지 않는다.

## 완료 조건

첫 번째 실제 기능을 Issue → Branch → PR → Review → Merge 흐름으로 개발할 수 있는 Repository 기반이 준비되어 있다.

---

# 6. Project Kickoff

## 목적

무엇을 만들 것인지뿐 아니라 왜 만드는지와 이번 프로젝트의 범위를 명확하게 한다.

## 주요 작업

최소한 다음을 확인한다.

- 프로젝트가 해결하려는 문제

- 주요 사용자

- 핵심 사용 시나리오

- 서비스의 기본 성격

- 첫 MVP 범위

- 명확하게 제외할 범위

- 이번 프로젝트에서 경험할 중요한 개발 주제

## 진행 규칙

이 단계에서 모든 세부 요구사항이나 미래 기능을 확정하려 하지 않는다.

프로젝트를 시작하는 데 필요한 방향과 범위를 정한다.

## 완료 조건

이 서비스가 누구를 위해 무엇을 해결하는지와 첫 번째 MVP가 어디까지인지 설명할 수 있다.

---

# 7. MVP 요구사항 정의

## 목적

첫 번째 실제 개발을 시작할 수 있을 정도로 요구사항을 구체화한다.

## 주요 작업

필요한 범위에서 다음을 정의한다.

- 사용자 역할

- 핵심 기능

- 주요 정상 흐름

- 주요 실패 흐름

- Business Rule

- 입력 / 출력 요구사항

- Validation

- 데이터 보존 요구사항

- MVP에서 제외할 기능

필요한 시점에 확정된 내용을 `REQUIREMENTS.md`에 기록한다.

## 진행 규칙

처음부터 서비스의 모든 미래 요구사항을 정의하지 않는다.

현재 MVP 구현에 필요한 요구사항에 집중한다.

구현 중 새로운 요구사항이 발견될 수 있다는 것을 전제로 한다.

## 완료 조건

첫 번째 Backend 기능을 선택하고 구현할 수 있을 정도로 요구사항이 명확하다.

---

# 8. 초기 설계

## 목적

코드를 작성하기 전에 현재 MVP 구현에 필요한 최소한의 구조를 결정한다.

## 주요 작업

필요한 범위에서 다음을 검토한다.

- 핵심 Domain

- 주요 Entity

- Entity 관계

- 데이터 저장 구조

- 필요한 수준의 ERD

- 주요 API

- Request / Response의 기본 계약

- 정상 / 실패 흐름

- Transaction이 필요한 영역

- 애플리케이션의 기본 구조

- 외부 시스템 사용 여부

- 중요한 기술 선택

필요에 따라 `ARCHITECTURE.md`, `DECISIONS.md`, ERD, API 관련 문서를 만든다.

## 진행 규칙

설계를 생략하지 않는다.

반대로 개발 시작 전에 시스템 전체의 모든 세부사항을 완벽하게 설계하려 하지 않는다.

현재 개발에 필요한 수준까지만 설계한다.

## 완료 조건

첫 번째 기능을 개발하면서 핵심 구조를 처음부터 다시 결정해야 하는 상태가 아니며 구현을 시작할 최소 설계가 준비되어 있다.

---

# 9. Backend 개발 기반 구축

## 목적

실제 Backend 기능 개발이 가능한 실행 환경을 구성한다.

## 주요 작업

프로젝트에 필요한 범위에서 다음을 구성한다.

- Java / Spring 애플리케이션

- Build Tool

- 기본 프로젝트 구조

- 환경별 설정 구조

- 실제 사용할 RDBMS

- 로컬 DB 환경

- DB 연결

- Migration 도구

- 초기 Migration

- JPA 설정

- Test 환경

- Secret 분리 방법

- 기본 실행 / Build / Test 방법

## 진행 규칙

Backend 애플리케이션 생성 방법을 특정 IDE, ZIP, Wizard 또는 CLI로 고정하지 않는다.

현재 개발환경에서 자연스러운 방법을 사용한다.

DB가 필요한 프로젝트라면 실제 사용할 RDBMS 계열을 초반부터 사용한다.

개발 단계에서만 편한 임시 저장 방식을 사용한 뒤 DB 경험을 생략하지 않는다.

## 완료 조건

Backend 애플리케이션이 정상적으로 실행되고 실제 DB에 연결되며 Migration이 적용되고 첫 기능 개발을 시작할 수 있다.

---

# 10. 첫 Vertical Slice 개발

## 목적

설계한 구조와 전체 기능 개발 흐름이 실제로 동작하는지 하나의 작은 기능으로 확인한다.

## 주요 작업

가능하면 첫 기능은 다음이 연결되는 작은 Vertical Slice로 선택한다.

**HTTP 요청  
→ Application / Service  
→ Domain  
→ Repository  
→ DB  
→ HTTP 응답**

첫 기능에서 실제 기능 개발 Workflow를 처음부터 끝까지 경험한다.

## 기본 Workflow

**기능 선택  
→ 요구사항 확인  
→ 필요한 설계 확인  
→ Issue  
→ Branch  
→ 구현 및 Test  
→ 로컬 검증  
→ Commit  
→ Push  
→ Pull Request  
→ CI가 있다면 확인  
→ Diff / Review  
→ 수정  
→ Merge  
→ 필요한 문서 / 상태 갱신**

구현 방식에 따라 Test First, TDD 또는 구현과 Test를 함께 진행할 수 있다.

중요한 것은 구현과 검증을 분리된 마지막 단계로 생각하지 않는 것이다.

## 완료 조건

첫 기능이 실제 DB까지 연결되어 동작하고 필요한 검증을 통과했으며 PR / Review / Merge까지 완료했다.

---

# 11. CI 기본 구성

## 목적

개발자의 로컬 환경이 아니라 Repository 수준에서 Build와 Test를 자동으로 검증한다.

## 주요 작업

프로젝트에 필요한 수준에서 다음을 구성한다.

- Source Checkout

- Runtime / JDK 설정

- Dependency 준비

- Build

- Test

- Test DB 또는 필요한 외부 환경

- Pull Request Check

- 실패 결과 확인

GitHub Repository를 사용하는 경우 GitHub Actions 등을 사용할 수 있다.

## 진행 규칙

Build와 Test 방법이 정해지기 전에 CI부터 복잡하게 만들지 않는다.

CI 설정 파일을 만드는 것 자체를 완료로 판단하지 않는다.

실제로 성공과 실패가 발생하는지 확인한다.

## 완료 조건

정해진 Git 이벤트에서 Build와 Test가 자동 실행되며 성공 / 실패 결과를 확인할 수 있다.

---

# 12. Backend 기능 반복 개발

## 목적

첫 기능에서 확인한 개발 Workflow를 실제 MVP 기능들에 반복 적용한다.

## 기본 Workflow

각 기능은 기본적으로 다음 과정을 반복한다.

**기능 선택  
→ 요구사항 확인  
→ 필요한 설계 확인  
→ Issue  
→ Branch  
→ 구현 / Test  
→ 로컬 검증  
→ Commit  
→ Push  
→ Pull Request  
→ CI  
→ Review  
→ 수정  
→ Merge  
→ 필요한 문서 / 상태 갱신**

## 진행 규칙

기능 하나의 크기가 지나치게 커지지 않도록 작업을 분해한다.

구현 중 기존 요구사항이나 설계로 해결할 수 없는 문제가 발견되면 임시 코드로 우회한 뒤 넘어가지 않는다.

필요한 요구사항 또는 설계 변경을 먼저 처리한다.

DB Schema가 변경되면 새로운 Migration을 추가한다.

## 완료 조건

현재 Backend MVP에 포함된 기능이 필요한 개발 Workflow와 검증을 거쳐 구현되어 있다.

---

# 13. Backend 독립 검증 및 안정화

## 목적

Frontend가 존재하지 않아도 현재 Backend 요구사항을 독립적으로 검증하고 사용할 수 있는 상태를 만든다.

## 주요 작업

프로젝트에 필요한 범위에서 다음을 확인한다.

- 전체 자동화 Test

- 주요 API 실제 호출

- 정상 흐름

- 실패 흐름

- Validation

- Error Response

- DB 상태

- Migration 재현성

- 환경설정

- Secret 분리

- CI 상태

- 새로운 환경에서 실행 가능한지 여부

## 진행 규칙

Frontend가 생기기 전이라는 이유로 Backend API의 실제 동작 확인을 미루지 않는다.

HTTP Client나 실제 요청 도구 등을 사용하여 API를 독립적으로 확인할 수 있다.

## 완료 조건

현재 Backend MVP를 Frontend 없이도 Test와 API 호출을 통해 독립적으로 검증할 수 있다.

---

# 14. Container 구성

## 목적

애플리케이션 실행환경을 명시적으로 패키징하고 재현 가능한 실행 방식을 만든다.

## 주요 작업

필요한 범위에서 다음을 구성한다.

- Dockerfile

- Runtime

- `.dockerignore`

- Container Image Build

- 환경변수 전달

- DB 연결

- Docker Compose 필요 여부

- Container 실행

- 종료

- 재시작

## 진행 규칙

Container 기술 자체를 사용하는 것을 목표로 하지 않는다.

애플리케이션이 로컬 머신의 특정 환경에만 의존하지 않고 재현 가능한 방식으로 실행되도록 하는 데 초점을 둔다.

## 완료 조건

Backend Image를 Build하고 Container에서 실제 애플리케이션을 실행하여 정상 동작을 확인할 수 있다.

---

# 15. Backend 배포환경 구성

## 목적

로컬을 벗어난 실제 환경에 Backend를 배포할 수 있는 기반을 마련한다.

## 주요 작업

프로젝트 규모에 맞게 다음을 검토한다.

- 배포 대상 Platform / Server

- Runtime

- Container Registry 필요 여부

- Production DB

- Network

- Domain / DNS

- HTTPS

- 환경변수

- Secret

- 접근 제어

- Migration 적용 방식

- 배포 방식

- Rollback 방법

필요한 내용은 `DEPLOYMENT.md` 등에 기록할 수 있다.

## 진행 규칙

현재 프로젝트 규모와 학습 목표보다 지나치게 복잡한 인프라를 선택하지 않는다.

실제 문제 없이 Kubernetes, MSA 등의 구조를 먼저 도입하지 않는다.

## 완료 조건

현재 Backend를 실제 환경에 배포하기 위한 인프라와 절차가 준비되어 있다.

---

# 16. Backend Release / 배포

## 목적

Merge된 애플리케이션을 실제 환경에 Release한다.

## 기본 흐름

프로젝트 상황에 따라 다음과 같은 흐름을 경험한다.

**Merge된 코드  
→ CI  
→ Artifact / Image 생성  
→ Registry  
→ Production Migration  
→ Deploy  
→ Application Start  
→ Health 확인**

CD 자동화는 프로젝트에 적절한 시점에 추가할 수 있다.

## 진행 규칙

“배포 명령이 성공했다”는 사실만으로 배포 성공으로 판단하지 않는다.

배포된 애플리케이션이 실제 요청을 처리할 수 있는지 확인한다.

## 완료 조건

Backend가 실제 외부 환경에서 실행되고 주요 API와 DB가 정상 동작한다.

---

# 17. Health / Logging / Monitoring

## 목적

애플리케이션이 실행 중인지뿐 아니라 실제 서비스가 정상인지 판단하고 문제 발생 시 원인을 추적할 수 있게 한다.

## Health

최소한 애플리케이션의 정상 동작 여부를 확인할 방법을 마련한다.

필요하면 DB 등 주요 Dependency 상태도 확인한다.

## Logging

요청, 오류 및 중요한 애플리케이션 상태를 추적할 수 있게 한다.

Password, Token 등의 Secret과 민감정보를 로그에 남기지 않는다.

## Monitoring

프로젝트에 필요한 수준부터 도입한다.

필요해지면 다음을 추가할 수 있다.

- Metrics

- Resource Monitoring

- Error Tracking

- Alert

- Dashboard

## 진행 규칙

처음부터 대규모 Observability 환경을 구축하지 않는다.

현재 서비스의 운영 상태를 판단하는 데 필요한 수준부터 시작한다.

## 완료 조건

서비스가 정상인지 확인할 수 있고 문제가 발생했을 때 기본적인 원인 조사가 가능하다.

---

# 18. Backend 운영 확인

## 목적

Backend를 만드는 것뿐 아니라 배포된 애플리케이션을 운영하는 기본 경험을 한다.

## 주요 작업

필요한 범위에서 다음을 경험한다.

- Application 상태 확인

- Process / Container 상태 확인

- 로그 확인

- DB 연결 확인

- 애플리케이션 재시작

- 설정 확인

- CI/CD 결과 확인

- 실패한 Release 확인

- 새로운 Release 상태 확인

반복적으로 발생하거나 기록 가치가 있는 문제는 `TROUBLESHOOTING.md` 등에 남길 수 있다.

## 완료 조건

배포된 Backend를 확인하고 기본적인 운영 문제를 조사할 수 있는 상태다.

---

# 19. Frontend 기술 선택

## 목적

Backend가 독립적으로 검증되고 기본 배포와 운영까지 경험된 이후 전체 웹서비스를 완성하기 위한 Frontend 기술을 결정한다.

## 주요 고려사항

- 서비스 UI 특성

- 주요 사용자 흐름

- Backend API

- 프로젝트 규모

- 현재 개발환경

- 학습 목표

- 유지보수성

- 생태계

- Rendering 방식

- 당시 기술 상황

## 진행 규칙

프로젝트 시작 단계에서 React, Vue 등 특정 Framework를 미리 확정해두지 않는다.

실제 프로젝트 요구사항을 기준으로 선택한다.

중요한 기술 선택은 필요하면 `DECISIONS.md`에 기록한다.

## 완료 조건

현재 프로젝트에서 사용할 Frontend 기술과 선택 이유가 정해져 있다.

---

# 20. Frontend 개발 기반 구축

## 목적

선택한 Frontend 기술로 실제 기능 개발을 시작할 수 있는 환경을 만든다.

## 주요 작업

필요한 범위에서 다음을 구성한다.

- `frontend/`

- Runtime

- Package Manager

- 프로젝트 생성

- 개발 서버

- Build

- 환경변수

- Backend API 주소

- Routing

- 기본 프로젝트 구조

- Lint / Formatting

- Test 환경

## 완료 조건

Frontend 애플리케이션이 실행되고 실제 기능 개발을 시작할 수 있다.

---

# 21. Frontend 기능 개발

## 목적

MVP의 사용자 흐름을 실제 UI로 구현한다.

## 기본 Workflow

기능에 따라 다음과 같은 개발 흐름을 반복한다.

**사용자 흐름 확인  
→ Issue  
→ Branch  
→ UI 구현  
→ 상태 처리  
→ 필요한 Test  
→ Browser 검증  
→ Commit / Push  
→ PR  
→ CI  
→ Review  
→ Merge**

API 연동을 아직 하지 않는 UI 작업과 실제 Backend 연동 작업을 필요에 따라 구분한다.

## 진행 규칙

Frontend 전체를 한 번에 구현하지 않는다.

사용자 흐름 또는 화면 단위의 작은 기능으로 나누어 진행한다.

## 완료 조건

MVP의 주요 사용자 흐름을 Frontend에서 수행할 수 있는 상태다.

---

# 22. Backend / Frontend 통합

## 목적

독립적으로 개발한 Backend와 Frontend를 실제 사용자 흐름으로 연결한다.

## 주요 작업

실제 통합 과정에서 다음과 같은 문제를 확인할 수 있다.

- 필요한 응답 데이터 부족

- API Contract 불편

- Pagination 필요

- Validation 변경

- Error Response 개선

- 새로운 API

- Authentication / Authorization 문제

- CORS

- 파일 업로드

- 새로운 사용자 흐름

- Frontend 요구에 따른 API 변경

## 진행 규칙

이 단계에서 발견된 문제를 초기 Backend 개발 실패로 간주하지 않는다.

실제 서비스 통합 과정에서 발견된 **새로운 요구사항 또는 변경 요구사항**으로 취급한다.

Backend와 Frontend 중 어느 쪽을 변경해야 하는지 실제 책임을 기준으로 판단한다.

## 완료 조건

Frontend가 실제 Backend API와 연결되어 주요 사용자 흐름이 동작한다.

---

# 23. 통합 과정의 요구사항 변경

## 목적

통합 과정에서 발견된 새로운 요구사항을 임시 수정이 아니라 정상적인 개발 변경으로 처리한다.

## 기본 흐름

**새 요구사항 발견  
→ 영향 분석  
→ 요구사항 변경  
→ 필요한 설계 변경  
→ 관련 문서 갱신  
→ Issue  
→ Branch  
→ 구현  
→ 필요한 Migration  
→ Test  
→ 통합 검증  
→ PR  
→ CI  
→ Review  
→ Merge**

API Contract가 변경되면 Backend와 Frontend 양쪽에 미치는 영향을 확인한다.

DB Schema가 변경되면 새로운 Migration을 추가한다.

## 완료 조건

통합 과정에서 발견된 변경사항이 임시 Patch가 아니라 정상적인 개발 Workflow를 거쳐 반영되어 있다.

---

# 24. 전체 웹서비스 검증

## 목적

Backend와 Frontend 각각의 동작을 넘어 실제 사용자 관점에서 서비스가 정상적으로 작동하는지 확인한다.

## 주요 검증 대상

필요한 범위에서 다음을 확인한다.

- 핵심 정상 사용자 흐름

- 실패 흐름

- Validation

- Error UI

- API 연동

- 실제 DB 저장

- 화면 이동

- 새로고침

- Production Build

- 환경변수

- Backend / Frontend 연결

- 실제 배포환경과의 차이

자동화할 가치가 있는 검증은 Test로 남긴다.

Browser 또는 실제 환경에서만 확인할 수 있는 부분은 실제로 확인한다.

## 완료 조건

MVP의 핵심 사용자 흐름이 Backend와 Frontend를 함께 사용하여 정상 동작한다.

---

# 25. 전체 웹서비스 배포

## 목적

Backend뿐 아니라 Frontend까지 포함한 실제 서비스를 사용할 수 있게 배포한다.

## 주요 작업

프로젝트 구조에 따라 다음을 확인한다.

- Backend Production Release

- Frontend Production Build

- Frontend 배포

- Backend API 주소

- Domain

- HTTPS

- Production 환경변수

- CORS

- Production DB

- Migration

- Health

- 실제 사용자 요청

## 진행 규칙

Backend와 Frontend가 각각 실행된다는 사실만으로 전체 서비스 배포 완료로 판단하지 않는다.

실제 배포된 URL에서 주요 사용자 흐름을 확인한다.

## 완료 조건

실제 배포환경에서 사용자가 웹서비스의 핵심 기능을 처음부터 끝까지 사용할 수 있다.

---

# 26. 운영 상태 확인

## 목적

배포된 전체 웹서비스의 실제 운영 상태를 확인한다.

## 주요 확인 대상

- Frontend 접근

- Backend Health

- 주요 API

- Database

- Application Log

- Error

- Process / Container

- CI/CD

- Release 상태

- 주요 사용자 흐름

필요한 운영 절차가 생기면 관련 운영 문서나 `TROUBLESHOOTING.md` 등에 기록한다.

## 완료 조건

현재 서비스의 정상 여부를 판단하고 기본적인 문제를 추적할 수 있다.

---

# 27. 배포된 기존 서비스 변경

## 목적

새 프로젝트를 처음 만드는 것뿐 아니라 이미 운영 중인 서비스를 안전하게 변경하는 전체 과정을 경험한다.

첫 배포 이후 의미 있는 기능이나 구조를 최소 한 번 이상 변경한다.

## 변경 예시

- 기존 테이블에 컬럼 추가

- 새로운 Business Rule

- 새로운 API

- 기존 API 변경

- Validation 변경

- 새로운 Frontend 기능

- Backend / Frontend 동시 변경

## 변경 Workflow

**새 요구사항  
→ 영향 분석  
→ 요구사항 / 설계 수정  
→ 필요한 Migration  
→ Issue  
→ Branch  
→ 구현  
→ Test  
→ 로컬 / 통합 검증  
→ PR  
→ CI  
→ Review  
→ Merge  
→ Release  
→ Production Migration  
→ Deploy  
→ Health / Log / 사용자 흐름 확인**

## 진행 규칙

운영 DB를 삭제하고 처음부터 다시 생성하는 방식으로 Schema 변경을 해결하지 않는다.

기존 사용자와 기존 데이터를 고려하여 변경한다.

## 완료 조건

기존 서비스의 상태와 데이터를 유지하면서 변경사항을 안전하게 배포하고 운영 결과까지 확인했다.

---

# 28. DB / Migration 공통 원칙

DB와 Schema 변경은 프로젝트 전체 Lifecycle에 걸쳐 다음 원칙을 적용한다.

- DB가 필요한 프로젝트는 실제 RDBMS를 사용한다.

- 가능한 범위에서 local / test / production은 동일한 DB 계열을 사용한다.

- Schema 변경 이력은 Migration으로 관리한다.

- 이미 적용된 Migration을 임의로 수정하지 않는다.

- 변경이 필요하면 새로운 Migration을 추가한다.

- 개발 중 DB를 반복 삭제하여 Schema를 맞추는 방식에 의존하지 않는다.

- Migration은 실제 실행하여 검증한다.

- 운영 데이터가 존재한 이후의 Schema 변경은 기존 데이터와 호환성을 고려한다.

- 필요하면 JPA schema validation 등의 검증을 사용한다.

---

# 29. Test / Verification 공통 원칙

Test는 프로젝트 마지막에 추가하는 별도의 작업이 아니다.

기능 개발과 변경 과정에 지속적으로 포함한다.

현재 코드의 책임과 위험에 따라 필요한 수준의 검증을 선택한다.

예:

- Unit Test

- Domain / Service Test

- Repository Test

- Integration Test

- API Test

- 실제 RDBMS 기반 Test

- Frontend Test

- Browser 검증

- 통합 검증

모든 종류의 Test를 형식적으로 추가하지 않는다.

무엇을 보장해야 하는지 먼저 판단하고 그에 맞는 Test를 사용한다.

중요한 동작은 가능한 범위에서 반복 실행 가능한 자동화된 Test로 남긴다.

---

# 30. 환경 / Secret 공통 원칙

프로젝트에 필요하면 환경을 구분한다.

예:

- local

- test

- production

환경마다 값은 다를 수 있지만 어떤 설정이 어떻게 다른지 명확하게 유지한다.

다음과 같은 민감정보를 Repository에 직접 저장하지 않는다.

- DB Password

- API Key

- Token

- Production Credential

- 기타 Secret

Git에 포함할 설정과 외부에서 주입해야 할 Secret을 구분한다.

---

# 31. 문서 관리 원칙

문서는 프로젝트와 함께 발전한다.

처음부터 필요하지 않은 문서를 전부 만들지 않는다.

실제 필요가 생기면 다음과 같은 문서를 생성하거나 갱신할 수 있다.

- `REQUIREMENTS.md`

- `ARCHITECTURE.md`

- `DECISIONS.md`

- `DEPLOYMENT.md`

- `TROUBLESHOOTING.md`

- ERD

- API 관련 문서

- Frontend 관련 설계 문서

- 운영 문서

문서 작성 자체를 프로젝트의 목적으로 만들지 않는다.

현재 개발과 다음 작업에 필요한 수준으로 유지한다.

실제 구현 또는 결정이 변경되면 관련 문서도 함께 변경한다.

Lifecycle 단계, 주요 완료 작업, 중요한 결정, Migration / CI / 배포 상태 등 프로젝트 진행에 의미 있는 변화가 발생하면 `docs/PROJECT_STATE.md`에 현재 상태를 반영한다.

---

# 32. 기술과 범위 관리 원칙

프로젝트에 사용되는 기술은 현재 해결해야 할 문제와 규모에 맞게 선택한다.

예를 들어 실제 요구사항이 없다면 다음을 미리 도입하지 않는다.

- Redis

- Kafka

- Kubernetes

- MSA

- 분산락

- 복잡한 Cache 구조

- 대규모 장애복구 구조

- 대규모 트래픽 대응 구조

- 복잡한 Observability Stack

프로젝트가 단순하다고 개발 프로세스를 생략하지 않는다.

반대로 실제 필요가 없는데 기술적 복잡성을 추가하여 프로젝트를 불필요하게 크게 만들지도 않는다.

**비즈니스 난이도와 개발 프로세스의 완성도를 구분한다.**

---

# 33. 프로젝트 완료 기준

코드 작성이나 첫 배포만으로 프로젝트 완료로 판단하지 않는다.

최소한 다음 경험이 하나의 Lifecycle로 연결되어 있어야 한다.

- 개발환경을 확인했다.

- Repository와 협업환경을 구성했다.

- Kickoff를 진행했다.

- MVP 요구사항을 정했다.

- 필요한 설계를 했다.

- 실제 Backend 개발환경을 구축했다.

- 실제 RDBMS와 Migration을 사용했다.

- 작은 기능 단위의 개발 Workflow를 반복했다.

- Test와 실제 검증을 진행했다.

- Issue / Branch / Commit / PR / Review / Merge를 경험했다.

- CI를 사용했다.

- Backend를 독립적으로 검증했다.

- Container를 사용했다.

- Backend를 실제 환경에 배포했다.

- Health와 Logging을 확인했다.

- 기본 운영을 경험했다.

- 프로젝트 상황에 맞춰 Frontend 기술을 선택했다.

- Frontend를 개발했다.

- Backend와 Frontend를 실제로 통합했다.

- 통합 과정에서 발견된 요구사항 변경을 정상적인 개발 Workflow로 처리했다.

- 전체 웹서비스를 실제로 배포했다.

- 배포된 서비스를 운영 관점에서 확인했다.

- 이미 배포된 서비스를 다시 변경했다.

- Migration / Test / CI / 재배포 / 운영 확인을 다시 경험했다.

- 프로젝트 문서와 현재 상태가 실제 Repository와 함께 유지되어 있다.

이 프로젝트의 최종 목표는 하나의 서비스를 빠르게 완성하는 것이 아니다.

**새로운 프로젝트에서도 같은 개발 Lifecycle을 스스로 반복할 수 있을 정도로 실제 웹서비스 개발 과정을 처음부터 끝까지 경험하는 것**이다.
