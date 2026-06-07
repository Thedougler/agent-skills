# Agent Skills

Centralized skill library for all `ai-os` subprojects. Skills live at
[github.com/Thedougler/agent-skills](https://github.com/Thedougler/agent-skills).

Skills marked with `*` were present identically in multiple projects — only one copy is kept here.

## Installing skills into a project

**Clone the repo (first time):**
```bash
git clone https://github.com/Thedougler/agent-skills.git
```

**Pull a single skill into a project:**
```bash
# From the agent-skills repo root
cp -r <skill-name> /path/to/project/.claude/skills/

# Example
cp -r tdd ../shattered-sea/.claude/skills/
```

**Pull all skills at once:**
```bash
cp -r */ /path/to/project/.claude/skills/
```

**Keep skills up to date:**
```bash
git -C /path/to/agent-skills pull
```

## Git

After any change to this repo, commit and push to `Thedougler/agent-skills` (main) as the final step of every operation. Use the `gh` CLI for all GitHub operations (PRs, issues, checks): `gh pr create`, `gh issue list`, `gh run list`, etc.

## Source projects

| Prefix / Group | Source project |
|---|---|
| `ttrpg-*`, `prep-*`, `session-*`, `vault-*`, `obsidian-*`, `live-*`, `sandbox-narrative`, `tag-taxonomy`, `ttrpg-writing`, `world-update`, `pc-combat-primer`, `cross-linker`, `roll-dice`, `daily-update` | `shattered-sea` |
| `expo-*`, `react-native-*`, `vercel-*`, `supabase*`, `openrouter-*` (models/ts-sdk/usage), `web-*`, `ui-ux-pro-max`, `agents-sdk`, `sandbox-sdk`, `durable-objects`, `workers-best-practices`, `wrangler`, `deploy-to-vercel`, `native-data-fetching`, `building-native-ui`, `add-app-clip`, `upgrading-expo`, `eas-update-insights`, `use-dom`, `create-agent`, `find-skills`, `new-wiki-entry`, `improve-codebase-architecture`, `db-reset` | `nextturn` |
| `job-application-assistant`, `job-scraper`, `upskill` | `ai-job-search` |
| `tdd` * | `shattered-sea` + `nextturn` (identical) |
| `skill-creator` * | `shattered-sea` + `nextturn` (identical) |
| `cli-improvement`, `continuous-self-improvement`, `enforced-in-code`, `organize`, `openrouter-image-gen`, `openrouter-image-edit`, `player-view-dev`, `live-transcription-workspace` | `shattered-sea` |

## All skills

### TTRPG / Campaign (shattered-sea)

| Skill | Purpose |
|---|---|
| `ttrpg-llm-wiki-init` | Foundation skill — run first in every shattered-sea session |
| `ttrpg-wiki-ingest` | Ingest source material into the wiki |
| `ttrpg-wiki-lint` | Health checks, auto-corrections, snapshot diffing |
| `ttrpg-wiki-organize` | Reorganize and structure vault content |
| `ttrpg-wiki-query` | Query and search wiki data |
| `ttrpg-writing` | Prose quality for wiki content (DM and player-facing) |
| `ttrpg-visual-aids` | Generate visual aids for sessions |
| `vault-health` | Vault integrity checks |
| `cross-linker` | Add missing cross-references between pages |
| `tag-taxonomy` | Enforce controlled tagging vocabulary |
| `session-ingest` | Multi-pass session transcript processing |
| `session-recap` | Summarize sessions |
| `world-update` | Update campaign world state |
| `prep-session` | Session prep |
| `prep-encounter` | Encounter design and calibration |
| `prep-npc` | NPC creation and expansion |
| `prep-creature` | Creature/monster stat blocks |
| `prep-dungeon` | Dungeon and adventure site design |
| `prep-ship` | Ship creation |
| `prep-island` | Island creation |
| `prep-location` | Location prep |
| `prep-faction` | Faction prep |
| `prep-situation` | Situation prep |
| `prep-hb-item` | Homebrew item creation |
| `pc-combat-primer` | PC combat profiles and encounter calibration |
| `sandbox-narrative` | Narrative generation for sandbox play |
| `live-co-dm` | Live co-DM with voice profiling |
| `live-transcription` | Session audio transcription with speaker ID |
| `live-transcription-workspace` | Workspace for live transcription |
| `roll-dice` | Dice rolling utility |
| `daily-update` | Daily vault updates |

### Obsidian

| Skill | Purpose |
|---|---|
| `obsidian-markdown` | Obsidian markdown conventions |
| `obsidian-cli` | Obsidian CLI integration |
| `obsidian-json-canvas` | JSON canvas support |
| `obsidian-bases` | Obsidian Bases integration |

### OpenRouter

| Skill | Purpose |
|---|---|
| `openrouter-models` | Model selection reference |
| `openrouter-typescript-sdk` | TypeScript SDK usage |
| `openrouter-usage` | Usage patterns |
| `openrouter-image-gen` | Image generation via OpenRouter |
| `openrouter-image-edit` | Image editing via OpenRouter |

### Web / Vercel / Backend (nextturn)

| Skill | Purpose |
|---|---|
| `vercel-react-best-practices` | React/Next.js performance (70 rules) |
| `vercel-react-native-skills` | Vercel for React Native |
| `deploy-to-vercel` | Vercel deployment workflows |
| `web-perf` | Web performance optimization |
| `web-design-guidelines` | Design system guidance |
| `ui-ux-pro-max` | UX/UI best practices |
| `use-dom` | DOM manipulation patterns |
| `supabase` | Supabase database and auth |
| `supabase-postgres-best-practices` | Postgres optimization |
| `workers-best-practices` | Cloudflare Workers patterns |
| `durable-objects` | Cloudflare Durable Objects |
| `wrangler` | Wrangler CLI |
| `agents-sdk` | Bootstrap AI agents with OpenRouter |
| `sandbox-sdk` | Sandbox environment SDK |
| `improve-codebase-architecture` | Architecture review |
| `db-reset` | Database reset utilities |

### Mobile / React Native (nextturn)

| Skill | Purpose |
|---|---|
| `react-native-best-practices` | React Native patterns |
| `expo-cicd-workflows` | Expo CI/CD |
| `expo-deployment` | Expo deployment |
| `expo-dev-client` | Expo dev client setup |
| `expo-module` | Expo native modules |
| `expo-observe` | Expo observability |
| `expo-tailwind-setup` | Tailwind in Expo |
| `expo-api-routes` | Expo API routes |
| `expo-brownfield` | Brownfield Expo integration |
| `expo-ui-swiftui` | SwiftUI native UI integration |
| `expo-ui-jetpack-compose` | Jetpack Compose native UI integration |
| `building-native-ui` | Native component development |
| `native-data-fetching` | Native data fetching patterns |
| `add-app-clip` | iOS App Clips |
| `upgrading-expo` | Expo version upgrades |
| `eas-update-insights` | EAS Update insights |

### Job Search (ai-job-search)

| Skill | Purpose |
|---|---|
| `job-application-assistant` | Fit eval, CV/cover-letter drafting, interview prep |
| `job-scraper` | Scrape Canadian job boards, deduplicate across runs |
| `upskill` | Identify skill gaps from job postings |

### General / Cross-project

| Skill | Purpose |
|---|---|
| `tdd` | Test-driven development framework |
| `skill-creator` | Create, improve, and benchmark skills |
| `find-skills` | Discover installable skills |
| `create-agent` | Bootstrap modular AI agents |
| `new-wiki-entry` | Wiki entry management |
| `cli-improvement` | CLI enhancement patterns |
| `continuous-self-improvement` | Self-optimization loop |
| `enforced-in-code` | Code-enforced policy patterns |
| `organize` | General content organization |
| `player-view-dev` | Player-view development tooling |
