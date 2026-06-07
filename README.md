# Agent Skills

A centralized library of Claude Code skills consolidated from multiple projects. Skills cover TTRPG campaign tooling, web/mobile development, job search automation, and general-purpose workflows.

## What's here

85 skills across 6 categories:

| Category | Count | Examples |
|---|---|---|
| TTRPG / Campaign | 31 | `prep-npc`, `session-ingest`, `ttrpg-wiki-lint` |
| Mobile / React Native | 16 | `expo-deployment`, `react-native-best-practices` |
| Web / Backend | 16 | `vercel-react-best-practices`, `supabase`, `workers-best-practices` |
| Obsidian / OpenRouter | 9 | `obsidian-markdown`, `openrouter-models` |
| Job Search | 3 | `job-application-assistant`, `job-scraper`, `upskill` |
| General | 10 | `tdd`, `skill-creator`, `find-skills` |

See [CLAUDE.md](CLAUDE.md) for the full index with descriptions.

## Usage

**Clone:**
```bash
git clone https://github.com/Thedougler/agent-skills.git
```

**Install a single skill into a project:**
```bash
cp -r agent-skills/tdd my-project/.claude/skills/
```

**Install all skills:**
```bash
cp -r agent-skills/*/ my-project/.claude/skills/
```

**Update:**
```bash
git -C agent-skills pull
```

## Skill structure

Each skill is a directory containing a `SKILL.md` (the skill definition loaded by Claude Code) and optionally a `references/` subdirectory with supporting documentation the skill reads at runtime.

```
tdd/
├── SKILL.md
├── deep-modules.md
├── interface-design.md
├── mocking.md
├── refactoring.md
└── tests.md
```

## Sources

Skills were consolidated from three projects:

- `shattered-sea` — D&D 5e campaign wiki and TTRPG tooling
- `nextturn` — Full-stack AI life coach app (React/Expo/Cloudflare)
- `ai-job-search` — Job application automation framework
