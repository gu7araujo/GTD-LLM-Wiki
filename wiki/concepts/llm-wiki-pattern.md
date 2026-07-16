---
type: concept
tags: [llm-wiki, knowledge-management]
created: 2026-07-10
updated: 2026-07-11
sources: ["[[llm-wiki-pattern-source]]"]
---

# LLM Wiki (the pattern)

_A method for building a personal knowledge base where an LLM incrementally builds and maintains a
persistent, interlinked wiki that sits between you and your raw sources._

## What it is

Rather than treating documents as a pile to retrieve from at query time (see [[rag]]), the LLM reads
each new source and **integrates** it into an existing wiki: updating entity pages, revising topic
summaries, flagging contradictions, and strengthening or challenging the evolving synthesis. Knowledge
is **compiled once and kept current**, not re-derived on every question.

Its structure is the [[three-layer-architecture]]; its verbs are the three [[wiki-operations]]
(ingest / query / lint); its navigation aids are the [[index-and-log|index and log]].

## Why it matters

- **It compounds.** The cross-references are already there; the contradictions already flagged; the
  synthesis already reflects everything read. Every source and every question makes it richer.
- **It survives.** Humans abandon wikis because maintenance grows faster than value. The LLM makes
  maintenance cost ≈ 0, so the wiki stays current. This is the core reason the pattern works.
- **Division of labor.** Human curates sources, explores, asks good questions. LLM does the
  summarizing, cross-referencing, filing, and bookkeeping.

## How it relates to other ideas

- **Contrast:** [[rag]] — retrieval without accumulation; the thing this pattern improves on.
- **Ancestor:** [[memex]] — Vannevar Bush's 1945 vision of associative trails; the LLM solves the
  "who does the maintenance" problem Bush couldn't.
- **Psychology:** [[distributed-cognition]] — GTD's name for the same move ("extensão da mente",
  per [[allen-gtd-book-notes-source]]); the wiki is to knowledge what a GTD system is to commitments.
- **Mechanism:** [[three-layer-architecture]], [[wiki-operations]], [[index-and-log]].
- **Author / tools:** [[andrej-karpathy]], [[obsidian]], [[qmd]].
- **Metaphor:** Obsidian is the IDE, the LLM is the programmer, the wiki is the codebase.

## Open questions

- Where does this pattern stop scaling with index-first navigation alone?
- One-at-a-time vs. batch ingest — what's the right supervision level?

## Sources

- [[llm-wiki-pattern-source]] (Karpathy gist — the seed source)
