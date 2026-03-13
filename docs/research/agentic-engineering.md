# Agentic Engineering

> "'Agentic' because the new default is that you are not writing the code directly 99% of the time, you are orchestrating agents who do. 'Engineering' to emphasize that there is an art & science and expertise to it." — Andrej Karpathy

## 1. 핵심 개념

Agentic Engineering은 Andrej Karpathy가 2026년 2월에 제안한 용어로, "vibe coding"의 진화형이다. 인간 개발자가 코드를 직접 작성하는 대신 **AI 에이전트 시스템을 오케스트레이션하여 소프트웨어를 구축**하는 패러다임.

핵심 전환:
- 엔지니어링 역량이 사라지는 것이 아니라 **방향이 전환**된다
- 코드 작성에서 → **시스템 설계, 제약조건, 피드백 루프 설계**로

## 2. Vibe Coding → Agentic Engineering 진화

### 2.1 타임라인
- **2025년 2월**: Karpathy가 "vibe coding" 트윗 — "a shower of thoughts throwaway tweet that I just fired off"
- **2025년**: vibe coding이 업계 표준 용어가 됨
- **2026년 2월**: Karpathy가 "agentic engineering"으로 전환 제안

### 2.2 비교

| 차원 | Vibe Coding (2025) | Agentic Engineering (2026) |
|------|-------------------|---------------------------|
| **본질** | 프롬프트로 코드 생성 | 에이전트 시스템 오케스트레이션 |
| **인간 역할** | 프롬프트 작성자 | 아키텍트 + PM + 검증자 |
| **적합성** | 프로토타입, 주말 해킹 | 프로덕션, 전문 개발 |
| **핵심 역량** | 좋은 프롬프트 작성 | 시스템 설계, 제약조건, 피드백 루프 |
| **품질 보증** | 수동/사후 | 구조적/자동/사전 |
| **산업 성숙도** | 초기 실험 | 전문 엔지니어링 규율 |

### 2.3 Karpathy의 핵심 인사이트
> "Something you can learn and become better at, with its own depth of a different kind."

업계가 **"vibes"에서 "discipline"으로** 이동. 이는 단순한 리브랜딩이 아니라 산업의 성숙을 의미.

## 3. 소프트웨어 엔지니어링의 세대 전환

```
SE 1.0: 전통적 소프트웨어 엔지니어링 (인간이 모든 코드 작성)
SE 2.0: AI 보조 개발 (Copilot, 자동완성)
SE 3.0: Agentic Software Engineering (에이전트가 자율적으로 코드 작성/테스트/제출)
```

SE 3.0의 특징:
- 강력한 자율 에이전트가 코드를 작성, 테스트, 제출
- 짧은 프롬프트로 전체 마이크로 애플리케이션 생성 가능
- 전례 없는 생산성의 가능성

## 4. 팀 구조의 변화

### 4.1 새로운 팀 구성
> "Agentic engineering transforms all members of the development team into product managers."

과거: 다양한 유형의 엔지니어(프론트엔드, 백엔드, DevOps 등)
현재: **"AI 에이전트가 무엇을 해야 하는지 명시하는"** 하나의 기본 역할을 공유하는 인간들

### 4.2 멀티 에이전트 시스템
- 여러 에이전트가 동시에 협력하여 태스크를 분담
- 각 에이전트가 고유 역할 (SW 엔지니어, PM, 분석가 등)
- 단일 오케스트레이션 에이전트가 조율
- 더 정교한 의사결정과 간소화된 워크플로우

### 4.3 Agile의 진화
에이전틱 엔지니어링 시대에도 Agile은 여전히 중요하나, 적응이 필요:
- 인간만이 빌드할 때의 관행이 AI 에이전트 시대에 항상 충분하지 않음
- 스프린트 계획, 리뷰, 회고의 초점이 변화

## 5. Cognitive Debt (인지적 부채)

