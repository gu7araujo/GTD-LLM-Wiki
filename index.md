---
type: index
updated: 2026-07-25
---

# Index

The content catalog for this wiki — every page with a one-line summary, organized by category. This is
the **first thing to read when answering a query**: scan here to find relevant pages, then drill in.
Updated on every ingest, query-that-files-a-page, and lint. See `CLAUDE.md` for conventions, [[overview]]
for the big picture, and [[log]] for the timeline.

**Counts:** 2 sources · 3 entities (people) · 2 entities (tools) · 19 concepts · 3 syntheses

---

## Overview & navigation
- [[overview]] — top-level map of the vault and current working thesis.
- [[index]] — this catalog (you are here).
- [[log]] — chronological, append-only record of ingests / queries / lints.

## Sources — `wiki/sources/`
- [[llm-wiki-pattern-source]] — Karpathy's "LLM Wiki" gist; the seed source describing the pattern this vault implements. `2026-07-10` · raw: [[raw/karpathy-llm-wiki-gist]]
- [[allen-gtd-book-notes-source]] — David Allen's *Getting Things Done* (Brazilian ed.), reading notes with page cites; concept pages carry verbatim PT quotes. `2026-07-11` · raw: [[raw/allen-gtd-book-notes]]

## Entities — `wiki/entities/`
**People**
- [[andrej-karpathy]] — author of the LLM Wiki pattern; coined "Obsidian = IDE, LLM = programmer, wiki = codebase."
- [[vannevar-bush]] — originator of the [[memex]] (1945), the associative-knowledge-store antecedent.
- [[david-allen]] — author of *Getting Things Done*; creator of the [[gtd-method]].

**Tools**
- [[obsidian]] — markdown KB app; the front-end / "IDE" for this vault.
- [[qmd]] — optional local markdown search engine (BM25+vector, CLI + MCP); for when the index stops scaling.

## Concepts — `wiki/concepts/`
**Meta (LLM Wiki)**
- [[llm-wiki-pattern]] — the core pattern: LLM builds & maintains a persistent, compounding wiki.
- [[rag]] — retrieval-augmented generation; the re-derive-every-query foil the pattern improves on.
- [[three-layer-architecture]] — raw sources → wiki → schema; who owns each layer.
- [[wiki-operations]] — the three verbs: ingest, query, lint (+ the schema that governs them).
- [[index-and-log]] — the two navigation files and why index-first beats embeddings at moderate scale.
- [[memex]] — Vannevar Bush's 1945 vision; the pattern's spiritual ancestor.

**GTD (productivity)** — all pages quote the book verbatim (PT) with page numbers
- [[gtd-method]] — hub: the five steps, the two essential elements, principles-over-methods, ch.14 science.
- [[gtd-glossary]] — the appendix "Glossário de termos do GTD" (p343), verbatim; go-to for term lookups.
- [[capture]] — capturar/coletar; inboxes, the three success factors, the power of the capture habit.
- [[clarify]] — esclarecer/processar; "exige ação?", the two-minute rule, processing guidelines.
- [[organize]] — organizar; projects, calendar, context lists, Waiting For, Someday/Maybe, reference.
- [[reflect]] — refletir/revisar; what to review and when; why trust requires currency.
- [[engage]] — engajar; four-criteria model, threefold model, interruptions & multitasking.
- [[weekly-review]] — "a chave mágica da sustentabilidade do processo"; what/why/when/where.
- [[next-action]] — the signature question; the 10-second gap, smart-people procrastination, meetings.
- [[open-loops]] — laços abertos / internal agreements; the stress mechanism GTD solves; Baumeister.
- [[natural-planning-model]] — the five planning phases + unnatural/reactive anti-patterns.
- [[brainstorming]] — the *how* phase; capture keys (no judgment, quantity, defer analysis); mind maps.
- [[mind-like-water]] — the promised state; martial-arts ready position; flow theory.
- [[horizons-of-focus]] — the six altitudes (Térreo → Horizonte 5), from the glossary.
- [[distributed-cognition]] — "extensão da mente"; the bridge between GTD and the [[llm-wiki-pattern]].

## Syntheses — `wiki/syntheses/`
- [[separate-the-phases]] — why GTD's five steps must be run as separate passes, not all at once (p59). `2026-07-16`
- [[inbox-processing-template]] — what fields a note template should have for processing an inbox item: propósito/princípios/resultado/próxima ação from [[natural-planning-model]], plus the "exige ação?" tree missing from it. `2026-07-25`
- [[gtd-open-loop-exercise]] — the Chapter 1 "important exercise" (p43): capture one internal agreement, then clarify it into outcome + next action; distinguished from the Chapter 3 planning-model exercise. `2026-08-31`

## Red links to fill (mentioned, no page yet)
- [[dataview]] · [[marp]] · [[obsidian-web-clipper]] · [[notebooklm]] · [[tolkien-gateway]] · [[roy-baumeister]]
