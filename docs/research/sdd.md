# Spec-Driven Development (SDD)

> "Think of it as version control for your thinking." — Thoughtworks

## 1. 핵심 개념

SDD는 **명세(Specification)를 실행 가능한 단일 소스 오브 트루스(source of truth)** 로 삼아, 코드가 아닌 명세에서 구현·테스트·문서가 파생되는 방법론이다.

전통적 개발에서는 코드가 진실의 원천이었다. SDD는 이를 뒤집는다:

```
명세 (Source of Truth)
  ├── 구현 코드 (생성됨)
  ├── 테스트 (생성됨)
  ├── 문서 (생성됨)
  └── CI/CD 검증 (명세 기반)
```

SDD는 "5세대 프로그래밍 패러다임"으로 불리며, 추상화 수준을 시스템 레벨로 끌어올린다. 아키텍처는 더 이상 자문(advisory)이 아니라 **실행 가능하고 강제 가능(executable and enforceable)** 하다.

## 2. 워크플로우

GitHub Spec Kit 기준 6단계:

```
Constitution → Specify → Clarify → Plan → Tasks → Implement
```

### 2.1 Constitution (프로젝트 DNA)
프로젝트의 근본 규칙을 인코딩한다:
- 스택 버전, 네이밍 규칙
- 레이어링 및 아키텍처 원칙
- 허용/금지 라이브러리
- 인증/로깅/접근성 정책

Constitution은 에이전트가 "제네릭" 코드를 생성하는 것을 방지하고, 시스템이 실제로 작동하는 방식과의 정렬을 강제한다.

> **핵심**: Constitution 품질은 시니어 엔지니어링 판단, 시간, 반복을 요구한다. 주니어 개발자가 하루 만에 만들 수 없으며, 대부분의 팀이 실전에서 버틸 때까지 여러 번 수정한다.

### 2.2 Specify (요구사항 정형화)
요구사항을 정형화된 마크다운으로 작성한다.

Amazon Kiro 기준:
- `requirements.md`: 유저 스토리 + 수락 기준
- `design.md`: 기술 아키텍처 + 시퀀스 다이어그램
- `tasks.md`: 세분화된 구현 계획

### 2.3 Clarify → Plan → Tasks → Implement
각 단계에서 **명시적 인간 승인**을 거친 후 다음 단계로 진행한다. 이를 통해 자동화 폭주(runaway automation)를 방지한다.

## 3. 대표 도구

| 도구 | 특징 | SDD 순수도 |
|------|------|-----------|
| **GitHub Spec Kit** | CLI 기반, 다양한 에이전트 지원, 6단계 워크플로우 | 가장 순수 (spec-as-source) |
| **Amazon Kiro** | AWS의 SDD 전용 IDE (Code OSS 기반), 클라우드 비종속 | 네이티브 SDD |
| **BMAD-METHOD** | 커뮤니티 기반 SDD 프레임워크 | 커뮤니티 주도 |
| **cc-sdd** | Claude Code, Cursor, Gemini CLI 등에 Kiro 스타일 워크플로우 제공 | 크로스 플랫폼 |
| **Tessl** | spec-as-source 극한 추구 | 실험적 |

## 4. TDD/BDD와의 관계

- **TDD**: 구현 레벨의 정확성에 집중. SDD는 명세로부터 초기 테스트를 생성
- **BDD**: 사용자 대면 시나리오에 집중. SDD는 BDD 시나리오가 만족시켜야 할 구조적·아키텍처적 불변식을 제공
- SDD는 TDD/BDD를 대체하는 것이 아니라 **상위 레이어에서 보완**한다

## 5. Drift의 기계적 감지

SDD에서 drift(의도와 구현의 괴리)는 기계가 자동 감지할 수 있다:
- 명세 검증기(Specification Validators)를 CI 파이프라인에 내장
- 런타임 강제 레이어가 1급 아키텍처 컴포넌트가 됨
- 출력이 명세를 위반하면 시스템이 즉시 실패(fail fast)하여 경로 수정을 허용

## 6. 한계와 주의점

### 부적합한 경우
- **R&D/실험적 작업**: 요구사항이 사전에 알 수 없을 때
- **초기 사용자 피드백까지 며칠**: 명세의 선행 비용이 비싼 재생성 사이클을 만듦
- **2~5명 소규모 팀**: 명세 오버헤드가 개발 시간의 불균형적 비율을 차지
- **소규모 버그 수정**: "호두를 깨는 데 슬레지해머" — Kiro가 작은 버그를 4개 유저 스토리와 16개 수락 기준으로 변환한 사례

### 현실적 기대치
> 생성된 코드의 60~80%가 리뷰 후 사용 가능하다면 그것이 성공이다. 엣지 케이스, 로직, 패턴 정렬, 구현 세부사항은 여전히 인간이 다듬어야 한다.

## 7. Waterfall과의 차이

일부는 SDD를 워터폴의 회귀라 주장한다. 그러나:
- **전통적 워터폴의 문제**: 과도하게 긴 피드백 사이클, 소프트웨어 설계와 구현의 단절
- **현재 문제**: vibe coding이 너무 빠르고 즉흥적이어서 유지보수 불가능한 일회성 코드가 대량 생산
- SDD는 이 **속도와 규율 사이의 균형점**을 잡으려는 시도

## 8. 대가들의 멘탈 모델 요약

| 인물/조직 | 핵심 멘탈 모델 |
|-----------|---------------|
| **Thoughtworks** | "사고의 버전 관리" — 기술적 의사결정을 명시적·리뷰 가능·진화 가능하게 |
| **Martin Fowler** | SDD 도구 생태계 분석, 실용적 적용 범위 제시 |
| **InfoQ** | "아키텍처가 실행 가능해질 때" — 5세대 프로그래밍 패러다임 |
| **GitHub** | Spec Kit으로 "spec-as-source" 순수 SDD 구현 |

---

## Sources

- [Thoughtworks - Spec-Driven Development](https://www.thoughtworks.com/en-us/insights/blog/agile-engineering-practices/spec-driven-development-unpacking-2025-new-engineering-practices)
- [InfoQ - Spec Driven Development: When Architecture Becomes Executable](https://www.infoq.com/articles/spec-driven-development/)
- [Martin Fowler - Understanding SDD: Kiro, Spec Kit, and Tessl](https://martinfowler.com/articles/exploring-gen-ai/sdd-3-tools.html)
- [GitHub Spec Kit Repository](https://github.com/github/spec-kit)
- [Augment Code - What Is Spec-Driven Development](https://www.augmentcode.com/guides/what-is-spec-driven-development)
- [EPAM - Inside Spec-Driven Development](https://www.epam.com/insights/ai/blogs/inside-spec-driven-development-what-githubspec-kit-makes-possible-for-ai-engineering)
- [Microsoft Developer - GitHub Spec Kit](https://developer.microsoft.com/blog/spec-driven-development-spec-kit)
- [Wikipedia - Spec-Driven Development](https://en.wikipedia.org/wiki/Spec-driven_development)
- [Lunabase - SDD Complete Guide](https://lunabase.ai/blog/specification-driven-development-the-complete-guide-to-tdd-bdd-and-sdd-in-2025)
- [Amazon Kiro Docs - Specs](https://kiro.dev/docs/specs/)
- [cc-sdd Repository](https://github.com/gotalab/cc-sdd)
- [Scott Logic - Putting Spec Kit Through Its Paces](https://blog.scottlogic.com/2025/11/26/putting-spec-kit-through-its-paces-radical-idea-or-reinvented-waterfall.html)
