---
type: concept
tags: [llm-wiki, retrieval, contrast]
created: 2026-07-10
updated: 2026-07-10
sources: ["[[llm-wiki-pattern-source]]"]
---

# RAG (Retrieval-Augmented Generation)

_The default pattern for LLMs over documents: retrieve relevant chunks at query time and generate an
answer from them. The foil against which the [[llm-wiki-pattern|LLM Wiki]] pattern is defined._

## What it is

You upload a collection of files; at query time the LLM retrieves the relevant chunks (often via
embeddings) and generates an answer. NotebookLM, ChatGPT file uploads, and most "chat with your docs"
systems work this way.

## Why it matters (and its limitation)

RAG works, but **the LLM rediscovers knowledge from scratch on every question** — there is no
accumulation. A subtle question that requires synthesizing five documents forces the model to find and
piece together the fragments *every time*. Nothing is built up between queries.

> [!note] The key contrast
> RAG **retrieves**; the [[llm-wiki-pattern|LLM Wiki]] **accumulates**. The wiki compiles knowledge
> once into a persistent artifact and keeps it current, so the synthesis, cross-references, and
> contradiction flags already exist before you ask.

## How it relates to other ideas

- **Improved on by:** [[llm-wiki-pattern]].
- **Navigation alternative:** [[index-and-log|index-first navigation]] replaces embedding-based
  retrieval at moderate scale (~100 sources, hundreds of pages), per the seed source.
- **Example systems:** [[notebooklm]], ChatGPT file uploads.

## Open questions

- At what scale does index-first navigation need to be supplemented by real search ([[qmd]]) — i.e.,
  where does the wiki start to need RAG-like tooling again?

## Sources

- [[llm-wiki-pattern-source]]
