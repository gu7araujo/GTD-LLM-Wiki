---
type: log
updated: 2026-07-11
---

# Log

Append-only, reverse-chronological record of everything done to this wiki — ingests, queries, lint
passes. **Newest entries at the top.** Each header uses a fixed, greppable prefix so the log stays
machine-readable:

```
grep "^## \[" log.md | head -5     # the 5 most recent entries
```

Header format: `## [YYYY-MM-DD] <op> | <title>` where `<op>` ∈ `ingest` · `query` · `lint`.
See [[index]] for the content catalog and [[overview]] for the big picture.

---

## [2026-07-11] query  | How to deal with internal agreements (GTD)?

- Answered entirely from [[open-loops]] (aliases already covered "acordos internos"): stress mechanism (p42–46), the three options for broken agreements — don't make / keep / renegotiate (p283–286), and Baumeister's finding that a trusted plan releases the burden without completion (p319).
- No new pages filed: the concept page already held the full answer.

## [2026-07-11] query  | What does the GTD book say about the weekly review?

- Answered entirely from [[weekly-review]] (verbatim quotes, pp. 80, 231–236, 343) — no re-read of `raw/` needed; the quote-retrieval convention worked as intended.
- No new pages filed: the concept page already held the full answer, so a synthesis would duplicate it.

## [2026-07-11] ingest | Getting Things Done (A arte de fazer acontecer) — book notes

- **Read:** [[raw/allen-gtd-book-notes]] in full — Gustavo's reading notes of David Allen's GTD (Brazilian revised ed.), 1,085 lines with page cites p14–p343, incl. the appendix glossary.
- **Created (17 pages):**
  - Source: [[allen-gtd-book-notes-source]]
  - Entity: [[david-allen]]
  - Concepts: [[gtd-method]] (hub), [[gtd-glossary]], [[capture]], [[clarify]], [[organize]], [[reflect]], [[engage]], [[weekly-review]], [[next-action]], [[open-loops]], [[natural-planning-model]], [[brainstorming]], [[mind-like-water]], [[horizons-of-focus]], [[distributed-cognition]]
- **Updated:** [[overview]] (GTD cluster + cross-domain thesis note), [[memex]] and [[llm-wiki-pattern]] (link to [[distributed-cognition]]), [[index]].
- **Decisions (per Gustavo's direction — optimize for quote-retrieval):**
  - Every GTD concept page carries **verbatim Portuguese quotes with page numbers** under "What the book says", plus the term's glossary definition (p343) up top — so "what does the book say about X?" is answerable with quotes from the wiki alone.
  - [[gtd-glossary]] transcribes the whole appendix glossary verbatim, each term linked to its full page — the designated go-to entry point.
  - **New convention:** bilingual `aliases:` frontmatter (e.g. `capturar`/`capture phase`) for PT/EN retrieval. Worth adopting vault-wide.
  - Page names in English kebab-case, H1 shows both languages; provenance callout on the source page notes quotes are from reading notes (possible paraphrase).
  - Red link left for [[roy-baumeister]]; Drucker quote (p45) left unattributed since the notes don't attribute it.

## [2026-07-10] ingest | LLM Wiki — Karpathy gist (seed source)

- **Read:** [[raw/karpathy-llm-wiki-gist]] — Andrej Karpathy's "LLM Wiki" idea file, in full.
- **Created (13 pages):**
  - Source: [[llm-wiki-pattern-source]]
  - Concepts: [[llm-wiki-pattern]], [[rag]], [[three-layer-architecture]], [[wiki-operations]], [[index-and-log]], [[memex]]
  - Entities: [[andrej-karpathy]], [[vannevar-bush]], [[obsidian]], [[qmd]]
  - Navigation: [[overview]], [[index]], and this [[log]]
- **Scaffolding:** created `CLAUDE.md` schema, the `raw/ wiki/{sources,entities,concepts,syntheses} templates/` structure, and all five templates.
- **Notes:**
  - This is a **meta seed** — the source describes the very pattern the vault implements, so it doubles as living documentation of the workflow.
  - Enforced unique basenames across the vault: source page suffixed `-source`; raw file named `karpathy-llm-wiki-gist` and linked only via path-qualified `[[raw/...]]`. Rule recorded in `CLAUDE.md`.
  - Left intentional red links for future pages: [[dataview]], [[marp]], [[obsidian-web-clipper]], [[notebooklm]], [[tolkien-gateway]].
  - Adopted a house convention that departs from the source: **log newest-first** (source used append-at-bottom / `tail`). Noted on [[index-and-log]].