### 5.1 정의
Margaret-Anne Storey (2026년 2월):
> "Technical debt lives in the code; **cognitive debt lives in people.**"

### 5.2 속도-이해 격차
- AI 에이전트: 분당 140~200줄 유의미한 코드 생성
- 인간: 분당 20~40줄 이해
- **5~7배의 속도-이해 격차**가 "인지적 부채"를 생성

### 5.3 통계
- 67% 개발자가 AI 생성 코드 디버깅에 더 많은 시간 소요
- 68%가 보안 취약점 해결에 더 많은 시간 소요
- 59%가 더 많은 배포 문제 보고
- **속도 이점이 리뷰/디버그/수정 사이클에서 증발**

### 5.4 교훈적 사례
Storey의 학생 팀 사례 (7~8주차):
- 처음엔 기술 부채를 탓했으나, 진짜 문제는 **아무도 설계 결정의 이유를 설명할 수 없었던 것**
- "시스템의 이론이 조각나거나 완전히 사라졌다"
- 기술 부채보다 인지적 부채가 더 빠르게 축적되어 팀을 마비시킴

### 5.5 기술 부채 vs 인지적 부채
- **기술 부채**: 의식적 트레이드오프, 코드베이스에 보이고, 계획 가능
- **인지적 부채**: 사람들의 머릿속에 존재, 보이지 않고, 훨씬 교활함

### 5.6 실무자의 경험
> "After using many claudes non-stop for a month, I feel stupider. Not in a good way... but in a way where I find myself becoming increasingly lazy, deciding not to put in the cognitive work required to build a computer system of any meaningful complexity." — Rushabh Doshi

## 6. Context Engineering (기반 기술)

### 6.1 정의
> "Context engineering is curating what the model sees so that you get a better result." — Bharani Subramaniam

프롬프트 엔지니어링을 넘어서는 개념: "어떤 컨텍스트 구성이 모델의 원하는 행동을 생성할 가능성이 가장 높은가?"

### 6.2 코딩 에이전트에서의 적용
- AGENTS.md, CLAUDE.md, 규칙 파일 등의 폭발적 증가
- Claude Code가 이 영역에서 혁신을 주도
- MIT Technology Review: 2025년을 "vibe coding에서 context engineering으로의 전환"으로 규정

### 6.3 실전 조언
> "Context engineering is underrated. Learn to manage agent context deliberately—use skills files, use commands, pull in relevant context only when it's needed. Dump too much in and you get context rot/poisoning: the agent drowns in irrelevant information and loses track of what actually matters. Think of it like briefing a contractor."

## 7. 시니어 엔지니어의 가치 증가

### 7.1 반직관적 통찰
> "This isn't a market that's getting worse for senior engineers—it's a market that's getting worse for engineers who only wrote code."

코드 생성이 저렴해지면 가장 가치 있는 엔지니어:
- 사용자/고객 문제를 **명확한 의도**로 합성
- 품질/아키텍처/설계 **가드레일**을 세우고
- 에이전트에서 **훌륭한 결과**를 이끌어내는 사람

### 7.2 에이전트 실패 시 필요한 것
AI 에이전트는 자신의 출력이 잘못되었음을 알 컨텍스트적 이해가 부족하다. 에이전트가 실패하면(그리고 반드시 실패한다), 문제가 **명세에 있는지, 템플릿 규칙에 있는지, 에이전트의 해석에 있는지** 진단할 수 있는 시니어 엔지니어가 필요.

## 8. 현실적 품질 데이터

- AI가 생성한 "그럴듯한" 수정의 29.6%가 행동 회귀를 도입하거나 엄격한 재테스트에서 오류
- GPT-4 패치의 진짜 해결률: 상세 수동 감사 후 12.47% → 3.97%로 하락
- AI 에이전트가 자주 단일 파일에 국한된 표면적 패치를 생성 (인간 개발자와 달리)

