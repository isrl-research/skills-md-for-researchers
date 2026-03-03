---
name: atomic-extractor
description: Extract generalizable principles, heuristics, or skills from emails, feedback exchanges, memos, meeting notes, or document threads and convert them into structured atomic markdown notes with consistent YAML frontmatter. Use this skill whenever a user asks to "extract lessons", "turn this into atomics", "derive principles", "capture heuristics", "convert this exchange into lab knowledge", or when processing professional communication that contains transferable insight. Do NOT use this for simple summaries. This skill is specifically for distilling durable, reusable knowledge.
---

# Atomic Extractor

This skill converts real-world communication into durable, generalizable atomic knowledge units.

An **atomic** is a standalone markdown note that captures:

- A transferable **principle**, **heuristic**, or **skill**
- A concise explanation of why it matters
- A grounded example from the source context
- Clear application guidance
- Structured YAML frontmatter for programmatic retrieval
- Written in second person

The goal is knowledge distillation — not summarization.

---

# Classification Model

Each extracted atomic must be classified as exactly one of:

## 1. Principle
A high-level truth about systems, incentives, history, or behavior.

Example:
> Systems evolve as they accumulate data and constraints; hindsight clarity does not imply past incompetence.

Principles shape worldview and interpretation.

---

## 2. Heuristic
A decision-making lens or rule of thumb.

Example:
> Write as a neutral scribe, not a judge, when documenting regulatory evolution.

Heuristics guide framing and judgment.

---

## 3. Skill
A repeatable procedural behavior.

Example:
> When sending a revised document, include a concise bullet summary of changes.

Skills are actionable and behavior-specific.

---

# Extraction Rules

1. Only extract **generalizable** insights.
2. Do not extract context-specific commentary.
3. Do not invent insight.
4. If no principle, heuristic, or skill exists, explicitly state:

> No generalizable principle, heuristic, or skill identified in this exchange.

5. Avoid over-analysis. If an insight is clearly implied and transferable, extract it cleanly without forcing deeper abstraction.

---

# YAML Frontmatter Schema

Each atomic must begin with:

```yaml
---
id: <ISO-8601 timestamp>
title: "<Descriptive, searchable title>"
type: principle | heuristic | skill
summary: "<One-sentence compressed formulation>"
source_type: email | memo | meeting | chat | document
author_of_source: "<Name if available, otherwise Unknown>"
tags:
  - <ai-generated tag>
  - <ai-generated tag>
  - <ai-generated tag>
created_at: <same ISO-8601 timestamp>
---
```

## Requirements

- `id` must be ISO-8601 timestamp (e.g., 2026-03-03T14:23:51Z)
- `title` must be descriptive and searchable
- `summary` must be one sentence
- `tags` should be meaningful and minimal (avoid jargon stuffing)
- `created_at` must match `id`

---

# Body Structure (Required)

After the frontmatter, use this exact structure:

```
## Core Idea

[Generalizable formulation]

## Why This Matters

[Explain the system logic or reasoning]

## Example From Context

[Grounded example from the source exchange]

## How To Apply

[Actionable guidance or implementation]
```

---

# Tone & Writing Constraints

- Neutral, precise, non-performative.
- Do not moralize.
- Do not flatter.
- Do not judge actors in the source.
- Write like a lab archivist documenting durable insight.
- Avoid unnecessary jargon.
- Avoid artificial neutrality phrasing (no “it is worth noting that” padding).

The atomic should read like a useful internal knowledge artifact, not an essay.

---

# Multiple Atomics

If the exchange clearly contains multiple separable insights, produce multiple atomics.

If insights are intertwined and inseparable, produce one well-structured atomic.

---

# Output Format

Return each atomic as a complete standalone `.md` document.

If multiple atomics are extracted, separate them clearly with:

```
--- ATOMIC 1 ---
<markdown>

--- ATOMIC 2 ---
<markdown>
```

---

# What This Skill Is NOT

- Not a summary tool
- Not a sentiment analysis tool
- Not a rewrite tool
- Not a critique tool

It is a knowledge distillation tool.

---

# Decision Boundary

If unsure whether something is generalizable, ask:

> Would this still make sense if removed entirely from this context and applied elsewhere?

If yes → extract.
If no → do not extract.

---

End of Skill.
