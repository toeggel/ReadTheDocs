---
name: write-learn-note
description: 'Write a concise, practical knowledge note from something the user learned. Use when: user says "write a note about X", "capture my learnings on X", "TIL about X", "document what I learned", "create a learn note", "summarize this topic for future reference". Produces a short, reusable reference note for a software developer or close-to-code architect.'
argument-hint: 'Topic or thing learned (e.g. "Redis eviction policies", "k6 load testing setup")'
---

# Write Learn Note

## When to Use
- User says "write a note about X", "capture what I learned about X", or "TIL X"
- User shares something they just learned and wants to preserve it
- User wants a topic summarized as a future reference, not a deep-dive tutorial

## Procedure

1. **Identify the topic** — extract it from the user's message or arguments
2. **Clarify if needed** — if the topic is vague, ask:
   - What exactly did you learn? (implementation detail, design concept, tradeoff?)
   - Are you writing this to use it, debug it, or decide between options?
   - What level of detail? (overview / practical how-to / code-level)
3. **Choose detail level** — default to **practical** unless the user specifies otherwise:
   - *Overview*: what it is, why it exists, when to use it
   - *Practical* (default): behavior, common usage, tradeoffs, concrete example
   - *Code-level*: APIs, config, debugging, edge cases — only when needed to implement, debug, or decide
4. **Write the note** using the Output Format below
5. **Save the note** to `Learn/` in the workspace, or ask the user for the preferred location

## Target Reader

Write for a **software developer / close-to-code architect** who:
- makes implementation and design decisions
- may also act as tech lead or architect
- is **not** primarily a platform, DevOps, or SRE specialist

Exclude platform/infra detail unless it directly affects code or architecture.

## Output Format

Use this markdown structure:

### Summary
One or two sentences describing the topic.

### Why it matters
Short bullets about the practical impact.

### How it works in practice
Short bullets with the minimum useful detail.

### Example
One minimal, realistic example (code or config if relevant).

### Gotchas
Short list of common pitfalls or mistakes.

### Rule of thumb
One sentence capturing the practical takeaway.

## Writing Guidelines

- Prefer bullets over paragraphs
- Prefer concrete examples over abstract explanation
- No textbook background, historical context, or filler
- For each detail, ask: does this help the reader **use it**, **debug it**, **choose between options**, or **explain it**? If no — omit it

## Quality Check

Before finalizing, verify the note:
- [ ] Short and specific
- [ ] Matches target reader role
- [ ] Contains at least one concrete example
- [ ] Free of filler and irrelevant background
- [ ] Feels like "what I need next time I touch this" — not "everything there is to know"



