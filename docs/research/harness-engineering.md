# Harness Engineering

> "If 2025 was the year AI agents proved they could write code, 2026 is the year we learned that the agent isn't the hard part — the harness is." — NxCode

## 1. 핵심 개념

Harness Engineering은 AI 코딩 에이전트가 신뢰할 수 있는 작업을 수행할 수 있도록 **제약조건, 피드백 루프, 문서, 린터, 라이프사이클 관리를 설계하는 새로운 엔지니어링 분야**이다.

핵심 통찰:
> **"The underlying model matters less than the system around it."**

증거: LangChain은 모델 변경 없이 하네스만 교체하여 Terminal Bench 2.0에서 52.8% → 66.5%로 성적 향상 (Top 30 → Top 5).

## 2. OpenAI의 실험

### 2.1 개요
- **기간**: 5개월
- **결과**: 약 100만 줄의 프로덕션 코드를 **수동 타이핑 없이** 빌드 & 출시
- **팀 규모**: ~40명
- **효율**: 수동 대비 약 **1/10 시간**
- **범위**: 애플리케이션 로직, 문서, CI 설정, observability 설정, 툴링

### 2.2 핵심 발견
- 엔지니어의 주요 역할이 "코드 작성"에서 **"에이전트가 유용한 작업을 할 수 있도록 환경 설계"** 로 전환
- "No manually typed code at all"을 강제 함수(forcing function)로 사용하여 하네스 설계를 촉진

## 3. 하네스의 3축 (Fowler/Böckeler 프레임워크)

```
┌─────────────────────────────────────────────┐
│              HARNESS                         │
│                                             │
│  ┌──────────┐  ┌──────────┐  ┌──────────┐  │
│  │  INFORM  │  │  VERIFY  │  │ CORRECT  │  │
│  │          │  │          │  │          │  │
│  │ Context  │  │ Archi-   │  │ Garbage  │  │
│  │ Engine-  │  │ tectural │  │ Collec-  │  │
│  │ ering    │  │ Constr-  │  │ tion     │  │
│  │          │  │ aints    │  │          │  │
│  └──────────┘  └──────────┘  └──────────┘  │
│                                             │
└─────────────────────────────────────────────┘
```

### 3.1 Inform (Context Engineering)
에이전트에게 **무엇을 해야 하는지** 알려준다.
- 코드베이스 내 지속적으로 향상되는 지식 베이스
- AGENTS.md, 규칙 파일, 프로젝트 문서
- observability 데이터, 브라우저 내비게이션 등 동적 컨텍스트
- 코드 설계 자체가 컨텍스트의 거대한 부분 — "the code design itself is a huge part of the context"

### 3.2 Verify (Architectural Constraints)
에이전트가 **올바르게 했는지** 검증한다.
- LLM 기반 에이전트뿐만 아니라 **결정론적 커스텀 린터와 구조적 테스트**로 모니터링
- CI/CD 파이프라인 통합
- 모듈 레이어 위반 자동 감지

### 3.3 Correct (Garbage Collection)
잘못되었을 때 **교정**한다.
- 주기적으로 실행되는 에이전트가 문서 불일치나 아키텍처 제약 위반을 탐지
- 엔트로피와 부패(entropy and decay)에 대항
- 자기 수리 메커니즘과 피드백 루프

## 4. 핵심 원칙들

### 4.1 "Map, not a Manual"
> "Give Codex a map, not a 1,000-page instruction manual"

**문제**: 거대한 AGENTS.md 하나로 모든 것을 설명하려는 접근은 예측 가능하게 실패한다.
**이유**: 컨텍스트는 희소 자원. 거대 지시문은 작업, 코드, 관련 문서를 밀어내어 에이전트가 핵심 제약을 놓치거나 잘못된 것에 최적화하게 만든다.
**해결**: 필요한 컨텍스트만 적시에 제공하는 구조화된 접근.

### 4.2 Depth-First Task Decomposition
큰 목표를 작은 빌딩 블록으로 쪼갠다:
```
큰 목표
  ├── design (설계)
  ├── code (구현)
  ├── review (검토)
  └── test (테스트)
```
각 블록을 완성하여 더 복잡한 태스크를 해금(unlock)한다.

### 4.3 Dependency Layer Enforcement
```
Types → Config → Repo → Service → Runtime → UI
```
- 에이전트가 이 레이어 내에서만 동작하도록 제한
- 구조적 테스트가 모듈 레이어 위반을 자동 감지하고 방지
- 의존성이 통제된 순서로 흐름

