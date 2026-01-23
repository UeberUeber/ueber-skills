# ueber-skills

A collection of custom skills following the SKILL.md standard.

## Compatibility

These skills work with any AI coding assistant that supports the SKILL.md format:
- [Claude Code](https://docs.anthropic.com/en/docs/claude-code/skills)
- [Google Antigravity](https://antigravity.google/docs/skills)
- And other SKILL.md-compatible tools

## Installation

Copy the `skills` folder to your tool's configuration directory.

| Platform | Path |
|----------|------|
| Claude Code (global) | `~/.claude/skills/` |
| Claude Code (project) | `.claude/skills/` |
| Antigravity (global) | `~/.gemini/antigravity/skills/` |
| Antigravity (project) | `.agent/skills/` |

For other tools, refer to their documentation.

## Available Skills

### `/agora` - The Wisdom Square

An open square where wisdom from across time and space gathers to debate your problem.

**When to use:**
- You want diverse perspectives on a problem or idea
- You need deep exploration through dialectical discussion
- You want to challenge your thinking with opposing viewpoints

**How it works:**
1. You bring a problem to the square
2. Historical figures are summoned based on relevance (not preselected)
3. Thesis → Antithesis → Metanoia structure unfolds
4. The Devil provides meta-critique of every discussion
5. You reflect on what changed in your thinking

**Generated files:**

When you run `/agora`, the following structure is created in your project root:

```
{project-root}/
└── agora/
    ├── sessions/
    │   └── {topic-name}/
    │       ├── problem.md      # Clarified problem statement
    │       ├── me.md           # Your persona for this session
    │       ├── debate.md       # Full debate transcript
    │       └── metanoia.md     # Final insights
    │
    └── personas/
        └── {figure-name}/
            ├── knowledge.md    # Figure's thinking system (fixed)
            └── encounters.md   # Past interactions (accumulates)
```

The `personas/` folder acts as a reusable wisdom library — figures remember past encounters across sessions.

## License

[CC BY-NC 4.0](LICENSE) - Free to use and modify with attribution, but not for commercial purposes.

---

# 한국어

SKILL.md 표준을 따르는 커스텀 스킬 모음집입니다.

## 호환성

SKILL.md 포맷을 지원하는 모든 AI 코딩 도구에서 사용할 수 있습니다:
- [Claude Code](https://docs.anthropic.com/en/docs/claude-code/skills)
- [Google Antigravity](https://antigravity.google/docs/skills)
- 기타 SKILL.md 호환 도구

## 설치 방법

`skills` 폴더를 사용하는 도구의 설정 디렉토리에 복사하세요.

| 플랫폼 | 경로 |
|--------|------|
| Claude Code (전역) | `~/.claude/skills/` |
| Claude Code (프로젝트) | `.claude/skills/` |
| Antigravity (전역) | `~/.gemini/antigravity/skills/` |
| Antigravity (프로젝트) | `.agent/skills/` |

다른 도구는 해당 문서를 참조하세요.

## 사용 가능한 스킬

### `/agora` - 지혜의 광장

시공간을 초월한 지혜가 모여 당신의 문제를 토론하는 열린 광장입니다.

**사용 시점:**
- 문제나 아이디어에 대해 다양한 관점이 필요할 때
- 변증법적 토론을 통한 깊은 탐구가 필요할 때
- 반대 의견으로 자신의 생각에 도전하고 싶을 때

**작동 방식:**
1. 당신이 문제를 광장에 가져옵니다
2. 문제와 관련된 역사적 인물들이 소환됩니다 (미리 정해진 게 아님)
3. 정(Thesis) → 반(Antithesis) → 메타노이아(Metanoia) 구조로 전개
4. 악마(Devil)가 모든 토론에 메타 비평을 제공합니다
5. 당신의 생각이 어떻게 변했는지 성찰합니다

**생성되는 파일:**

`/agora` 실행 시 프로젝트 루트에 다음 구조가 생성됩니다:

```
{project-root}/
└── agora/
    ├── sessions/
    │   └── {topic-name}/
    │       ├── problem.md      # 정제된 문제 정의
    │       ├── me.md           # 이 세션에서의 당신의 페르소나
    │       ├── debate.md       # 전체 토론 기록
    │       └── metanoia.md     # 최종 인사이트
    │
    └── personas/
        └── {figure-name}/
            ├── knowledge.md    # 인물의 사고 체계 (고정)
            └── encounters.md   # 과거 대화 기록 (누적)
```

`personas/` 폴더는 재사용 가능한 지혜 라이브러리 역할을 합니다 — 인물들은 세션을 넘어 과거 대화를 기억합니다.

## 라이센스

[CC BY-NC 4.0](LICENSE) - 저작자 표시 필수, 상업적 이용 금지.
