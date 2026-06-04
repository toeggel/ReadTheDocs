---
tags:
  - ai
  - workflow
---

# AI Workflows

Practical guide: what to use, why, tradeoffs, and a minimal setup.

## Quick Decision

- One-off task -> Prompt
- Repeatable behavior rule -> Instruction
- Repeatable task flow -> Skill
- Multi-step execution -> Agent
- External system/tool access -> MCP
- Fast shell/devops flow -> CLI

## Topics

### Prompt

- Best for: One request
- Benefit: Fast and flexible
- Drawback: Quality depends on context quality

### Instructions

- Best for: Team conventions
- Benefit: Consistent outputs across sessions
- Drawback: Can become noisy if too broad

### Skills

- Best for: Repeatable workflows
- Benefit: Reusable, structured execution
- Drawback: Upfront design effort

globally installed skills are located here: `%USERPROFILE%\.agents\skills` or `%USERPROFILE%\.copilot\skills`

### Agents

- Best for: Complex multi-step tasks
- Benefit: Better planning and autonomy
- Drawback: More setup and maintenance

### MCP

- Best for: External tools and APIs
- Benefit: Real data and integrations
- Drawback: Security and ops overhead

## Loading Behavior

- Instructions are not automatically loaded in every case.
- Broad instructions can be loaded very often, for example global instructions or wide `applyTo` patterns.
- Narrow instruction files are only useful if they match the current task.
- Skills are usually loaded on demand, not on every request.
- Result: put stable behavior rules in instructions, but put heavier workflows into skills or agents.

## Minimal Setup

1. Add global behavior rules in AGENTS.md or .github/copilot-instructions.md.
2. Add domain instructions for focused areas (api, security, docs).
3. Add one prompt for recurring asks (for example: "draft ADR", "review API").
4. Add one skill for a common workflow (for example: "create concise doc page").
5. Add one agent when task orchestration becomes repetitive.

Example structure:

```text
.github/
  copilot-instructions.md
  instructions/
    docs.instructions.md
    api.instructions.md
  prompts/
    write-short-doc.prompt.md
  skills/
    create-doc-page/SKILL.md
  agents/
    docs-editor.agent.md
AGENTS.md
```

## Concrete Usage

- Prompt: "Summarize this page in 5 bullets with 1 action per bullet."
- Instruction: "For docs pages: short headings, short bullets, avoid duplicate content."
- Skill: "When asked to create docs, first link related pages, then draft minimal page."
- Agent: "Investigate, propose options, apply edits, run checks, report risks."

## Token Optimization

- Keep instructions short. Long global instructions cost tokens on many requests.
- Avoid `applyTo: "**"` unless the rule really applies everywhere.
- Split rules by area: docs, backend, frontend, security.
- Link to existing docs instead of embedding the same guidance again.
- Prefer small prompts with good context over large generic prompts.
- Use skills for larger workflows so the details are loaded only when needed.
- Remove stale instructions. Old rules create noise and contradictions.

Good for tokens:

- "Write a short page in the style of `docs/frontend/best-practices.md`."

Bad for tokens:

- Large prompt + copied style guide + copied examples + repeated repo rules

## Typical Workflow

1. Start with a prompt and success criteria.
2. Promote repeated guidance into instructions.
3. Promote repeated process into a skill.
4. Promote repeated orchestration into an agent.
5. Add MCP only if local context is not enough.

## Best Practices

- Keep each instruction file narrow in scope.
- Prefer links to existing docs over copied text.
- Treat skills as small building blocks.
- Keep agents focused on one workflow outcome.
- Review AI output before merge or publish.

## Related

- [AI overview](index.md)
- [System prompt basics](system-prompt.md)
- [Examples](examples)
