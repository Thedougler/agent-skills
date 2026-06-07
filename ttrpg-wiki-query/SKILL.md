---
name: ttrpg-wiki-query
metadata:
  version: "1.0"
description: >
  The mandatory default method for finding anything in the campaign wiki. Use
  this ANY time you need in-world information — whether the user explicitly asks you
  to look something up, or you need context before answering, prepping, or writing.
  Invoke it BEFORE asserting, inventing, or assuming any campaign fact: NPCs,
  locations, ships, factions, creatures and stat blocks, items, deities, lore,
  situations, session history, the party, or current world state. Trigger on phrases
  like "look up", "what do we know about", "is there a page for", "find the entry
  for", "does the wiki say", "search the wiki", "what's the current state of", "who
  is", "where is", "what happened with". Also trigger silently whenever you would
  otherwise guess a campaign detail — if you are not certain something is established
  canon, search first. Every other TTRPG skill defers to this one for lookups.
  Uses a tiered search (in-context index/hot → frontmatter/keyword → semantic search):
  fast on easy lookups, comprehensive on hard ones.
---

# TTRPG Wiki Query

**This is how you find things. Use it before you state anything.**

The campaign wiki may have hundreds of pages and you carry almost none of them in context. The
single worst failure mode in a sandbox wiki is **confidently inventing a fact that
contradicts established canon** — a renamed NPC, a ship that sank two sessions ago, a
faction that wants the opposite of what you said. This skill exists to make that
failure impossible: when a campaign fact matters, you retrieve it instead of guessing.

Two non-negotiables:

1. **Never assert an in-world fact you have not found in a wiki page** (or confirmed is
   genuinely absent). If you can't find it, say so — don't fill the gap with invention.
2. **Gather *complete* context, not the first hit.** A page rarely stands alone. The
   NPC links to a faction, a situation, a location, a session. Incomplete context
   produces answers that are locally right and globally wrong.

---

## The tiered method

Climb the tiers in order. **Stop the moment you have a confident, complete answer** —
most lookups never reach Tier 3. Each tier is more powerful and more expensive than the
last, so paying for Tier 3 on a question Tier 1 already answered just wastes time.

### Tier 1 — What you already have (free)

