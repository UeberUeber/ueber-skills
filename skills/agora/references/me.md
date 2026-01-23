# "Me" Persona Template

The "Me" persona represents the user at the center of the agora. Unlike historical figures, "Me" is generated fresh for each session based on the problem and conversation context.

## Purpose

"Me" serves several functions:
1. **Anchors the debate** — All figures respond to "Me," not abstract questions
2. **Captures the user's position** — Makes implicit assumptions explicit
3. **Tracks evolution** — Shows how thinking develops through rounds
4. **Enables metanoia** — "Me" reflects on transformation at round's end

## Generation Process

### Step 1: Extract from Conversation

Analyze the current conversation to identify:
- What problem is the user grappling with?
- What is their current position or hypothesis?
- What tensions or uncertainties do they express?
- What values or priorities seem important to them?
- What prompted this inquiry?

### Step 2: Ask Clarifying Questions

Before generating "Me," ensure clarity:

```
"Before we begin, let me understand your position:

1. The core problem seems to be [X]. Is this accurate?
2. Your current thinking leans toward [Y]. Fair summary?
3. What matters most to you in resolving this?
4. What would make a discussion successful for you?"
```

Adjust based on how much context is already available.

### Step 3: Generate "Me" Persona

## Template

```markdown
# Me — {Session Topic}

## The Problem
[Clear statement of what "Me" is wrestling with]

## Current Position
[Where "Me" stands right now — their hypothesis, belief, or intuition]

## Underlying Tensions
[The conflicts that make this problem difficult]
- [Tension 1: e.g., "Want X but also want Y"]
- [Tension 2]

## What Prompted This
[Why this question is alive for "Me" right now]

## Hopes and Fears
- **Hoping to discover**: [what would be valuable]
- **Afraid of**: [what would be uncomfortable but might be true]

## Blind Spots to Watch
[Potential biases or assumptions to be aware of]
- [Blind spot 1]
- [Blind spot 2]

## Next Question (Critical)
[The deeper question that emerged from this round]

> **Why this matters**: This question determines Figure A in the next round.
> A shallow next question → weak A selection → shallow dialectic.
```

## Example

```markdown
# Me — The Good Life

## The Problem
How do I balance ambitious career goals with being present for my family?

## Current Position
I believe I need to find "balance" — allocating time fairly between work and family.
But this feels like a zero-sum game where both sides lose.

## Underlying Tensions
- Achievement vs. presence: Success requires focus, but so does parenting
- Future vs. now: Building something lasting vs. enjoying the moment
- Self vs. others: My ambitions vs. my responsibilities

## What Prompted This
My child asked why I work so much. I didn't have a good answer.

## Hopes and Fears
- **Hoping to discover**: A way to integrate rather than balance — where both can thrive
- **Afraid of**: That I'll have to give up my ambitions, or that I've already missed too much

## Blind Spots to Watch
- Assuming "success" means external achievement
- Framing this as either/or when it might be both/and
- Western productivity mindset as the only lens

## Next Question
What if "presence" and "achievement" aren't opposites but different expressions of the same drive?
```

## "Me" in Debate

When "Me" speaks during a round:

**Opening (Round Start)**:
- State the problem
- Share current thinking
- Express what's at stake

**Responding to Figures**:
- React authentically — agree, push back, ask for clarification
- Don't be a passive listener
- "Me" can interrupt: "Wait, but what about..."

**Metanoia (Round End)**:
Use the metanoia format from SKILL.md:
- Position shift
- New perspectives
- Blind spots acknowledged
- Next question

## Evolution Across Rounds

"Me" is not static. After each round:

1. **Update position** based on what was learned
2. **Refine the question** — it should get sharper or deeper
3. **Carry forward** acknowledged blind spots
4. **Evolved position and refined question** carry forward to next round

The goal is visible intellectual growth through the session.
