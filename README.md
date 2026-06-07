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

## Skill index

Checked skills are reusable as-is. Unchecked skills were built for a specific
project and need adaptation or are reference-only.

### General / Cross-project

- [x] `skill-creator` — Create, improve, and benchmark skills
- [x] `find-skills` — Discover installable skills
- [ ] `tdd` — Test-driven development framework
- [ ] `improve-codebase-architecture` — Architecture review and deepening
- [ ] `create-agent` — Bootstrap modular AI agents with OpenRouter
- [ ] `enforced-in-code` — Code-enforced policy patterns

### Web / Vercel / Backend

- [ ] `vercel-react-best-practices` — React/Next.js performance (70 rules)
- [ ] `vercel-react-native-skills` — Vercel for React Native
- [ ] `deploy-to-vercel` — Vercel deployment workflows
- [ ] `web-perf` — Web performance optimization via Chrome DevTools
- [ ] `web-design-guidelines` — Web Interface Guidelines compliance
- [ ] `ui-ux-pro-max` — UX/UI best practices (50+ styles, 161 palettes)
- [ ] `use-dom` — Expo DOM components for web-to-native migration
- [ ] `supabase` — Supabase database and auth
- [ ] `supabase-postgres-best-practices` — Postgres optimization
- [ ] `workers-best-practices` — Cloudflare Workers patterns
- [ ] `durable-objects` — Cloudflare Durable Objects
- [ ] `wrangler` — Wrangler CLI reference
- [ ] `agents-sdk` — Cloudflare Agents SDK
- [ ] `sandbox-sdk` — Cloudflare Sandbox SDK

### Mobile / React Native

- [ ] `react-native-best-practices` — React Native performance patterns
- [ ] `expo-cicd-workflows` — Expo CI/CD with EAS
- [ ] `expo-deployment` — Expo app deployment (iOS, Android, web)
- [ ] `expo-dev-client` — Expo dev client setup
- [ ] `expo-module` — Expo native modules (Swift, Kotlin)
- [ ] `expo-observe` — EAS Observe metrics and monitoring
- [ ] `expo-tailwind-setup` — Tailwind CSS v4 in Expo
- [ ] `expo-api-routes` — Expo Router API routes
- [ ] `expo-brownfield` — Brownfield Expo integration
- [ ] `expo-ui-swiftui` — SwiftUI views in Expo
- [ ] `expo-ui-jetpack-compose` — Jetpack Compose views in Expo
- [ ] `building-native-ui` — Native component development
- [ ] `native-data-fetching` — Network requests and data fetching
- [ ] `add-app-clip` — iOS App Clips
- [ ] `upgrading-expo` — Expo SDK version upgrades
- [ ] `eas-update-insights` — EAS Update health monitoring

### OpenRouter

- [ ] `openrouter-models` — Model selection and pricing reference
- [ ] `openrouter-typescript-sdk` — TypeScript SDK usage
- [ ] `openrouter-usage` — Usage and cost querying
- [ ] `openrouter-image-gen` — Image generation via OpenRouter
- [ ] `openrouter-image-edit` — Image editing via OpenRouter

### Obsidian

- [ ] `obsidian-markdown` — Obsidian Flavored Markdown reference
- [ ] `obsidian-cli` — Obsidian CLI integration
- [ ] `obsidian-json-canvas` — JSON canvas support
- [ ] `obsidian-bases` — Obsidian Bases database layer

### TTRPG / Campaign

- [ ] `ttrpg-llm-wiki-init` — Foundation skill for shattered-sea sessions
- [ ] `ttrpg-wiki-ingest` — Ingest source material into the wiki
- [ ] `ttrpg-wiki-lint` — Health checks and auto-corrections
- [ ] `ttrpg-wiki-organize` — Vault file/folder restructuring
- [ ] `ttrpg-wiki-query` — Query and search wiki data
- [ ] `ttrpg-writing` — Prose quality for wiki content
- [ ] `ttrpg-visual-aids` — Visual aid generation for sessions
- [ ] `vault-health` — Vault integrity checks
- [ ] `cross-linker` — Add missing cross-references
- [ ] `tag-taxonomy` — Controlled tagging vocabulary
- [ ] `session-ingest` — Session transcript processing
- [ ] `session-recap` — Session summaries
- [ ] `world-update` — Campaign world state updates
- [ ] `prep-session` — Session prep
- [ ] `prep-encounter` — Encounter design and calibration
- [ ] `prep-npc` — NPC creation and expansion
- [ ] `prep-creature` — Creature/monster stat blocks
- [ ] `prep-dungeon` — Dungeon and adventure site design
- [ ] `prep-ship` — Ship creation
- [ ] `prep-island` — Island creation
- [ ] `prep-location` — Location prep
- [ ] `prep-faction` — Faction prep
- [ ] `prep-situation` — Situation prep
- [ ] `prep-hb-item` — Homebrew item creation
- [ ] `pc-combat-primer` — PC combat profiles
- [ ] `sandbox-narrative` — Sandbox narrative generation
- [ ] `live-co-dm` — Live co-DM with voice profiling
- [ ] `live-transcription` — Session audio transcription
- [ ] `roll-dice` — Dice rolling utility

### Job Search

- [ ] `job-application-assistant` — Fit eval, CV/cover-letter drafting, interview prep
- [ ] `job-scraper` — Scrape Canadian job boards, deduplicate across runs
- [ ] `upskill` — Identify skill gaps from job postings

## Hooks (`hooks/`)

Shell scripts that fire on Claude Code tool events (`PreToolUse` / `PostToolUse`).
Covers Python formatting/linting, TypeScript formatting, env/lockfile guards, and
wiki-specific automation (frontmatter, wikilink checks, index regen).

See [hooks/README.md](hooks/README.md) for wiring instructions.

## Subagents (`agents/`)

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