### 4.4 Humans Steer, Agents Execute
엔지니어는 아키텍트가 된다:
- 인간의 역할: **제약 정의, 피드백 루프 큐레이션, 출력 검증**
- 에이전트의 역할: PR 오픈, 변경 평가, 태스크 기준 충족까지 반복

### 4.5 "On the Loop" vs "In the Loop"
- **In the loop**: 에이전트의 아티팩트를 직접 수정
- **On the loop**: 아티팩트를 생산한 **하네스를 수정**하여 원하는 결과를 얻음
- 하네스 엔지니어링은 "on the loop" 방식 — 지속적으로 하네스를 개선하여 결과의 품질을 향상

## 5. Codex 하네스 아키텍처

- Codex는 웹 앱, CLI, IDE 확장, macOS 앱 등 여러 표면(surface)에 존재
- 모든 표면이 **동일한 Codex 하네스**로 구동
- 핵심 연결 고리: **Codex App Server** — 클라이언트 친화적, 양방향 JSON-RPC API
- Codex 모델은 하네스 존재 하에 훈련됨 — 도구 사용, 실행 루프, 압축, 반복 검증이 볼트온이 아님

## 6. 대가들의 멘탈 모델

### Martin Fowler / Birgitta Böckeler
- "I like 'harness' as a word to describe the tooling and practices we can use to **keep AI agents in check**"
- **반직관적 미래**: AI 코드 신뢰성 향상은 솔루션 공간을 확장이 아닌 **제약**으로 달성
- **경고**: 기존 비표준 코드베이스에 하네스 후속 적용은 경제적으로 비현실적일 수 있음 → **pre-AI vs post-AI 앱 간 유지보수 비용 격차**
- "가장 harness-friendly한 기술 스택을 선택하게 될 수 있다"

### Simon Willison
- Codex에 대한 실용적 분석 제공
- 하네스 관점에서 Codex 작동 방식 해부

### Mitchell Hashimoto
- "harness engineering" 용어의 초기 사용자 중 하나
- OpenAI 글보다 앞서 블로그 포스트로 개념 정립

### OpenAI 팀
- "The primary job of our engineering team became enabling the agents to do useful work"
- 커스텀 인스트럭션으로 매 PR에서 자동으로 구조, 모듈 경계, 시맨틱, 커버리지 기준 강제

## 7. 스킬 설계에의 시사점

하네스 수준을 진단할 때 3축을 기준으로 평가 가능:

| 평가 축 | 확인 항목 예시 |
|---------|---------------|
| **Inform** | AGENTS.md/CLAUDE.md 존재 여부, 규칙 파일, 아키텍처 문서 |
| **Verify** | CI/CD 파이프라인, 린터 설정, 구조적 테스트, 커버리지 |
| **Correct** | 자동 정리 스크립트, 문서-코드 동기화 메커니즘 |

---

## Sources

- [OpenAI - Harness Engineering](https://openai.com/index/harness-engineering/)
- [OpenAI - Unlocking the Codex Harness](https://openai.com/index/unlocking-the-codex-harness/)
- [OpenAI - Unrolling the Codex Agent Loop](https://openai.com/index/unrolling-the-codex-agent-loop/)
- [Martin Fowler - Harness Engineering](https://martinfowler.com/articles/exploring-gen-ai/harness-engineering.html)
- [Martin Fowler - Context Engineering for Coding Agents](https://martinfowler.com/articles/exploring-gen-ai/context-engineering-coding-agents.html)
- [Martin Fowler - Humans and Agents in SE Loops](https://martinfowler.com/articles/exploring-gen-ai/humans-and-agents.html)
- [InfoQ - OpenAI Introduces Harness Engineering](https://www.infoq.com/news/2026/02/openai-harness-engineering-codex/)
- [NxCode - Harness Engineering Complete Guide](https://www.nxcode.io/resources/news/harness-engineering-complete-guide-ai-agent-codex-2026)
- [Simon Willison - How I Think About Codex](https://simonwillison.net/2026/Feb/22/how-i-think-about-codex/)
- [SmartScope - What Is Harness Engineering](https://smartscope.blog/en/blog/harness-engineering-overview/)
- [Ignorance.ai - The Emerging Harness Engineering Playbook](https://www.ignorance.ai/p/the-emerging-harness-engineering)
- [Engineering Leadership Newsletter - How OpenAI's Codex Team Works](https://newsletter.eng-leadership.com/p/how-openais-codex-team-works-and)
