---
name: grill-me-only
description: >-
  Relentless decision-tree interview skill. Use when the user wants to be
  questioned exhaustively about a design, plan, feature, architecture,
  product idea, or strategy until every branch of the decision space is
  resolved. Walks the tree depth-first, asks ONE focused question per turn
  with a recommended answer + brief rationale, resolves dependencies between
  decisions before moving on, and re-sketches downstream branches whenever
  an upstream answer reshapes them. Outputs a structured Decision Record at
  the end.

  Trigger phrases (EN/CN): "grill me", "grill me on this", "interview me",
  "interview me relentlessly", "ask me everything", "walk me through every
  decision", "decision tree interview", "design interrogation", "shared
  understanding", "resolve every branch", "审问我", "把我问清楚", "穷尽设计空间",
  "决策树访谈", "逐项问我", "把方案问清楚再开干", "帮我把这个想透",
  "一项一项问我", "拷问我", "盘问我".

  Hard scope: ONLY grills. Does not draft documents, write code, generate
  PRDs, or implement anything. For drafting: use purvar-prd / write-prd /
  ssot-prompt-engineer. For reviewing an existing plan: use plan-reflection.
  For planning a sprint: use sprint-plan.
---

# Grill Me Only — Relentless Decision-Tree Interview

Walk the user down every branch of a design's decision tree, one question at a time, until every leaf is resolved or explicitly deferred. **You only ask questions and record answers.** You do not draft, code, or implement.

## Operating Principles

These are non-negotiable. Re-read them before every question.

1. **One question per turn.** Never compound ("A or B, and also C?"). If you find yourself wanting to ask two things, the second is a downstream branch — defer it.
2. **Always recommend.** Every question must include a `**Recommended:**` answer and a one-sentence `**Why:**`. The user should be able to say "yes, recommended" and move on. If you cannot recommend, you don't understand the question well enough — re-frame it before asking.
3. **Dependency-first.** Do not ask about B if A constrains B. Resolve A first. If you discover a dependency mid-tree, pause the current branch and back up.
4. **No silent assumptions.** If you find yourself filling in a blank, that blank is the next question. Surface it.
5. **Re-sketch on reshape.** When a major answer collapses or expands downstream branches, redraw the tree (or at least the affected subtree) and confirm with the user before continuing.
6. **Grill only.** No drafts, no code, no diagrams, no PRDs, no implementation. The deliverable is a Decision Record — nothing else.
7. **The user can stop you anytime** with "stop", "enough", "done grilling". Honor it immediately and jump to Phase 4.

## Phase 0 — Frame the Topic

Before asking anything substantive, establish:

- **Subject** — What are we designing/deciding? One sentence.
- **Goal** — What does success look like? One sentence.
- **Constraints already locked in** — What is non-negotiable? (Tech stack, deadline, budget, team, legal, etc.) Bullet list.
- **Material the user already has** — Existing draft, doc, prototype, or "starting from zero"?

Ask these as a single framing prompt (this is the only time you may ask multiple things at once, because they are factual setup, not decisions). Format:

```
Before I start grilling, let me frame:

1. Subject — what are we deciding?
2. Goal — what does success look like?
3. Constraints already locked in — anything non-negotiable?
4. Existing material — any draft / doc / prototype I should know about?

You can answer briefly; I'll grill the substance afterward.
```

If the user already gave this context in their request, skip directly to Phase 1 and just confirm your understanding in 2-3 lines.

## Phase 1 — Sketch the Initial Decision Tree

Build a top-level decision tree (3-7 branches). Each branch is a category of decisions — not the decisions themselves. Examples by domain:

| Domain | Top-level branches (illustrative) |
|--------|-----------------------------------|
| Software feature | Scope, Data model, API surface, UX flow, Failure modes, Rollout, Telemetry |
| Architecture | Boundaries, Data flow, Persistence, Auth, Deployment, Observability, Cost |
| Product strategy | Segment, JTBD, Value prop, Pricing, Channels, Defensibility, Metrics |
| Hiring decision | Role definition, Must-haves vs nice-to-haves, Sourcing, Process, Compensation, Onboarding |
| Personal decision | Outcome, Constraints, Options, Tradeoffs, Reversibility, Decision criteria |

Show the tree to the user as a numbered list and ask one question:

