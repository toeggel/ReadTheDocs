---
tags:
  - ai
---

# AI

Context is king! 💩 In -> 💩 Out
Different Model have different outcome -> try out

## Prompting

Pillars
- Context 
	- Is King
- Intent
- Clarity
- Specific

## Copilot Setup

- .github/
	- copilot-instructions.md
	- instructions/
		- frontend.instructions.md // [frontend.instructions](examples/copilot-setup/frontend.instructions.md)
		- testing.instructions.md
	- prompts/
		- codequality.prompt.md
		- \*.prompt.md // [api.prompt](examples/copilot-setup/api.prompt.md)
	- agents/
		- \*.agent.md // [architect.agent](examples/copilot-setup/architect.agent.md)
- AGENTS.md // general agents instructions
We can call prompts in the chat window by using `/codequlaity check for this`
or using agents by selecting our custom agents

###  Image

We can work with images in copilot e.g. ask about hand drawn images or convert them to mermaid diagrams.

##  Best Practices

- Session splitting / small context
- Right context over more context
- Modular and custom rules instruction files