---
type: concept
tags: [llm-wiki, architecture]
created: 2026-07-10
updated: 2026-07-10
sources: ["[[llm-wiki-pattern-source]]"]
---

# Three-layer architecture

_The structural backbone of the [[llm-wiki-pattern|LLM Wiki]]: raw sources → wiki → schema._

## What it is

| Layer | Directory | Who owns it | Role |
|---|---|---|---|
| **Raw sources** | `raw/` | Human (curates) | Immutable source of truth. Articles, papers, gists, images. The LLM reads but **never modifies** them. |
| **The wiki** | `wiki/` | LLM (fully) | Generated markdown: summaries, [[wiki-operations|entity/concept pages]], comparisons, overview, synthesis. The LLM creates, updates, and cross-references. |
| **The schema** | `CLAUDE.md` | Human + LLM (co-evolved) | Tells the LLM how the wiki is structured and what workflows to follow. Turns the LLM into a disciplined maintainer rather than a chatbot. |

## Why it matters

The separation is what keeps the system trustworthy and durable:

- **Immutability of `raw/`** means the source of truth can always be re-derived from — the wiki is a
  lossy, opinionated compilation, but the originals are never corrupted.
- **LLM ownership of `wiki/`** means no human bottleneck on maintenance — the reason the pattern
  survives where human-maintained wikis die.
- **The schema as config** is the highest-leverage file: get it right and every future session behaves
  like a disciplined librarian. In this vault the schema is `CLAUDE.md`; for Codex it would be
  `AGENTS.md`.

## How it relates to other ideas

- Realized through the [[wiki-operations]] (ingest / query / lint) that move information between layers.
- Navigated via the [[index-and-log]] files.
- Tooling for the layers: [[obsidian]] (browse/edit), [[qmd]] (optional search over the wiki layer).

## Open questions

- When does the wiki layer need sub-structure beyond `sources / entities / concepts / syntheses`?

## Sources

- [[llm-wiki-pattern-source]]