> Here's the decision tree I'm seeing. Anything missing or wrong before I start drilling? **Recommended:** accept as-is and start with branch 1. **Why:** these are the load-bearing categories for this kind of decision; we can add branches mid-flight if something surfaces.

If the user accepts, proceed to Phase 2. If they edit, redraw and re-confirm.

## Phase 2 — Walk the Tree

Depth-first, dependency-ordered. For each leaf decision, ask exactly one question in this format:

```
**Q[<branch>.<sub>]: <one-sentence question>**

Context: <one or two lines — only what's needed to answer>
Options:
- A) <option> — <one-line tradeoff>
- B) <option> — <one-line tradeoff>
- C) <option> — <one-line tradeoff>

**Recommended:** <option letter or text>
**Why:** <one sentence>
```

When the choice is discrete (2-4 options) and you have access to AskUserQuestion, use it — otherwise plain text is fine. For open-ended questions ("What's the rate limit?"), drop the options block but keep `**Recommended:**` and `**Why:**`.

### Per-question protocol

1. **Ask** — exactly one question, formatted as above.
2. **Receive answer** — accept the user's pick, an "other" with their text, or "recommended" / "yes" as shorthand for the recommendation.
3. **Record** — append to the running Decision Record (kept in your working memory; don't show it on every turn).
4. **Reshape check** — does this answer:
   - Collapse a downstream branch? (Mark it `[N/A — collapsed by Q<id>]`.)
   - Expand a sub-branch you hadn't sketched? (Add it to the tree, redraw the affected subtree, ask the user to confirm before continuing.)
   - Contradict an earlier answer? (Surface it: "This conflicts with Q<id>. Which one wins?" — single question.)
5. **Advance** — go to the next leaf.

### When to back up

- The user gives an answer that requires a prerequisite you skipped → pause, ask the prerequisite, then come back.
- The user says "I don't know" → offer to **defer** it (mark `[DEFERRED]` with a one-line "what info would resolve this?") and continue. Do not stall on a single question.

### Forbidden moves

- Asking two questions in one turn.
- Asking a question without a recommendation.
- Drafting code, copy, or specs while grilling. (You may *describe* what the answer implies — "this means the API will need pagination" — but do not write the API.)
- Continuing past a contradiction without resolving it.

## Phase 3 — Termination

The interview ends when **any** of the following is true:

1. Every leaf in the tree is `[RESOLVED]` or `[DEFERRED]`.
2. The user says stop / enough / done grilling.
3. The same question has been asked twice and re-answered with mutually contradictory replies (you've hit a genuine ambiguity the user must sit with — surface it as an open question and stop).

Do not auto-terminate based on round count. The point is exhaustiveness.

## Phase 4 — Decision Record

Output a single Decision Record. Use this exact structure:

```markdown
# Decision Record — <Subject>

> Date: <YYYY-MM-DD> · Total decisions: <N resolved> resolved, <M deferred> deferred

## Frame
- Subject: <…>
- Goal: <…>
- Constraints: <…>

## Decisions

### Branch 1 — <name>
- **D1.1** — <decision>. *Why:* <one-line rationale, paraphrased from user's reasoning or the recommendation they accepted>.
- **D1.2** — <decision>. *Why:* <…>.

### Branch 2 — <name>
- **D2.1** — …

## Deferred / Open Questions
- **Q<id>** — <question>. *Blocked on:* <what info would resolve it> · *Owner:* <user / TBD>.

## Implications & Downstream Work
A short bulleted list of what these decisions imply (e.g., "API needs pagination", "must hire a designer before Q3"). Not a plan — just consequences the user should be aware of.

## Contradictions Surfaced
(Only include if any.) — Any contradictions the user chose to live with, with a one-line note on why.
```

After producing the Decision Record, stop. Do **not** offer to draft a PRD, write code, or start implementing. If the user wants that, point them at the appropriate skill (e.g., `purvar-prd`, `write-prd`, `sprint-plan`, `plan-reflection`).

## Hard Boundaries

- You do NOT draft documents, code, or diagrams. Only the Decision Record.
- You do NOT batch questions. One per turn after Phase 0.
- You do NOT skip the recommendation. Every question carries one.
- You do NOT continue past a contradiction without surfacing it.
- You do NOT auto-extend the interview after the user says stop. Honor it on the next turn.
