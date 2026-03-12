# Synthesis: 세 방법론의 관계와 스킬 설계 원칙

## 1. 세 방법론의 관계도

```
┌──────────────────────────────────────────────────────┐
│            Agentic Engineering (상위 패러다임)          │
│   "인간이 오케스트레이션, 에이전트가 실행"                │
│                                                       │
│   ┌───────────────┐    ┌────────────────────────┐    │
│   │      SDD      │    │  Harness Engineering   │    │
│   │   (무엇을)     │───▶│  (어떻게 제어할 것인가)   │    │
│   │  명세 = 진실    │    │  Inform + Verify       │    │
│   │  의도의 정형화   │    │  + Correct             │    │
│   └───────────────┘    └────────────────────────┘    │
│              │                      │                 │
│              ▼                      ▼                 │
│   ┌──────────────────────────────────────────────┐   │
│   │        Context Engineering (기반 기술)          │   │
│   │   "모델이 보는 것을 큐레이션하여                   │   │
│   │    더 나은 결과를 얻는 것"                        │   │
│   └──────────────────────────────────────────────┘   │
│                        │                              │
│                        ▼                              │
│   ┌──────────────────────────────────────────────┐   │
│   │       Cognitive Debt (핵심 리스크)               │   │
│   │   "속도가 이해를 초과할 때의 부채"                  │   │
│   └──────────────────────────────────────────────┘   │
└──────────────────────────────────────────────────────┘
```

### 관계 요약
- **SDD**는 "무엇을 만들 것인가"의 의도를 정형화하는 방법론
- **Harness Engineering**은 "에이전트를 어떻게 제어할 것인가"의 시스템 설계
- **Agentic Engineering**은 이 모든 것을 아우르는 상위 패러다임
- **Context Engineering**은 세 방법론 모두의 기반 기술
- **Cognitive Debt**는 이 모든 방법론이 해결하려는 핵심 리스크

## 2. 스킬 설계에 적용할 핵심 원칙

### 2.1 스킬 1: 프로젝트 하네스 초기 세팅

SDD + Harness Engineering의 교훈을 종합하면, 프로젝트 세팅 스킬이 다뤄야 할 영역:

#### A. Context Layer (Inform)
- [ ] AGENTS.md / CLAUDE.md / rules 파일 생성
- [ ] 프로젝트 구조 문서화 (아키텍처, 의존성 흐름)
- [ ] Constitution 작성 (스택, 네이밍, 허용/금지 규칙)
- [ ] Steering 문서 (product.md, structure.md, tech.md)

#### B. Verification Layer (Verify)
- [ ] CI/CD 파이프라인 설정 또는 검증
- [ ] 린터/포매터 설정
- [ ] 구조적 테스트 (의존성 레이어 위반 감지)
- [ ] 커버리지 기준 설정

#### C. Correction Layer (Correct)
- [ ] 문서-코드 동기화 메커니즘
- [ ] 주기적 정리/검증 스크립트
- [ ] 피드백 루프 설계

#### D. SDD Artifacts (선택적)
- [ ] requirements.md 템플릿
- [ ] design.md 템플릿
- [ ] tasks.md 템플릿

### 2.2 스킬 2: 하네스 수준 진단/평가

Fowler/Böckeler의 3축 프레임워크를 기반으로 하네스 성숙도를 평가:

#### 평가 프레임워크 (초안)

```
┌─────────────────────────────────────────────────────┐
│                 Harness Maturity Level               │
│                                                      │
│  Level 0: Bare    - 하네스 없음                       │
│  Level 1: Basic   - AGENTS.md + 기본 린터             │
│  Level 2: Guided  - Constitution + CI + 구조적 테스트  │
│  Level 3: Managed - SDD 워크플로우 + 피드백 루프       │
│  Level 4: Optimized - 자동 교정 + 인지 부채 관리      │
│                                                      │
└─────────────────────────────────────────────────────┘
```

#### 축별 평가 항목

