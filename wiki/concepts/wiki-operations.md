---
type: concept
tags: [llm-wiki, workflow]
created: 2026-07-10
updated: 2026-07-10
sources: ["[[llm-wiki-pattern-source]]"]
---

# Wiki operations (ingest / query / lint)

_The three verbs that move information through the [[three-layer-architecture]] and keep the
[[llm-wiki-pattern|LLM Wiki]] alive._

## Ingest

A new source enters. The LLM reads it, **discusses key takeaways** with the human, writes a summary
page in `wiki/sources/`, updates the [[index-and-log|index]], updates relevant entity and concept pages
across the wiki, and appends to the [[index-and-log|log]]. **A single source might touch 10–15 pages.**
Preference in the seed source: ingest one at a time and stay involved; batch ingest is possible with
less supervision.

## Query

The human asks a question. The LLM reads the [[index-and-log|index]] first, drills into relevant pages,
and synthesizes an answer **with citations**. Answers can be markdown, a comparison table, a [[marp]]
slide deck, a matplotlib chart, or a [[obsidian|canvas]]. **Key insight: good answers get filed back
into the wiki as new pages** (in `wiki/syntheses/`) so explorations compound like ingested sources.

## Lint

Periodic health check. Look for: contradictions between pages, stale claims superseded by newer
sources, orphan pages with no inbound links, important concepts lacking their own page, missing
cross-references, and data gaps a web search could fill. The LLM also suggests new questions and
sources to seek. Keeps the wiki healthy as it grows.

## Schema

Not an operation but the config that governs all three: the [[three-layer-architecture|schema file]]
(`CLAUDE.md` here) documents these workflows so every session runs them consistently. Co-evolve it as
conventions are discovered.

## How it relates to other ideas

- Operates over the [[three-layer-architecture]].
- Reads/writes the [[index-and-log]] on every pass.

## Sources

- [[llm-wiki-pattern-source]]
