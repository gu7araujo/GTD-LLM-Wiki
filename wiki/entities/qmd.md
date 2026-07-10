---
type: entity
entity_type: tool
tags: [llm-wiki, tooling, search]
created: 2026-07-10
updated: 2026-07-10
sources: ["[[llm-wiki-pattern-source]]"]
---

# qmd

_An optional local search engine for markdown files — the recommended way to add real search over the
wiki once it outgrows [[index-and-log|index-first navigation]]._

## Overview

qmd (https://github.com/tobi/qmd) is a local, on-device search engine for markdown with hybrid
BM25 + vector search and LLM re-ranking. It ships both a **CLI** (the LLM can shell out to it) and an
**MCP server** (the LLM can use it as a native tool). Presented in the seed source as the obvious first
CLI tool to add as a wiki grows.

## Key facts

- Hybrid **BM25 + vector** search with **LLM re-ranking**, fully on-device.
- Two interfaces: **CLI** and **MCP server**.
- **Optional and scale-gated:** at small scale the [[index-and-log|index file]] is enough; qmd (or a
  simpler home-grown script) becomes worthwhile as page count grows.

## Relationships

- Supplements → [[index-and-log]] when index-first navigation stops scaling.
- An alternative to embedding-based → [[rag]] infrastructure, kept local.
- Operates over the `wiki/` layer of the [[three-layer-architecture]].

## Sources

- [[llm-wiki-pattern-source]]
