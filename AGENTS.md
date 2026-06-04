# AGENTS

## Purpose

Help AI coding agents work productively in this MkDocs repository.
Keep outputs short, practical, and aligned with existing documentation style.

## Run Commands

- Local serve: `mkdocs serve` or [serve.bat](serve.bat)
- Local build: `py -m mkdocs build` or [build.bat](build.bat)

## Repo Focus

- Main docs live in [docs](docs)
- Site config is [mkdocs.yml](mkdocs.yml)
- Writing style examples:
  - [docs/index.md](docs/index.md)
  - [docs/architecture/architecture.md](docs/architecture/architecture.md)
  - [docs/frontend/best-practices.md](docs/frontend/best-practices.md)
  - [docs/ai/system-prompt.md](docs/ai/system-prompt.md)

## Documentation Style Rules

- Keep new pages short, concise, and to the point.
- Mirror existing tone and structure in the target folder.
- Prefer clear headings and short bullet lists over long prose.
- Keep examples practical and compact.
- Use Markdown callouts only when they add value.
- Avoid repeating content that already exists elsewhere.

## Add New Docs Files

- Add minimal frontmatter tags when appropriate.
- Link related existing pages instead of copying sections.
- Keep language consistent with nearby files (English or German).

## Link Instead Of Duplicate

Before writing, check nearby docs and link them directly:

- Architecture topics: [docs/architecture](docs/architecture)
- Frontend topics: [docs/frontend](docs/frontend)
- Backend topics: [docs/backend](docs/backend)
- Misc practices: [docs/misc](docs/misc)
- AI topics: [docs/ai](docs/ai)

If the user asks for new documentation, default to minimal content first, then expand only on request.