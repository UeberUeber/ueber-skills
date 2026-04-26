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

### `/brainstorm-ing` - Structured Brainstorming + Implementation

A multi-agent brainstorming skill that generates 90-120+ ideas through structured divergent thinking, then converges into an actionable implementation.

**When to use:**
- You need to solve a complex problem creatively
- You want diverse perspectives before building something
- You want brainstorming that actually leads to implementation

**How it works:**

**Part 1 — Brainstorming:**
1. Define the problem (constraints, goals, open spaces)
2. Three expert personas are selected (triangulated for maximum diversity)
3. Independent divergence — each persona generates ~30-40 ideas using 7 creativity techniques + Verbalized Sampling
4. Cross-pollination (Teams) — personas react to each other's ideas, creating chain reactions
5. Individual integration — each persona digests what they learned
6. Convergence — independent evaluation, then you choose a direction

**Part 2 — Implementation:**
1. Define deliverables
2. Assemble a builder team
3. Build collaboratively (Teams)
4. Review against completion criteria

**Key techniques:**
- **Verbalized Sampling** — each idea shows its generation probability (%), breaking mode collapse and increasing diversity 1.6-2.1x
- **Contradiction pairs** — opposing ideas become seeds for breakthrough combinations
- **7 forced-expansion techniques** — SCAMPER, combinatorial decomposition, TRIZ, provocation, assumption reversal, worst possible idea, exaptation

**Generated files:**

The skill creates files in your project's working directory as agents collaborate. All outputs are delivered through the conversation.

### `/noo` - The Fundamental Process

Apply Christopher Alexander's living structure generation process to any problem. Based on *The Nature of Order*, this skill suggests optimal "generative sequences" — the order of steps that makes each subsequent step easier.

**When to use:**
- Planning implementation approach for a complex task
- Designing systems or architecture
- Breaking down complex tasks into an optimal sequence
- Seeking the order of operations that maximizes coherence

**How it works:**
1. Perceive the whole — absorb the deep structure of your situation
2. Identify latent centers — what could be strengthened next?
3. Choose the center whose strengthening gives the whole the most life
4. Strengthen it while also strengthening larger, adjacent, and smaller centers
5. Repeat — each step makes the next step easier

**Key concepts:**
- **The Coin Metaphor** — don't toss all coins at once; toss one at a time in the right order
- **Structure-preserving transformations** — each step preserves and extends what came before
- **Verification question** — "If I do this step now, does the next step become easier or harder?"

### `/khala` - Cross-Session Knowledge Sharing

Share knowledge between concurrent Claude Code sessions via shared files. Multiple sessions become collectively smarter by reading/writing to a shared `.khala/` directory.

**When to use:**
- Multiple Claude Code sessions work on the same project simultaneously
- Sessions need to share discoveries, avoid conflicts, or stay in sync
- You want parallel sessions to be aware of each other's progress

**How it works:**
1. Invoke `/khala <session-name>` to join the shared knowledge network
2. The session reads existing insights and registers itself
3. On each turn, the session checks for new insights from siblings
4. After significant work, the session broadcasts discoveries

**Shared files:**

| File | Purpose |
|------|---------|
| `.khala/stream.jsonl` | Raw event log (append-only JSONL) |
| `.khala/insights.md` | Curated insights for sibling sessions (append-only Markdown) |

### `/itchio-setting` - HTML5 Game Starter

Scaffold a new itch.io-ready HTML5 game project with a clean folder structure and a playable starter shell.

**When to use:**
- Starting a new browser game for itch.io
- Creating a Phaser, Pixi, Canvas, WebGL, or static HTML5 game skeleton
- Setting up project folders so later distribution is straightforward

**How it works:**
1. Derives a lowercase hyphen-case game slug
2. Creates an itch-friendly source structure with root `index.html`, `js/`, `css/`, `resources/`, and `vendor/`
3. Adds a playable placeholder with canvas/input/update loop
4. Keeps paths relative and prepares the project for later packaging with `/itchio-dist`

### `/itchio-dist` - itch.io HTML5 Distribution

Package an existing playable HTML5 game into a clean itch.io upload folder and ZIP.

**When to use:**
- Preparing an existing HTML5 game for itch.io upload
- Creating `dist/itch/<game-slug>/` and `<game-slug>-itch.zip`
- Cleaning dev-only files, recordings, local debug tools, and private metadata from a release

**How it works:**
1. Detects the game root and entry `index.html`
2. Copies only the required runtime files into a clean release folder
3. Vendors pinned engine CDN files when practical
4. Verifies the ZIP has root `index.html` and validates the release with a local HTTP server

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

### `/brainstorm-ing` - 구조화된 브레인스토밍 + 구현

멀티 에이전트 브레인스토밍 스킬. 구조화된 발산적 사고로 90-120개 이상의 아이디어를 생성한 뒤, 수렴해서 실제 구현까지 이어갑니다.

**사용 시점:**
- 복잡한 문제를 창의적으로 풀어야 할 때
- 무언가를 만들기 전에 다양한 관점이 필요할 때
- 실제 구현으로 이어지는 브레인스토밍이 필요할 때

**작동 방식:**