| 축 | Level 0 | Level 1 | Level 2 | Level 3 | Level 4 |
|---|---------|---------|---------|---------|---------|
| **Inform** | 없음 | AGENTS.md 존재 | Constitution + 아키텍처 문서 | SDD spec 워크플로우 | 동적 컨텍스트 + observability 통합 |
| **Verify** | 없음 | 기본 린터 | CI + 구조적 테스트 | 명세 기반 검증 + 커버리지 기준 | 자동 drift 감지 + fail-fast |
| **Correct** | 없음 | 수동 리뷰 | 자동화된 피드백 루프 | 주기적 GC 에이전트 | 자기 수리 + 인지 부채 모니터링 |

#### 진단 결과 형식 (초안)

```
=== Harness Diagnostic Report ===

Project: my-project
Date: 2026-03-12
Overall Level: 2 (Guided)

[Inform]  ██████████░░░░░░░░░░  50%
  ✓ CLAUDE.md exists
  ✓ Basic project structure documented
  ✗ No constitution/steering documents
  ✗ No SDD spec templates

[Verify]  ████████████████░░░░  80%
  ✓ CI pipeline configured
  ✓ Linter configured (eslint)
  ✓ Test coverage at 72%
  ✗ No structural dependency tests

[Correct] ████░░░░░░░░░░░░░░░░  20%
  ✓ Basic code review process
  ✗ No automated doc-code sync
  ✗ No periodic GC agents
  ✗ No cognitive debt monitoring

Recommendations:
  1. [HIGH] Add constitution document (steering/constitution.md)
  2. [HIGH] Add structural dependency tests
  3. [MED]  Set up doc-code sync mechanism
  4. [LOW]  Consider SDD spec templates for new features
```

## 3. 핵심 설계 원칙

### 3.1 "Map, not a Manual"
스킬이 생성하는 문서는 간결하고 구조화되어야 한다. 1,000줄짜리 AGENTS.md가 아니라 필요한 컨텍스트만 적시에 제공.

### 3.2 점진적 채택 (Progressive Adoption)
- Level 0에서 바로 Level 4로 갈 수 없다
- 세팅 스킬은 현재 레벨을 진단하고 **다음 레벨로의 구체적 단계**를 제안
- 소규모 버그에 SDD 전체를 적용하는 "슬레지해머" 접근 방지

### 3.3 도구 비종속 (Tool-Agnostic)
- Claude Code, Codex CLI, Gemini CLI 모두에서 작동
- 각 도구의 규칙 파일 형식 차이를 추상화
- cc-sdd의 크로스 플랫폼 접근 참고

### 3.4 Constitution 품질 우선
- 시니어 엔지니어의 판단이 필수
- 반복적 개선을 전제로 설계
- "프로젝트 DNA"를 정확히 인코딩

### 3.5 인지적 부채 인식
- 생성된 코드의 이해를 돕는 장치 포함
- "왜 이 결정이 내려졌는가"의 기록
- 팀 공유 이해 재구축 메커니즘

## 4. 크로스 플랫폼 규칙 파일 매핑

| 개념 | Claude Code | Codex CLI | Gemini CLI | Cursor |
|------|------------|-----------|------------|--------|
| 프로젝트 규칙 | CLAUDE.md | AGENTS.md | GEMINI.md | .cursorrules |
| 전역 규칙 | ~/.claude/CLAUDE.md | ~/.agents.md | - | - |
| 명령/스킬 | /commands/ | - | - | - |

## 5. 향후 개발 로드맵

### Phase 1 (현재): 리서치 & 문서화
- [x] SDD, Harness Engineering, Agentic Engineering 리서치
- [x] 문서 정리 및 종합

### Phase 2: 스킬 프로토타입
- [ ] 스킬 1 (하네스 세팅) 프로토타입 — Claude Code 우선
- [ ] 스킬 2 (하네스 진단) 프로토타입 — Claude Code 우선
- [ ] 평가 프레임워크 상세화

### Phase 3: 크로스 플랫폼 확장
- [ ] Codex CLI 지원
- [ ] Gemini CLI 지원
- [ ] 기타 에이전트 지원

### Phase 4: 커뮤니티 & 반복
- [ ] 실제 프로젝트에서 테스트
- [ ] 피드백 기반 개선
- [ ] Constitution 템플릿 라이브러리

---

## Sources

이 문서는 다음 리서치 문서들의 종합입니다:
- [SDD Research](./sdd.md)
- [Harness Engineering Research](./harness-engineering.md)
- [Agentic Engineering Research](./agentic-engineering.md)
