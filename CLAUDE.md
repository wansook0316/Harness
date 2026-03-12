# Harness Project Context

## 프로젝트 개요
CLI 기반 AI 코딩 에이전트(Claude Code, Codex CLI, Gemini CLI)용 **프로젝트 하네스 관리 스킬 2종** 개발 프로젝트.

## 현재 상태: Phase 1 완료 (리서치 & 문서화)

### 완료된 작업
- SDD, Harness Engineering, Agentic Engineering 웹 리서치
- 리서치 문서 4개 작성 (`docs/research/`)
- 종합 분석 + 스킬 설계 원칙 도출 (`docs/research/synthesis.md`)
- README.md 작성

### 다음 단계: Phase 2 — 스킬 프로토타입 (Claude Code 우선)

#### 스킬 1: 프로젝트 하네스 세팅 (`/harness-setup`)
- Inform(Context), Verify(Constraints), Correct(GC) 3축 기반 세팅
- Constitution, CLAUDE.md, 구조적 테스트 등 생성
- 설계 원칙: "Map, not a Manual", 점진적 채택, 도구 비종속

#### 스킬 2: 하네스 수준 진단 (`/harness-diagnose`)
- Fowler/Böckeler 3축 프레임워크 기반 성숙도 평가
- Level 0~4 5단계 모델
- 진단 결과 + 구체적 개선 권고

## 핵심 설계 원칙
1. **"Map, not a Manual"**: 간결하고 구조화된 컨텍스트. 1,000줄 AGENTS.md 금지
2. **점진적 채택**: 현재 레벨 진단 → 다음 레벨로의 구체적 단계 제안
3. **도구 비종속**: Claude Code, Codex CLI, Gemini CLI 모두 지원
4. **Constitution 품질 우선**: 시니어 판단 필수, 반복적 개선 전제
5. **인지적 부채 인식**: "왜"의 기록, 팀 공유 이해 재구축

## 문서 구조
```
docs/research/sdd.md                 # SDD 방법론
docs/research/harness-engineering.md # 하네스 엔지니어링
docs/research/agentic-engineering.md # 에이전틱 엔지니어링
docs/research/synthesis.md           # 종합 + 스킬 설계 원칙 + 평가 프레임워크
```

## 참고
- 평가 프레임워크 상세 초안: `docs/research/synthesis.md` 섹션 2.2
- 크로스 플랫폼 규칙 파일 매핑: `docs/research/synthesis.md` 섹션 4
