# Agents (Subagents)

Markdown files that define Claude Code subagents — specialist agents spawned by the
main agent via the `Agent` tool to handle focused subtasks without polluting the main
context window.

## Agent inventory

| File | Model | Source | Purpose |
|---|---|---|---|
| `content-quality-reviewer.md` | sonnet | shattered-sea | Reviews wiki content against sandbox rules and frontmatter standards |
| `lore-consistency-checker.md` | sonnet | shattered-sea | Cross-references entity claims across vault files for contradictions |
| `ts-typecheck.md` | haiku | shattered-sea | Runs `pnpm typecheck` and reports TS errors — fast, cheap pass before UI builds |
| `gemini-research-expert.md` | sonnet | ai-job-search | Executes research via `gemini -p "..."` CLI and synthesizes findings |

## File format

Each file uses YAML frontmatter followed by a system prompt:

```markdown
---
name: my-agent
description: One-line description shown when selecting agents
model: sonnet   # haiku | sonnet | opus
---

System prompt content here...
```

The `description` field is what Claude uses to decide when to dispatch this agent.
Write it as a clear trigger condition, not a capability statement.

## Installation

Copy the agent file into your project's `.claude/agents/`:
```bash
cp agent-skills/agents/ts-typecheck.md my-project/.claude/agents/
```

Claude Code discovers agents automatically from that directory — no settings.json
wiring required.

## Notes

- **`ts-typecheck.md`** contains a hardcoded absolute path (`/Users/nick/ai-os/shattered-sea`).
  Update the `pnpm typecheck` working directory to match your project before use.
- **`content-quality-reviewer.md`** and **`lore-consistency-checker.md`** encode
  shattered-sea-specific rules (sandbox rules, frontmatter schema). Adapt or replace
  the rules section for other wikis.
- **`gemini-research-expert.md`** requires the `gemini` CLI to be installed and
  authenticated (`gemini` from Google's SDK). It is project-agnostic.
