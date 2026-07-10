---
type: log
updated: 2026-07-10
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
