---
type: concept
tags: [llm-wiki, navigation]
created: 2026-07-10
updated: 2026-07-10
sources: ["[[llm-wiki-pattern-source]]"]
---

# Index and log

_The two special navigation files that let the LLM (and you) find your way around the
[[llm-wiki-pattern|wiki]] as it grows. They serve different purposes._

## index.md — content-oriented

A **catalog** of everything in the wiki: each page listed with a link, a one-line summary, and
optional metadata (date, source count), organized by category (sources, entities, concepts, syntheses).
Updated on every ingest. On a [[wiki-operations#Query|query]] the LLM **reads the index first** to
locate relevant pages, then drills in. This index-first approach works well at moderate scale
(~100 sources, hundreds of pages) and **avoids embedding-based [[rag|RAG]] infrastructure** entirely.

## log.md — chronological

An **append-only** record of what happened and when — ingests, queries, lint passes. If each entry
starts with a consistent prefix it becomes parseable with plain unix tools:

```
## [2026-07-10] ingest | Article Title
```
```
grep "^## \[" log.md | head -5   # the 5 most recent entries
```

The log gives a timeline of the wiki's evolution and helps the LLM see what's been done recently.

> [!note] Convention in this vault
> The seed source uses `tail -5` for the last entries (append at bottom). This vault instead puts
> **newest entries at the top**, so `head -5` shows the most recent — see `CLAUDE.md`.

## How it relates to other ideas

- Written on every [[wiki-operations|operation]].
- The index-first strategy is why this vault can skip [[qmd]]/[[rag]] tooling at small scale.

## Sources

- [[llm-wiki-pattern-source]]
