# GTD LLM Wiki

A personal knowledge base built on [Andrej Karpathy's "LLM Wiki"](https://github.com/karpathy) pattern:
instead of re-deriving answers from raw sources on every question (RAG), knowledge is **compiled once
into a persistent, compounding wiki** — structured, cross-linked, and kept current by an LLM.

> Obsidian is the IDE, the LLM is the programmer, the wiki is the codebase.

The human curates sources and directs analysis; Claude reads, extracts, files, cross-references, and
flags contradictions. This instance is seeded with the *LLM Wiki* pattern itself and David Allen's
*Getting Things Done* (GTD), as a worked example of turning a book into structured, queryable pages
rather than a pile of notes.

## How it's organized

```
CLAUDE.md    # the schema — how the wiki is built and maintained
index.md     # content catalog — what's in the wiki
log.md       # append-only record — when things happened
raw/         # immutable source material (never edited)
wiki/        # LLM-generated, cross-linked markdown
  sources/     one summary page per ingested source
  entities/    people, orgs, tools, places, products
  concepts/    ideas, methods, frameworks
  syntheses/   cross-cutting analyses and kept answers
templates/   # Obsidian page templates
```

## How it works

Three operations, each closing the loop through `index.md` and `log.md`:

- **Ingest** — a new source is read in full, summarized, and its entities/concepts are created or
  revised across the wiki, with bidirectional links. A single source typically touches 10–15 pages.
- **Query** — questions are answered by reading the index first, drilling into relevant pages, and
  citing sources. Good answers can be filed back as synthesis pages so exploration compounds too.
- **Lint** — a periodic health check for contradictions, stale claims, orphan pages, and gaps.

Full conventions (naming, frontmatter schema, linking rules, contradiction handling) live in
[`CLAUDE.md`](CLAUDE.md).

## Requirements

- [Obsidian](https://obsidian.md) as the viewer/editor (Dataview plugin recommended for querying
  frontmatter).
- [Claude Code](https://claude.com/claude-code) (or another agent reading `CLAUDE.md`) as the
  maintainer.
