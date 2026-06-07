# Agent Skills

A centralized library of Claude Code skills, hooks, and subagents. Other projects
in ai-os (and beyond) can pull from this repo to bootstrap their own `.claude/`
setup — either using skills directly or copying them as starting points.

## How to use skills from this repo

### Use as-is (symlink)

High-quality, project-agnostic skills can be symlinked directly into a project.
Updates to the source propagate automatically — no re-copying needed.

```bash
ln -s /path/to/agent-skills/skill-creator my-project/.claude/skills/skill-creator
ln -s /path/to/agent-skills/find-skills   my-project/.claude/skills/find-skills
```

### Copy and adapt

Most skills in this repo were built for a specific project (shattered-sea, nextturn,
ai-job-search) and contain project-specific references, paths, or conventions.
Copy them into your project and modify to fit:

```bash
cp -r agent-skills/tdd my-project/.claude/skills/tdd
# then edit SKILL.md to match your project's test setup
```

### Which approach to use

| Tier | When | How | Examples |
|---|---|---|---|
| **Symlink** | Skill is generic and high quality — you'd never need to edit it | `ln -s` | `skill-creator`, `find-skills` |
| **Copy** | Skill is useful as a starting point but needs project-specific adaptation | `cp -r` then edit | `tdd`, `improve-codebase-architecture`, `prep-npc` |
| **Reference** | Skill is tightly coupled to its source project — read it for ideas | Browse on GitHub | `job-scraper`, `ttrpg-wiki-ingest`, `session-ingest` |

> **Current state:** `skill-creator` and `find-skills` are the gold-standard
> portable skills. Almost everything else was built for a specific repo and will
> need adaptation. Skills are being generalized over time — check the SKILL.md
> before assuming portability.

## What's here

**85 skills** across six domains, plus **9 hooks** and **4 subagents**.

| Domain | Count | Examples |
|---|---|---|
| TTRPG / Campaign | 31 | `prep-npc`, `session-ingest`, `ttrpg-wiki-lint` |
| Mobile / React Native | 16 | `expo-deployment`, `react-native-best-practices` |
| Web / Backend | 16 | `vercel-react-best-practices`, `supabase`, `workers-best-practices` |
| Obsidian / OpenRouter | 9 | `obsidian-markdown`, `openrouter-models` |
| Job Search | 3 | `job-application-assistant`, `job-scraper`, `upskill` |
| General | 10 | `tdd`, `skill-creator`, `find-skills` |

See [CLAUDE.md](CLAUDE.md) for the full index with descriptions.

### Hooks (`hooks/`)

Shell scripts that fire on Claude Code tool events (`PreToolUse` / `PostToolUse`).
Covers Python formatting/linting, TypeScript formatting, env/lockfile guards, and
wiki-specific automation (frontmatter, wikilink checks, index regen).

See [hooks/README.md](hooks/README.md) for wiring instructions.

### Subagents (`agents/`)

Specialist agent definitions dispatched via the `Agent` tool for focused subtasks:
wiki content review, lore consistency checking, TypeScript type checking, and
Gemini-backed research.

See [agents/README.md](agents/README.md) for details.

## Skill structure

Each skill is a directory containing a `SKILL.md` (loaded by Claude Code) and
optionally supporting files the skill reads at runtime:

```
skill-creator/          # complex skill with bundled tooling
├── SKILL.md
├── agents/
├── scripts/
├── eval-viewer/
└── references/

tdd/                    # skill with reference docs
├── SKILL.md
├── deep-modules.md
├── interface-design.md
├── mocking.md
├── refactoring.md
└── tests.md

roll-dice/              # minimal skill
├── SKILL.md
└── roll.sh
```

## For consuming projects

Add a note to your project's CLAUDE.md pointing here:

```markdown
## Shared skills

The [agent-skills](https://github.com/Thedougler/agent-skills) repo contains
reusable Claude Code skills. To install one:

    ln -s /path/to/agent-skills/<skill> .claude/skills/<skill>   # use as-is
    cp -r /path/to/agent-skills/<skill> .claude/skills/<skill>   # copy and adapt
```

## Keeping up to date

```bash
# Pull latest skills
git -C /path/to/agent-skills pull

# Symlinked skills update automatically.
# Copied skills need manual re-copy if you want upstream changes.
```

## Sources

Skills were consolidated from three projects:

- **shattered-sea** — D&D 5e campaign wiki and TTRPG tooling
- **nextturn** — Full-stack AI life coach app (React/Expo/Cloudflare)
- **ai-job-search** — Job application automation framework
