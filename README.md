# Harness

CLI 기반 AI 코딩 에이전트(Claude Code, Codex CLI, Gemini CLI 등)를 위한 **프로젝트 하네스 관리 스킬** 모음.

## 목적

AI 에이전트가 신뢰할 수 있는 코드를 생성하려면 에이전트 자체보다 **에이전트를 둘러싼 시스템(하네스)** 이 중요하다. 이 프로젝트는 두 가지 스킬을 제공한다:

### 스킬 1: 프로젝트 하네스 세팅
새 프로젝트 또는 기존 프로젝트에 하네스를 구축한다.
- Context Layer: AGENTS.md, CLAUDE.md, Constitution, 아키텍처 문서
- Verification Layer: CI/CD, 린터, 구조적 테스트, 커버리지 기준
- Correction Layer: 문서-코드 동기화, 주기적 정리, 피드백 루프

### 스킬 2: 하네스 수준 진단
현재 프로젝트의 하네스 성숙도를 평가하고 개선점을 제안한다.
- Inform / Verify / Correct 3축 기반 평가
- Level 0 (Bare) ~ Level 4 (Optimized) 5단계 성숙도 모델
- 구체적 개선 권고사항 제공

## 배경 방법론

이 프로젝트는 세 가지 방법론의 교차점에 위치한다:

| 방법론 | 역할 | 핵심 인사이트 |
|--------|------|-------------|
| **SDD** (Spec-Driven Development) | 의도의 정형화 | "명세가 소스 오브 트루스" |
| **Harness Engineering** | 에이전트 제어 시스템 설계 | "모델보다 하네스가 중요" |
| **Agentic Engineering** | 상위 패러다임 | "인간은 오케스트레이션, 에이전트가 실행" |

상세 리서치는 `docs/research/` 참조.

## 문서 구조

```
Harness/
├── README.md                          # 이 문서
├── CLAUDE.md                          # 세션 간 컨텍스트 유지용
├── docs/
│   └── research/
│       ├── sdd.md                     # SDD 방법론 리서치
│       ├── harness-engineering.md     # 하네스 엔지니어링 리서치
│       ├── agentic-engineering.md     # 에이전틱 엔지니어링 리서치
│       └── synthesis.md              # 종합 + 스킬 설계 원칙
```

## 크로스 플랫폼 지원 (계획)

| 에이전트 | 규칙 파일 | 지원 상태 |
|---------|----------|----------|
| Claude Code | CLAUDE.md | 우선 지원 |
| Codex CLI | AGENTS.md | 계획 |
| Gemini CLI | GEMINI.md | 계획 |
| Cursor | .cursorrules | 계획 |

## 로드맵

- [x] **Phase 1**: 리서치 & 문서화 (SDD, Harness Engineering, Agentic Engineering)
- [ ] **Phase 2**: 스킬 프로토타입 (Claude Code 우선)
- [ ] **Phase 3**: 크로스 플랫폼 확장
- [ ] **Phase 4**: 커뮤니티 테스트 & 반복

## 핵심 참고 자료

- [OpenAI - Harness Engineering](https://openai.com/index/harness-engineering/)
- [Martin Fowler - Harness Engineering](https://martinfowler.com/articles/exploring-gen-ai/harness-engineering.html)
- [Thoughtworks - Spec-Driven Development](https://www.thoughtworks.com/en-us/insights/blog/agile-engineering-practices/spec-driven-development-unpacking-2025-new-engineering-practices)
- [Anthropic - Effective Context Engineering](https://www.anthropic.com/engineering/effective-context-engineering-for-ai-agents)
- [Margaret-Anne Storey - Cognitive Debt](https://margaretstorey.com/blog/2026/02/09/cognitive-debt/)
