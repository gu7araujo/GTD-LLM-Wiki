---
type: index
updated: 2026-07-10
---

# Index

The content catalog for this wiki — every page with a one-line summary, organized by category. This is
the **first thing to read when answering a query**: scan here to find relevant pages, then drill in.
Updated on every ingest, query-that-files-a-page, and lint. See `CLAUDE.md` for conventions, [[overview]]
for the big picture, and [[log]] for the timeline.

**Counts:** 1 source · 2 entities (people) · 2 entities (tools) · 5 concepts · 0 syntheses

---

## Overview & navigation
- [[overview]] — top-level map of the vault and current working thesis.
- [[index]] — this catalog (you are here).
- [[log]] — chronological, append-only record of ingests / queries / lints.

## Sources — `wiki/sources/`
- [[llm-wiki-pattern-source]] — Karpathy's "LLM Wiki" gist; the seed source describing the pattern this vault implements. `2026-07-10` · raw: [[raw/karpathy-llm-wiki-gist]]

## Entities — `wiki/entities/`
**People**
- [[andrej-karpathy]] — author of the LLM Wiki pattern; coined "Obsidian = IDE, LLM = programmer, wiki = codebase."
- [[vannevar-bush]] — originator of the [[memex]] (1945), the associative-knowledge-store antecedent.

**Tools**
- [[obsidian]] — markdown KB app; the front-end / "IDE" for this vault.
- [[qmd]] — optional local markdown search engine (BM25+vector, CLI + MCP); for when the index stops scaling.

## Concepts — `wiki/concepts/`
- [[llm-wiki-pattern]] — the core pattern: LLM builds & maintains a persistent, compounding wiki.
- [[rag]] — retrieval-augmented generation; the re-derive-every-query foil the pattern improves on.
- [[three-layer-architecture]] — raw sources → wiki → schema; who owns each layer.
- [[wiki-operations]] — the three verbs: ingest, query, lint (+ the schema that governs them).
- [[index-and-log]] — the two navigation files and why index-first beats embeddings at moderate scale.
- [[memex]] — Vannevar Bush's 1945 vision; the pattern's spiritual ancestor.

## Syntheses — `wiki/syntheses/`
- _(none yet — filed query answers, comparisons, and discovered connections will be cataloged here.)_

## Red links to fill (mentioned, no page yet)
- [[dataview]] · [[marp]] · [[obsidian-web-clipper]] · [[notebooklm]] · [[tolkien-gateway]]
