# Synthesis: 세 방법론의 관계와 리서치 종합

> 이 문서는 리서치 결과의 종합이다. 정제된 원칙은 [PRINCIPLES.md](/PRINCIPLES.md) 참고.

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

## 2. 리서치에서 도출된 핵심 개념

### 2.1 Fowler/Böckeler의 3축 프레임워크
하네스 엔지니어링의 구조적 뼈대:
- **Inform** — 에이전트에게 올바른 컨텍스트 제공
- **Verify** — 에이전트의 산출물을 자동 검증
- **Correct** — 문제 발생 시 자동 교정 및 피드백 루프

### 2.2 SDD의 명세 중심 접근
- 명세(spec)가 진실의 원천(source of truth)
- 명세 → 구현 → 검증의 단방향 흐름
- 작업 규모에 따른 적응적 적용 (버그 수정 vs 신규 기능 vs 대규모 변경)

### 2.3 BMAD의 Product Brief 워크플로우
서비스 정체성 정의를 위한 질문 체계 (GP → G1 그룹의 근거):
- Vision Discovery: 핵심 문제, 현재 대안, 차별점
- Target Users: 1차/2차 페르소나, 사용자 여정
- Success Metrics: 사용자 성공 지표 + 비즈니스 지표
- Scope: MVP 경계, 미래 비전

### 2.4 진단 프레임워크 초안
7개 그룹(G1~G7), 32개 진단 항목으로 구성된 프레임워크를 도출.
스킬 구현 시 활용할 진단 체크리스트, 성숙도 모델(Level 0~4), 리포트 형식 포함.

**그룹 구조:**
- G1 Product Context — 서비스 정체성
- G2 Foundation — 환경 재현성
- G3 Entry & Navigation — 진입과 탐색
- G4 Architecture & Structure — 구조와 확장성
- G5 Verification & Quality Gate — 검증과 품질 관문
- G6 Specification & Documentation — 명세와 문서
- G7 Operations & Maintenance — 운영과 유지

## 3. 향후 개발 로드맵

### Phase 1 (완료): 리서치 & 문서화
- [x] SDD, Harness Engineering, Agentic Engineering 리서치
- [x] 문서 정리 및 종합
- [x] 원칙 정제 → [PRINCIPLES.md](/PRINCIPLES.md)

### Phase 2: 스킬 프로토타입
- [ ] 스킬 1 (하네스 세팅) 프로토타입 — Claude Code 우선
- [ ] 스킬 2 (하네스 진단) 프로토타입 — Claude Code 우선
- [ ] 진단 프레임워크 스킬 구현체로 전환

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
