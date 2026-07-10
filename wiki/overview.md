---
type: overview
tags: [llm-wiki, meta]
created: 2026-07-10
updated: 2026-07-10
sources: ["[[llm-wiki-pattern-source]]"]
---

# Overview

_The top-level map of this vault and its current working thesis. Start here, then use [[index|the index]]
to find specific pages and [[log|the log]] to see recent activity._

## What this vault is

A personal knowledge base built on Andrej Karpathy's [[llm-wiki-pattern|LLM Wiki]] pattern. An LLM agent
([[andrej-karpathy|Claude Code]], here) incrementally builds and maintains an interlinked wiki of
markdown pages that sits between me and my raw sources. I curate sources and ask questions; the LLM does
the reading, summarizing, cross-referencing, and bookkeeping. See the schema in `CLAUDE.md` for how it
operates.

## Current thesis

The vault is **seeded with the pattern that describes it** — meta but useful, because the seed source
doubles as the reference for how the system should work. The working claims so far:

- Persistent, compounding wikis beat query-time [[rag|RAG]] for knowledge that accumulates over time.
- The value is in **maintenance the LLM does for free**: cross-refs, contradiction flags, consistency.
- At this scale, [[index-and-log|index-first navigation]] is enough — no search engine ([[qmd]]) needed yet.

_This thesis will evolve as real domain sources (beyond the meta seed) are ingested._

## Map of the wiki

**Concepts** — the ideas
- [[llm-wiki-pattern]] — the core pattern (vs [[rag]])
- [[three-layer-architecture]] — raw → wiki → schema
- [[wiki-operations]] — ingest / query / lint
- [[index-and-log]] — the two navigation files
- [[memex]] — the 1945 antecedent

**Entities** — the people & tools
- People: [[andrej-karpathy]], [[vannevar-bush]]
- Tools: [[obsidian]] (the front-end), [[qmd]] (optional search)

**Sources** — what's been ingested
- [[llm-wiki-pattern-source]] — Karpathy's "LLM Wiki" gist (seed)

**Syntheses** — kept answers & analyses
- _(none yet — the first good query answer filed here will seed this section)_

## What to add next

Real domain sources. Candidate red-link pages waiting to be filled: [[dataview]], [[marp]],
[[obsidian-web-clipper]], [[notebooklm]], [[tolkien-gateway]].
