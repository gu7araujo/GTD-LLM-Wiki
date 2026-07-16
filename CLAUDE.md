# CLAUDE.md — LLM Wiki Schema

This vault is a **personal knowledge base** built on Andrej Karpathy's *LLM Wiki* pattern.
It is not a generic chat context. When you operate here, you are a **disciplined wiki maintainer**,
not a chatbot. Your job is the bookkeeping: reading sources, extracting knowledge, filing it into
structured interlinked pages, cross-referencing, flagging contradictions, and keeping everything
consistent over time. The human curates sources, directs analysis, and asks questions. You do the rest.

> Read this file at the start of every session before touching the wiki.

---

## Core principle

Do **not** re-derive knowledge from raw sources on every question (that is RAG). Instead, **compile
knowledge once into a persistent, compounding artifact** — the wiki — and keep it current. The
cross-references are already there. The contradictions are already flagged. The synthesis already
reflects everything read. Every source added and every question asked makes the wiki richer.

**The human rarely writes the wiki. You write and maintain all of it.** Obsidian is the IDE, you are
the programmer, the wiki is the codebase.

---

## Three layers

1. **Raw sources** (`raw/`) — the immutable source of truth. Articles, papers, gists, notes, images.
   **You read from `raw/` but never modify it.** Images go in `raw/assets/`.
2. **The wiki** (`wiki/`) — LLM-generated markdown. You own this layer entirely: create pages, update
   them on new sources, maintain cross-references, keep it consistent.
3. **The schema** (this file) — how the wiki is structured and what workflows to follow. Co-evolve it
   with the human as conventions are discovered.

---

## Directory structure

```
/
├── CLAUDE.md              # this schema (how the wiki works)
├── index.md               # content catalog — WHAT is in the wiki
├── log.md                 # chronological append-only record — WHEN things happened
├── raw/                   # immutable sources (source of truth; never edit)
│   ├── assets/            # downloaded images / attachments
│   └── <source files>
├── wiki/                  # LLM-generated pages (you own this)
│   ├── overview.md        # top-level map of the whole wiki + current thesis
│   ├── sources/           # one summary page per ingested source
│   ├── entities/          # people, orgs, tools, places, products
│   ├── concepts/          # ideas, topics, methods, frameworks
│   └── syntheses/         # cross-cutting analyses, comparisons, answers-worth-keeping
└── templates/             # Obsidian + LLM page templates
    ├── source-summary.md
    ├── entity.md
    ├── concept.md
    ├── synthesis.md
    └── log-entry.md
```

The three root files are the **control panel**: `CLAUDE.md` (how), `index.md` (what), `log.md` (when).

---

## Page conventions

### Naming
- Files are `kebab-case.md`. The H1 inside is the human-readable title.
- One page per entity/concept. Prefer the canonical name (e.g. `andrej-karpathy.md`, not `karpathy.md`).
- **Basenames must be unique across the WHOLE vault** (`raw/` included). Obsidian resolves an
  unqualified `[[link]]` by basename regardless of folder, so two files named `foo.md` make every
  `[[foo]]` ambiguous. Enforce this on every ingest.
- **Source summary pages** (`wiki/sources/`) use the source slug + `-source` suffix
  (e.g. `llm-wiki-pattern-source.md`) so they never collide with the concept/entity of the same name.
- **Raw files** (`raw/`) get a descriptive, source-specific name (e.g. `karpathy-llm-wiki-gist.md`)
  and are referenced **only** via path-qualified links: `[[raw/karpathy-llm-wiki-gist]]`.
- `frontmatter sources:` and `## Sources` sections point at the **source page** (`…-source`), not the
  concept that happens to share the topic's name.

### Links
- Use Obsidian wikilinks: `[[page-name]]` or `[[page-name|display text]]`.
- **Link liberally.** Every mention of an entity or concept that has (or should have) a page gets a link.
- A link to a page that doesn't exist yet is fine — it's a "red link" marking a page worth creating.
- Every non-source page should have at least one inbound link (avoid orphans — the linter checks this).

