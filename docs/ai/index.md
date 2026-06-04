---
tags:
  - ai
---

# AI

Context is king! 💩 In -> 💩 Out
Different Model have different outcome -> try out

## Workflows

See [AI Workflows](workflows.md) for a short, practical guide.

## Prompting

Pillars

- Context 
	- Is King
- Intent
- Clarity
- Specific

## Copilot Setup

```markdown
.
├─ .github/
│  ├─ copilot-instructions.md
│  ├─ instructions/
│  │  ├─ *.instructions.md
│  ├─ prompts/
│  │  └─ *.prompt.md
│  └─ agents/
│     └─ *.agent.md
└─ AGENTS.md
```
See [examples](examples) for examples.

We can call prompts in the chat window by using `/codequality check for this`
or using agents by selecting our custom agents

###  Image

We can work with images in copilot e.g. ask about hand drawn images or convert them to mermaid diagrams.

##  Best Practices

- Session splitting / small context
- Right context over more context
- Modular and custom rules instruction files
