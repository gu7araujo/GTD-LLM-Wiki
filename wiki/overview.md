---
type: overview
tags: [llm-wiki, meta]
created: 2026-07-10
updated: 2026-07-11
sources: ["[[llm-wiki-pattern-source]]", "[[allen-gtd-book-notes-source]]"]
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
- **First real domain is in: GTD.** The vault now holds David Allen's method as a quote-retrievable
  cluster ([[gtd-method]] hub + [[gtd-glossary]] + one page per term). Emerging cross-domain claim:
  GTD and the LLM Wiki are the **same move in different domains** — [[distributed-cognition]]
  (externalize into a trusted, regularly reviewed system) applied to commitments vs. knowledge.
  Even the maintenance rituals rhyme: [[weekly-review]] ↔ wiki lint.

_This thesis will evolve as more domain sources are ingested._

## Map of the wiki

**Concepts — meta (the LLM Wiki itself)**
- [[llm-wiki-pattern]] — the core pattern (vs [[rag]])
- [[three-layer-architecture]] — raw → wiki → schema
- [[wiki-operations]] — ingest / query / lint
- [[index-and-log]] — the two navigation files
- [[memex]] — the 1945 antecedent

**Concepts — GTD (productivity)**
- [[gtd-method]] — hub: the five steps and the method's promise
- [[gtd-glossary]] — the book's term glossary, verbatim (go-to for "what does the book say about X?")
- The five steps: [[capture]] · [[clarify]] · [[organize]] · [[reflect]] · [[engage]]
- Key practices & ideas: [[weekly-review]], [[next-action]], [[open-loops]], [[natural-planning-model]], [[brainstorming]], [[mind-like-water]], [[horizons-of-focus]], [[distributed-cognition]]

**Entities** — the people & tools
- People: [[andrej-karpathy]], [[vannevar-bush]], [[david-allen]]
- Tools: [[obsidian]] (the front-end), [[qmd]] (optional search)

**Sources** — what's been ingested
- [[llm-wiki-pattern-source]] — Karpathy's "LLM Wiki" gist (seed)
- [[allen-gtd-book-notes-source]] — GTD book notes (Brazilian edition, with page cites)

**Syntheses** — kept answers & analyses
- _(none yet — the first good query answer filed here will seed this section)_

## What to add next

Real domain sources. Candidate red-link pages waiting to be filled: [[dataview]], [[marp]],
[[obsidian-web-clipper]], [[notebooklm]], [[tolkien-gateway]].
