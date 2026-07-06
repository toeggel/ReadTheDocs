---
name: guided-learning
description: 'Guide the user through learning a new technology or topic, scoped to their role and project context. Use when: user says "help me learn X", "I need to understand X for my project", "teach me about X", "I am new to X and need to get up to speed", "explain X from a developer or architect perspective", "I need to ramp up on X". Produces a structured, role-adapted learning session covering concepts, practical usage, and architectural decisions relevant to the user.'
argument-hint: 'Topic + context (e.g. "Kubernetes for a greenfield .NET microservices project, lead developer and architect role")'
---

# Guided Learning

## When to Use
- User needs to learn a technology for an upcoming or current project
- User wants structured, role-relevant learning — not a generic tutorial
- User needs to quickly understand something well enough to make design decisions

## Procedure

### Step 1 — Gather Context

Ask the user (or extract from the argument) the following. Do not proceed without this:

- **Topic**: What do they want to learn?
- **Role**: What is their role on this project? (e.g., lead developer, architect, tech lead, full-stack dev)
- **Project context**: What are they building? What stack/platform?
- **Prior knowledge**: What do they already know about this topic?
- **Urgency**: Is there an immediate decision or deadline?

### Step 2 — Scope the Learning

Based on role and project context, determine:
- What does this person **actually need** to do their job well?
- What can they safely skip or defer?
- What decisions will they personally own?

For a **lead developer + low-level architect** role, prioritize:
- Core architecture and mental model
- Design patterns and structural decisions
- Integration with the rest of the stack
- Configuration tradeoffs that affect code or architecture
- Common mistakes that cause architectural pain later

Deprioritize unless the user owns it:
- Cluster/infrastructure operations and administration (SRE/platform concern)
- Provider-specific operational details
- Control plane internals and deep low-level mechanics
- Deep theory that doesn't change practical design decisions
- Edge cases not relevant to the project type

**Default detail level**: FL100–FL200 (concept + practical usage + tradeoffs) by default.
- FL100: what it is, what problem it solves, when it matters
- FL200: how it works in practice, typical usage, tradeoffs, concrete examples
- FL300: code-level detail, configuration, APIs, debugging — only when needed to implement, debug, or decide
- FL400: deep internals and theory — only if the user explicitly asks

### Step 3 — Present the Learning Path

Propose 4–6 topic areas, ordered from foundational to applied. Confirm with the user before proceeding.

Typical structure:
1. Core mental model (what it is, why it exists, key abstractions)
2. Main building blocks (the concepts/resources you'll use daily)
3. Practical usage patterns (how you'll actually use it in the project)
4. Design decisions (what choices you'll face as lead/architect)
5. Integration with the project stack
6. Pitfalls and common mistakes

Adjust the areas based on the topic and project — this is a starting template, not a fixed list.

### Step 4 — Teach Each Area

For each topic area, use this structure:

**1. Quick answer** — one or two sentences summarizing the concept, no filler

**2. Mental model** — the simplest useful explanation of how it works

**3. What matters for this project** — the parts the user needs to care about given their role and stack

**4. Practical tradeoffs** — short bullets on the main decisions or tensions

**5. Example** — one minimal, concrete example tied to the user's project and stack

**6. Common mistakes** — what teams typically get wrong here

After each area, ask: *"Does this make sense, or should I go deeper on any part before moving on?"*

Adjust depth based on the answer — go deeper when asked, move on when sufficient. For follow-up questions, deepen only the relevant part, not the whole area.

### Step 5 — Synthesize

After all areas, provide:
- The 3–5 key architectural decisions they will face on this project, with recommended defaults
- A suggested first action (what to do or learn next in practice)
- Pointers to go deeper when needed (official docs, key tools, established patterns)

### Step 6 — Capture

Offer to save key learnings as notes using the `write-learn-note` skill:
*"Should I write up a note on any of these topics to use as a future reference?"*

## Teaching Principles

- Lead with **why** before **what** — context before detail
- Use **concrete examples** tied to the user's project and stack
- Highlight **decisions and tradeoffs**, not just facts
- Adjust depth dynamically — go deeper when asked, move on when sufficient
- Stop when the user can make an informed decision — do not over-explain

## Quality Bar

A successful session lets the user say:
- "I understand the concept well enough to work with it"
- "I know what matters for my project"
- "I know what decisions I will face and what the tradeoffs are"
- "I know what to do or learn next"

If any of these are not true, narrow the session further to the user's actual role and project.

## Role Calibration

| Role | Emphasis |
|------|----------|
| Lead developer | Practical usage, code patterns, conventions, integration |
| Low-level architect | System design, tradeoffs, component boundaries, scalability |
| Both (common) | Decision points, design patterns, gotchas with architectural impact |

## Example Flow

**User input:** "Help me learn Kubernetes — I'm building a greenfield .NET microservices project, I'm the lead developer and architect, and I have no prior Kubernetes experience."

1. **Scope**: Focus on workload design, service networking, config/secrets management, Helm packaging. Skip cluster administration and infrastructure provisioning.
2. **Learning path proposed**:
   - Mental model: cluster, node, pod
   - Core resources: Deployment, Service, ConfigMap, Secret
   - Networking and ingress
   - Config packaging with Helm
   - Observability basics (logs, readiness/liveness probes)
3. **Each area** taught with .NET microservice examples (e.g., how a `Deployment` maps to a containerized ASP.NET service)
4. **Key decisions surfaced**: stateless vs. stateful workloads, Ingress controller choice, secrets management strategy, Helm chart structure per service vs. monorepo chart
5. **Offer** to create notes on: Kubernetes mental model, Helm structure, secrets management options
