---
name: khala
description: |
  Cross-session knowledge sharing via filesystem. Multiple concurrent Claude Code
  sessions become collectively smarter by reading/writing shared files in .khala/ directory.

  Use when:
  - User invokes /khala <session-name> to join the shared knowledge network
  - Multiple Claude Code sessions work on the same project simultaneously
  - User wants sessions to share discoveries, avoid conflicts, or stay in sync
  - User mentions "khala", "session sync", "cross-session", or "세션 공유"
---

# Khala — Cross-Session Knowledge Sharing

Share knowledge between concurrent Claude Code sessions via two append-only files in `.khala/` at the project root.

## Files

| File | Purpose | Format |
|------|---------|--------|
| `.khala/stream.jsonl` | Raw event log | JSONL, append-only |
| `.khala/insights.md` | Curated insights for sibling sessions | Markdown, append-only |

## On `/khala <session-name>` Invocation

1. Create `.khala/` directory if it doesn't exist
2. Read `.khala/insights.md` if exists — absorb current insights
3. Read `.khala/stream.jsonl` if exists — scan recent entries (last 100 lines if > 200)
4. Append registration to stream:
   ```jsonl
   {"t":"2026-02-06T14:30","s":"auth","m":"Session joined. Working on: Firebase auth"}
   ```
5. Summarize insights found (if any) and confirm session name to user

Operate under `<session-name>` for all subsequent Khala writes.

## Per-Turn Behavior

**Turn start:**
- Read `.khala/insights.md` for new entries
- If new insights found, inform user briefly: "Khala: [session] discovered [summary]"

**After significant work or user feedback:**
- Append to `.khala/stream.jsonl`
- If insight-worthy, also append to `.khala/insights.md`

## Stream Format

```jsonl
{"t":"YYYY-MM-DDTHH:MM","s":"session-name","m":"Natural language message"}
```

Write when: task started/completed, error resolved, dependency discovered, user feedback received, shared file modified.

```jsonl
{"t":"2026-02-06T14:42","s":"auth","m":"Firestore rules updated — /users/{uid} now requires auth"}
{"t":"2026-02-06T15:15","s":"auth","m":"User requested session-based auth instead of JWT"}
```

## Insight Format

Append to `.khala/insights.md`:

```markdown
### [HH:MM] session-name — Brief title

1-3 sentences. Essential knowledge other sessions need now.

---
```

## Insight Criteria

**Write when ANY apply:**
1. Affects sibling sessions — shared resource changed, API modified, dependency added
2. Prevents duplicate effort — "tried X, failed because Y"
3. Architectural decision — pattern others must follow
4. Non-obvious discovery — saves siblings from wasted time

**Skip when:** routine progress, session-internal decisions, common knowledge.

## File Size

- Stream > 200 lines → read last 100 only
- Insights → always read in full

## Rules

1. **Append-only** — never modify existing entries
2. **Concise** — stream < 200 chars, insights < 3 sentences
3. **Honest timestamps** — use actual current time
4. **Read before write** — check insights at turn start
5. **No conversation** — announcements only, no replies between sessions
