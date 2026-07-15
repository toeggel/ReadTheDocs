# GitHub Copilot Fundamentals

Encode what is always true in **instructions**, what is reusable and triggerable in **skills**, and what needs a dedicated persona or tool set in an **agent** - then let subagents handle anything that benefits from parallel or isolated execution.

## Summary

GitHub Copilot's customization model is built on three primitives - **Instructions**, **Skills**, and **Agents** - layered on top of a context-window system that you can explicitly shape. Mastering these lets you move from reactive chat to orchestrated, repeatable agentic workflows.

## Why it matters

- Default Copilot behavior is generic; the primitives let you encode your team's conventions, tooling, and workflows so they apply automatically.
- Understanding context prioritization tells you *why* suggestions miss and how to fix it fast.
- Subagent orchestration unlocks parallel or decomposed work that would overwhelm a single chat thread.

## How it works in practice

### The three primitives (layered)

- **Instructions** (`*.instructions.md`) - persistent background context scoped by glob pattern. Use for coding standards, architecture rules, and compliance guardrails. Applied automatically; no user action required.
- **Skills** (folder + `SKILL.md`) - reusable, bundled capabilities invokable via `/command` or auto-discovered by agents. Can include templates, scripts, and reference files. Supersede the older `*.prompt.md` pattern.
- **Agents** (`*.agent.md`) - opinionated personas that combine tools, MCP servers, and instructions. Use for specialist workflows (e.g., "Terraform Expert", "Security Reviewer") or as coordinators that delegate to subagents.

### Context — what Copilot sees and how it's prioritized

1. Code surrounding the cursor
2. Explicitly `#`-referenced files (VS Code) or `@`-mentioned files (CLI)
3. Recently modified files
4. Files directly imported by the current file

> Copilot does **not** scan the full repo by default. Use `#codebase` in chat to force a repo-wide search.

### Subagents — when and how

- A *subagent* is a temporary worker launched by the main agent for context isolation, specialization, or parallelism.
- Main agent = project lead (persists, talks to user). Subagent = focused contributor (temporary, reports back).
- In VS Code: enable the `agent` tool in frontmatter; use an `agents:` allowlist to control which workers the coordinator can call.
- In Copilot CLI: use `/fleet` to decompose a task into parallel background subagents automatically.
- Recursive subagent spawning is off by default (`chat.subagents.allowInvocationsFromSubagents`).

## Example

### Coordinator + worker agent (VS Code frontmatter)

```yaml
---
name: Feature Builder
tools: ['agent', 'read', 'search', 'edit']
agents: ['Planner', 'Implementer', 'Reviewer']
---
```

```yaml
---
name: Planner
user-invocable: false
tools: ['read', 'search']
---
```

### Scoped instruction file

```markdown
---
applyTo: "src/**"
---
# Coding standards
- Open braces on the same line.
- No implicit usings.
```

### CLI fleet invocation

```text
/fleet Update auth docs, refactor auth service, and add related tests.
```

## Gotchas

- Closing a file removes it from Copilot's active context - keep related files open while working.
- `handoffs` and `argument-hint` frontmatter work in VS Code but are **ignored** on GitHub.com cloud agents - don't assume portability.
- Skills replace prompt files; avoid investing in new `*.prompt.md` files.
- Subagents share the same filesystem - overlapping file writes across parallel agents cause conflicts.
- `user-invocable: false` hides an agent from the picker but still allows coordinator delegation; `disable-model-invocation: true` prevents delegation too.