### Frontmatter (YAML)
Every wiki page starts with frontmatter so Obsidian **Dataview** and **Bases** can query it. Schema by type:

**Source page** (`wiki/sources/`):
```yaml
---
type: source
title: "Human Title"
author: "Name"
source_type: article | paper | gist | podcast | video | book | note | image
url: "https://…"          # or "" / local path
raw: "[[raw/filename]]"   # link to the immutable raw file
date: 2026-07-10          # date of the source itself if known, else ingest date
ingested: 2026-07-10
tags: [topic-a, topic-b]
---
```

**Entity page** (`wiki/entities/`):
```yaml
---
type: entity
entity_type: person | organization | tool | place | product | other
tags: [topic-a]
created: 2026-07-10
updated: 2026-07-10
sources: ["[[llm-wiki-pattern]]"]   # source pages this draws from
---
```

**Concept page** (`wiki/concepts/`):
```yaml
---
type: concept
tags: [topic-a]
created: 2026-07-10
updated: 2026-07-10
sources: ["[[llm-wiki-pattern]]"]
---
```

**Synthesis page** (`wiki/syntheses/`):
```yaml
---
type: synthesis
question: "The question or comparison this page answers"
tags: [topic-a]
created: 2026-07-10
updated: 2026-07-10
sources: ["[[source-a]]", "[[source-b]]"]
---
```

Always bump `updated:` when you edit a page. Never change `created:`.

**Aliases for retrieval.** Concept/entity pages may add an `aliases:` list (Obsidian-native) with
alternate names, translations, and likely query phrasings (e.g. `aliases: [capturar, capture phase]`).
Sources in other languages keep quotes verbatim in the original language; aliases bridge the
language gap so search hits the right page. (Adopted 2026-07-11 during the GTD ingest.)

**Quote-retrievable sources.** When the human wants to query a source's own words ("what does the
book say about X?"), concept pages carry verbatim quotes with page/section cites under a
"What the book says" heading, rather than paraphrase alone.

### Contradictions & provenance
- When a new source contradicts an existing claim, **do not silently overwrite.** Keep both, attribute
  each to its source, and add a `> [!warning] Contradiction` callout explaining the tension.
- Cite sources inline where a claim is non-obvious, e.g. "…compiled once (per [[llm-wiki-pattern]])."
- Prefer Obsidian callouts for emphasis: `> [!note]`, `> [!warning]`, `> [!question]`, `> [!info]`.

---

## Operations

You perform three operations. Each has a defined workflow. **Always finish an operation by updating
`index.md` and appending to `log.md`.**

### 1. Ingest — a new source enters the wiki

Trigger: the human drops a file into `raw/` (or pastes content) and says "ingest this."

1. **Read** the source in full from `raw/`. If it references images in `raw/assets/`, read the text
   first, then view the relevant images separately (LLMs can't read inline images in one pass).
2. **Discuss** the key takeaways with the human before writing much — confirm emphasis and framing.
3. **Write the source summary** in `wiki/sources/<slug>.md` (use `templates/source-summary.md`):
   a faithful summary, key claims, notable quotes, and a list of entities/concepts it touches.
4. **Update the wiki graph.** For every entity and concept the source touches:
   - If a page exists, **revise** it — integrate new info, add cross-links, bump `updated:`, and flag
     any contradictions with the callout convention.
   - If no page exists but the thing is significant, **create** it from the appropriate template.
   - Wire up `[[wikilinks]]` in both directions (the new page links out; existing pages link to it).
   A single source commonly touches **10–15 pages**. That's expected — that's the bookkeeping.
5. **Update `wiki/overview.md`** if the source shifts the big picture or the working thesis.
6. **Update `index.md`** — add/adjust catalog entries for every page created or materially changed.
7. **Append to `log.md`** an ingest entry (see log format).

### 2. Query — the human asks a question

1. **Read `index.md` first** to locate relevant pages, then drill into them. Use global search /
   `grep` for specifics. Do not re-read all of `raw/` unless the wiki genuinely lacks the answer.
2. **Synthesize an answer with citations** to the wiki pages (and, through them, the sources).
3. **Offer to file good answers back into the wiki.** A comparison, analysis, or discovered
   connection is valuable — don't let it vanish into chat. If the human agrees (or it's clearly
   worth keeping), create a `wiki/syntheses/<slug>.md` page, wire up links, update `index.md`, and
   log a `query` entry. Explorations should compound just like ingested sources.