`<wiki>/index.md` and `<wiki>/hot.md` (or your project's equivalent files) are cheap and often already in context.

- **`index.md`** is the master catalog — every page, by path, with its one-line summary.
  Use it to answer *"does a page exist, and where?"* and to turn a vague name into an
  exact path. If `index.md` lists the entity, you have your file in one step.
- **`hot.md`** is current world state — live threads, faction clocks, where the party is
  *right now*. Any "what's the current state of…" or "what's happening with…" question
  starts here, because hot.md is curated to be the present-tense truth.

If the answer is a known page's location or a piece of live state, you may already be
done. Read the specific file (Tier 2's read step) and stop.

### Tier 2 — Frontmatter and exact-term search (fast, deterministic)

When you know the name, slug, or a distinctive term, you don't need an LLM — you need a
match. Two fast tools, no rerank latency:

- **Grep the vault** for proper nouns, slugs, or distinctive phrases:
  ```bash
  grep -rli "barnaby rook" <wiki>/        # which files mention it
  grep -rn "summary:" <wiki>/entities/characters/  # scan summaries in a branch
  ```
  Every file leads with a `summary:` frontmatter line written to answer *what is this
  right now, and why does it matter*. **Read summaries before opening full files** —
  often the summary is the whole answer, and you save the context budget.

- **`<your-keyword-search-tool>`** — fast BM25/keyword search, no LLM. Best
  when you know the vocabulary (exact names, code-like identifiers, distinctive terms):
  ```bash
  <your-keyword-search-tool> "character name or term" -c <your-collection>
  ```

Then **Read the actual file** for the matched path. Keyword search and grep tell you *which* file;
the file itself is the source of truth — read it directly (full content, line numbers,
and you can see its wikilinks for the completeness pass below).

### Tier 3 — Semantic search (comprehensive, slower)

Reach for this when you *don't* know the exact term: conceptual or thematic questions,
fuzzy memory, synonyms, "anything we have about…", or when Tiers 1–2 came up empty or
partial. Semantic/vector search finds pages by *meaning*, not just words. It takes longer
than keyword search — worth it for recall, wasteful for a lookup you could have grepped.

```bash
<your-semantic-search-tool> "what favor does the NPC want from the party member" -c <your-collection> --json \
  | jq -r '.[] | "[\(.score)] \(.file)\n\(.snippet)\n"'
```

If your tool returns verbose output, filter to score, path, and snippet to stay lean on context budget.
Then Read the top files.

If your project includes a reference guide for your semantic search tool's query modes
(e.g. keyword-weighted, vector, hypothetical document expansion), read it when a plain
query underperforms.

---

## The completeness pass (always)

A single page is a starting point, not an answer. Once you have your primary hit, gather
the pages it depends on — this is what makes context *comprehensive* rather than just
*present*:

- **Follow the `relationships:` frontmatter** and inline `[[wikilinks]]` from the page.
  An NPC's faction, home location, the situation they're entangled in, the ship they crew.
- **Read summaries first.** For each linked page, the `summary:` frontmatter usually tells
  you whether you need the full file. Open the body only when the summary is insufficient
  (the reading-order: summary → section → full).
- **Pull current state.** If the entity appears in your hot/current-state file or an active situation directory, that present-tense state overrides older page prose.

Stop expanding when further pages stop changing the answer. The goal is *complete enough
to be correct*, not *the whole vault*.

---

## Escalation to raw sources

The canonical wiki collection is the default and usually sufficient. Only when
a compiled page is **missing or visibly incomplete** for what you need, search the raw
sources — unprocessed GM notes, transcripts, and drafts (if your project maintains a
separate raw/draft collection):

```bash
<your-semantic-search-tool> "<question>" -c <your-raw-collection> --json | jq -r '.[] | "[\(.score)] \(.file)\n\(.snippet)\n"'
```

Treat raw hits as **draft, not settled canon** — flag that the fact came from raw material
and may not yet be reconciled into the wiki. If a raw source answers something the wiki
should have, that's a signal the page needs ingesting; note it.

---

## Reporting what you found

How you close out a search determines whether the next step is trustworthy:

- **Ground every claim in a path.** When you state a campaign fact, it should be traceable
  to a file you read — reference it (e.g. `<wiki>/entities/.../character-slug.md`). This lets the DM
  verify and lets you catch your own drift.
- **Be explicit about absence.** If the wiki genuinely has nothing, say
  *"No wiki page covers X"* — do not manufacture an answer. Absence is useful information
  (it usually means the page should be created, which routes to a `prep-*` skill).
- **Surface contradictions, don't resolve them silently.** If two pages disagree, or a page
  contradicts the hot/current-state file, present both and flag it — append to your project's discrepancy log, never quietly pick one.

---

## Index freshness

If your project uses an auto-reindex hook, the search index stays current automatically
after wiki edits — you don't manage this.

One caveat worth knowing: vector **embeddings** are regenerated in the background and lag a
little behind brand-new pages. So a page created moments ago in *this* session may not yet
surface in semantic results. That's fine — for pages you just wrote you already have them
in context, and grep / keyword search catch them immediately. If the index appears stale,
consult your project's reindex command.

---

## Quick reference

| Need | Tool |
|---|---|
| Does a page exist / where is it | `<wiki>/index.md` (Tier 1) |
| Current world state, live threads | `<wiki>/hot.md` (Tier 1) |
| Find pages by exact name / term | `grep -rli` or `<your-keyword-search-tool> … -c <collection>` (Tier 2) |
| Find pages by meaning / concept | `<your-semantic-search-tool> "…" -c <collection> --json \| jq …` (Tier 3) |
| Read a known page | Read the file directly (full content + wikilinks) |
| Raw / unprocessed sources | Search `<your-raw-collection>` (escalation only) |

| Reference file | Read when |
|---|---|
| Your project's semantic search guide | Tuning queries, advanced query modes, collection/path map |

Operational rules (auto-correct, wikilinks) are in your project's wiki-init skill references. Project rules are in CLAUDE.md (always loaded).