**Part 1 — 브레인스토밍:**
1. 문제 정의 (제약, 목표, 열린 공간)
2. 전문가 페르소나 3명 선정 (최대 다양성을 위한 삼각 배치)
3. 독립 발산 — 각 페르소나가 7가지 창의 기법 + Verbalized Sampling으로 ~30-40개 아이디어 생성
4. 교차 수분 (Teams) — 페르소나들이 서로의 아이디어에 반응, 연쇄 반응 발생
5. 개인 통합 — 각 페르소나가 배운 것을 소화
6. 수렴 — 독립 평가 후 방향 선택

**Part 2 — 실행:**
1. 산출물 정의
2. 빌더 팀 구성
3. 협력 개발 (Teams)
4. 완성 기준 대조 검토

**핵심 기법:**
- **Verbalized Sampling** — 각 아이디어에 생성 확률(%)을 표시해 mode collapse를 깨고 다양성 1.6-2.1배 향상
- **모순 쌍** — 정반대 아이디어가 돌파구 조합의 씨앗이 됨
- **7가지 강제 확장 기법** — SCAMPER, 조합 분해, TRIZ, Provocation, Assumption Reversal, Worst Possible Idea, Exaptation

**생성되는 파일:**

에이전트가 협업하면서 프로젝트 작업 디렉토리에 파일을 생성합니다. 모든 결과물은 대화를 통해 전달됩니다.

### `/noo` - 근본 프로세스

크리스토퍼 알렉산더의 살아있는 구조 생성 프로세스를 문제에 적용합니다. *The Nature of Order*에 기반하여, 각 단계가 다음 단계를 더 쉽게 만드는 최적의 "생성 시퀀스"를 제안합니다.

**사용 시점:**
- 복잡한 작업의 구현 접근법을 계획할 때
- 시스템이나 아키텍처를 설계할 때
- 복잡한 작업을 최적 순서로 분해할 때
- 일관성을 극대화하는 작업 순서를 찾을 때

**작동 방식:**
1. 전체를 인지 — 상황의 깊은 구조를 흡수
2. 잠재적 중심 파악 — 다음에 무엇을 강화할 수 있는가?
3. 전체에 가장 큰 생명력을 주는 중심을 선택하여 강화
4. 동시에 더 큰, 인접한, 더 작은 중심도 강화
5. 반복 — 각 단계가 다음 단계를 더 쉽게 만듦

**핵심 개념:**
- **동전 비유** — 모든 동전을 한 번에 던지지 말고, 올바른 순서로 하나씩
- **구조 보존 변환** — 각 단계가 이전 것을 보존하고 확장
- **검증 질문** — "이 단계를 지금 하면, 다음 단계가 더 쉬워지는가 어려워지는가?"

### `/khala` - 교차 세션 지식 공유

동시에 실행되는 여러 Claude Code 세션 간 지식을 공유합니다. 공유 `.khala/` 디렉토리를 통해 여러 세션이 집단적으로 더 똑똑해집니다.

**사용 시점:**
- 여러 Claude Code 세션이 같은 프로젝트에서 동시 작업할 때
- 세션 간 발견 공유, 충돌 방지, 동기화가 필요할 때
- 병렬 세션이 서로의 진행 상황을 인지하길 원할 때

**작동 방식:**
1. `/khala <세션이름>`으로 공유 지식 네트워크 합류
2. 기존 인사이트를 읽고 자신을 등록
3. 매 턴마다 형제 세션의 새로운 인사이트 확인
4. 중요한 작업 후 발견 사항을 방송

**공유 파일:**

| 파일 | 용도 |
|------|------|
| `.khala/stream.jsonl` | 원시 이벤트 로그 (추가 전용 JSONL) |
| `.khala/insights.md` | 형제 세션을 위한 큐레이션된 인사이트 (추가 전용 Markdown) |

### `/itchio-setting` - HTML5 게임 시작 세팅

itch.io에 올리기 좋은 HTML5 게임 프로젝트의 폴더 구조와 실행 가능한 시작 뼈대를 만듭니다.

**사용 시점:**
- 새 브라우저 게임을 itch.io 목표로 시작할 때
- Phaser, Pixi, Canvas, WebGL, 정적 HTML5 게임 스켈레톤이 필요할 때
- 나중에 배포하기 쉬운 구조로 프로젝트를 시작하고 싶을 때

**작동 방식:**
1. 게임 이름을 lowercase hyphen-case 슬러그로 정리
2. 루트 `index.html`, `js/`, `css/`, `resources/`, `vendor/` 구조 생성
3. 캔버스, 입력, 업데이트 루프가 있는 실행 가능한 placeholder 추가
4. 상대 경로를 유지하고 이후 `/itchio-dist` 패키징이 쉬운 형태로 정리

### `/itchio-dist` - itch.io HTML5 배포

이미 실행 가능한 HTML5 게임을 itch.io 업로드용 배포 폴더와 ZIP으로 정리합니다.

**사용 시점:**
- 기존 HTML5 게임을 itch.io에 업로드할 때
- `dist/itch/<game-slug>/`와 `<game-slug>-itch.zip`을 만들 때
- 개발용 파일, 녹화 파일, 로컬 디버그 도구, private metadata를 릴리즈에서 제외하고 싶을 때

**작동 방식:**
1. 게임 루트와 진입점 `index.html` 확인
2. 실행에 필요한 파일만 깨끗한 release folder로 복사
3. 가능하면 pinned engine CDN 파일을 `vendor/`에 로컬화
4. ZIP 루트에 `index.html`이 있는지 확인하고 local HTTP server로 검증

## 라이센스

[CC BY-NC 4.0](LICENSE) - 저작자 표시 필수, 상업적 이용 금지.