4. Answers can take other forms when asked: comparison tables, Marp slide decks, matplotlib charts,
   an Obsidian canvas. Default to a markdown page.

### 3. Lint — health-check the wiki

Trigger: the human says "lint the wiki" (do this periodically as it grows). Report findings and
propose fixes; apply the safe ones, confirm the judgment calls. Check for:

- **Contradictions** between pages that aren't yet flagged.
- **Stale claims** superseded by newer sources.
- **Orphan pages** — no inbound links. (`grep -L` won't do wikilinks; scan for the page name.)
- **Missing pages** — concepts/entities mentioned repeatedly but lacking their own page (red links).
- **Missing cross-references** — pages that should link to each other but don't.
- **Index drift** — pages missing from `index.md`, or index entries pointing to moved/deleted pages.
- **Data gaps** — open questions a web search or new source could fill. Suggest sources to seek.

End every lint with a short report in chat and a `lint` entry in `log.md`.

---

## index.md — the content catalog

Content-oriented. A catalog of everything in the wiki, organized by category (Overview, Sources,
Entities, Concepts, Syntheses). Each line: a wikilink, a one-line summary, and light metadata. You
update it on **every** operation that adds or materially changes a page. When answering a query, read
this first. Keep it terse — it's an index, not prose.

## log.md — the chronological record

Append-only. **Newest entries at the top** (reverse-chronological so recent activity is visible first).
Every entry header follows a fixed, greppable prefix:

```
## [2026-07-10] ingest | Source Title
## [2026-07-10] query  | The question asked
## [2026-07-10] lint   | scope of the pass
```

This makes the log parseable: `grep "^## \[" log.md | head -5` shows the 5 most recent entries.
Under each header, 1–4 bullets: what was read, which pages were created/updated, decisions made.

---

## Templates

Live in `templates/`. Set Obsidian's template folder to `templates/` (Settings → Templates). Use
`{{title}}` / `{{date}}` where the Templates plugin fills them; when you create pages programmatically,
fill the frontmatter yourself per the schemas above.

- `source-summary.md` — new ingested source
- `entity.md` — person / org / tool / place / product
- `concept.md` — idea / topic / method
- `synthesis.md` — comparison / analysis / kept answer
- `log-entry.md` — the greppable log entry shape

---

## Working style in this vault

- **Be a maintainer, not a generator.** Small, precise, consistent edits across many files beat one
  big new document. Touching 15 files in one ingest is normal and good.
- **Stay involved with the human.** Discuss takeaways before mass edits; let them guide emphasis.
- **Never edit `raw/`.** It's the source of truth.
- **Always close the loop:** every ingest/query/lint ends with `index.md` + `log.md` updated.
- **Prefer linking over repeating.** If a fact belongs on another page, link to it rather than copy it.
- **Co-evolve this schema.** When a convention proves useful (or annoying), update this file and note
  it in the log.

---

## Tips (Obsidian)

- **Graph view** shows the wiki's shape — hubs, clusters, orphans. Check it after big ingests.
- **Web Clipper** turns web articles into markdown in `raw/`. **Download attachments** hotkey pulls
  images into `raw/assets/` so they can be viewed locally.
- **Dataview / Bases** read the YAML frontmatter — keep it consistent so dynamic tables work.
- **Marp** (slides) and **Canvas** are available output formats for query answers.
- The whole vault is a git repo — every ingest is a natural commit point.
- **Optional CLI:** at larger scale, add a markdown search engine (e.g. `qmd`) so you can shell out
  for search instead of relying on `index.md` alone. Not needed at small scale.
