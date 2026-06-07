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
| **Symlink** | Skill is generic and high quality — you'd never need to edit it | `ln -s` | `skill-creator`, `find-skills`, `tdd`, `improve-codebase-architecture` |
| **Copy** | Skill is useful as a starting point but needs project-specific adaptation | `cp -r` then edit | `prep-npc` |
| **Reference** | Skill is tightly coupled to its source project — read it for ideas | Browse on GitHub | `job-scraper`, `ttrpg-wiki-ingest`, `session-ingest` |

> **Current state:** `skill-creator`, `find-skills`, `tdd`, and `improve-codebase-architecture` are symlink-ready.
> Most other skills were built for a specific repo and need adaptation.
> Skills are being generalized over time — check the SKILL.md before assuming portability.

## Skill index

Checked skills are reusable as-is. Unchecked skills were built for a specific
project and need adaptation or are reference-only.

### General / Cross-project

- [x] `skill-creator` — Create, improve, and benchmark skills
- [x] `find-skills` — Discover installable skills
- [x] `tdd` — Test-driven development framework
- [x] `improve-codebase-architecture` — Architecture review and deepening
- [x] `create-agent` — Bootstrap modular AI agents with OpenRouter
- [x] `enforced-in-code` — Code-enforced policy patterns

### Web / Vercel / Backend

- [x] `vercel-react-best-practices` — React/Next.js performance (70 rules)
- [x] `vercel-react-native-skills` — Vercel for React Native
- [x] `deploy-to-vercel` — Vercel deployment workflows
- [x] `web-perf` — Web performance optimization via Chrome DevTools
- [x] `web-design-guidelines` — Web Interface Guidelines compliance
- [x] `ui-ux-pro-max` — UX/UI best practices (50+ styles, 161 palettes)
- [x] `use-dom` — Expo DOM components for web-to-native migration
- [x] `supabase` — Supabase database and auth
- [x] `supabase-postgres-best-practices` — Postgres optimization
- [x] `workers-best-practices` — Cloudflare Workers patterns
- [x] `durable-objects` — Cloudflare Durable Objects
- [x] `wrangler` — Wrangler CLI reference
- [x] `agents-sdk` — Cloudflare Agents SDK
- [x] `sandbox-sdk` — Cloudflare Sandbox SDK

### Mobile / React Native

- [x] `react-native-best-practices` — React Native performance patterns
- [x] `expo-cicd-workflows` — Expo CI/CD with EAS
- [x] `expo-deployment` — Expo app deployment (iOS, Android, web)
- [x] `expo-dev-client` — Expo dev client setup
- [x] `expo-module` — Expo native modules (Swift, Kotlin)
- [x] `expo-observe` — EAS Observe metrics and monitoring
- [x] `expo-tailwind-setup` — Tailwind CSS v4 in Expo
- [x] `expo-api-routes` — Expo Router API routes
- [x] `expo-brownfield` — Brownfield Expo integration
- [x] `expo-ui-swiftui` — SwiftUI views in Expo
- [x] `expo-ui-jetpack-compose` — Jetpack Compose views in Expo
- [x] `building-native-ui` — Native component development
- [x] `native-data-fetching` — Network requests and data fetching
- [x] `add-app-clip` — iOS App Clips
- [x] `upgrading-expo` — Expo SDK version upgrades
- [x] `eas-update-insights` — EAS Update health monitoring

### OpenRouter

- [x] `openrouter-models` — Model selection and pricing reference
- [x] `openrouter-typescript-sdk` — TypeScript SDK usage
- [x] `openrouter-usage` — Usage and cost querying
- [x] `openrouter-image-gen` — Image generation via OpenRouter
- [x] `openrouter-image-edit` — Image editing via OpenRouter

### Obsidian

- [x] `obsidian-markdown` — Obsidian Flavored Markdown reference
- [x] `obsidian-cli` — Obsidian CLI integration
- [x] `obsidian-json-canvas` — JSON canvas support
- [x] `obsidian-bases` — Obsidian Bases database layer

### TTRPG / Campaign

- [x] `ttrpg-llm-wiki-init` — Foundation skill for shattered-sea sessions
- [x] `ttrpg-wiki-ingest` — Ingest source material into the wiki
- [x] `ttrpg-wiki-lint` — Health checks and auto-corrections
- [x] `ttrpg-wiki-organize` — Vault file/folder restructuring
- [x] `ttrpg-wiki-query` — Query and search wiki data
- [x] `ttrpg-writing` — Prose quality for wiki content
- [x] `ttrpg-visual-aids` — Visual aid generation for sessions
- [x] `vault-health` — Vault integrity checks
- [x] `cross-linker` — Add missing cross-references
- [x] `tag-taxonomy` — Controlled tagging vocabulary
- [x] `session-ingest` — Session transcript processing
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
- [x] `roll-dice` — Dice rolling utility

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