## 9. 2026년 승리 공식

```
Structured Context (AGENTS.md, 아키텍처 가드레일, SDD)
+ Tiered Rigor (일회용 vs 내구성 코드, 위험 기반 리뷰)
+ Smaller Teams with Higher Leverage
```

### 완화 전략
- 팀의 최소 1명이 AI 생성 변경을 완전히 이해한 후 출시
- 무엇이 변경되었는지뿐만 아니라 **왜** 변경되었는지 문서화
- 코드 리뷰, 회고, 지식 공유 세션을 통한 공유 이해 재구축

## 10. 산업 채택 현황

- Stack Overflow 2025 설문: 84%가 AI 보조 프로그래밍 사용 또는 의향
- Gartner (2025년 1월): 61% 조직이 agentic AI 개발 착수
- Gartner 예측: 2028년까지 33% 엔터프라이즈 앱에 agentic AI (2024년 0%에서)
- **경고**: 2027년까지 40% agentic AI 배포가 취소될 것 (비용, 불명확한 가치, 위험 관리 부실)

## 11. 떠오르는 공식 방법론

### AgentsWay
- AI 에이전트 기반 팀을 위한 공식 소프트웨어 개발 방법론
- 비SW 엔지니어링 분야(법률, 관광, 사이버보안)에서도 평가
- 확장성, 상호운용성, 도메인 적응성 검증

---

## Sources

- [The New Stack - From Vibes to Engineering](https://thenewstack.io/vibe-coding-agentic-engineering/)
- [The New Stack - Vibe Coding is Passé](https://thenewstack.io/vibe-coding-is-passe/)
- [CIO - 5 Ways Agentic Engineering Transforms Agile](https://www.cio.com/article/4086747/5-ways-agentic-engineering-transforms-agile-practices.html)
- [IBM - What is Agentic Engineering](https://www.ibm.com/think/topics/agentic-engineering)
- [Seven Peaks - A Practical Guide to Agentic Software Development](https://sevenpeakssoftware.com/blog/a-practical-guide-to-agentic-software-development)
- [Glide - What is Agentic Engineering](https://www.glideapps.com/blog/what-is-agentic-engineering)
- [NxCode - Agentic Engineering Complete Guide](https://www.nxcode.io/resources/news/agentic-engineering-complete-guide-vibe-coding-ai-agents-2026)
- [Margaret-Anne Storey - Cognitive Debt](https://margaretstorey.com/blog/2026/02/09/cognitive-debt/)
- [Margaret-Anne Storey - Cognitive Debt Revisited](https://margaretstorey.com/blog/2026/02/18/cognitive-debt-revisited/)
- [Simon Willison - Cognitive Debt](https://simonwillison.net/2026/Feb/15/cognitive-debt/)
- [Blake Crosley - Your Agent Writes Faster Than You Can Read](https://blakecrosley.com/blog/cognitive-debt-agents)
- [Anthropic - Effective Context Engineering](https://www.anthropic.com/engineering/effective-context-engineering-for-ai-agents)
- [Martin Fowler - Context Engineering for Coding Agents](https://martinfowler.com/articles/exploring-gen-ai/context-engineering-coding-agents.html)
- [Tal Rotbart - Advice to a Senior Engineer](https://medium.com/@rotbart/advice-to-a-senior-engineer-looking-for-work-in-an-ai-world-153aa9cd3d81)
- [arxiv - Agentic Software Engineering Research Roadmap](https://arxiv.org/html/2509.06216v1)
- [arxiv - AgentsWay Methodology](https://arxiv.org/pdf/2510.23664)
- [arxiv - AI Agentic Programming Survey](https://arxiv.org/html/2508.11126v1)
- [LangChain - State of Agent Engineering](https://www.langchain.com/state-of-agent-engineering)
- [Karpathy on X - Vibe Coding Retrospective](https://x.com/karpathy/status/2019137879310836075)
