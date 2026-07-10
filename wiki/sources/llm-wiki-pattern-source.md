---
type: source
title: "LLM Wiki — A pattern for building personal knowledge bases using LLMs"
author: "Andrej Karpathy"
source_type: gist
url: ""
raw: "[[raw/karpathy-llm-wiki-gist]]"
date: 2026-07-10
ingested: 2026-07-10
tags: [llm-wiki, knowledge-management, meta]
---

# LLM Wiki — A pattern for building personal knowledge bases using LLMs

> [!info] Source
> **Author:** [[andrej-karpathy]] · **Type:** gist / idea file · **Raw:** [[raw/karpathy-llm-wiki-gist]]
> This is the **seed source** of this vault — the document describing the very pattern this vault implements.

## Summary

An "idea file" meant to be handed to an LLM agent so it can help you instantiate a personal knowledge
base. The central move: instead of doing [[rag|RAG]] (retrieving raw chunks and re-deriving answers on
every query), have the LLM **incrementally build and maintain a persistent, interlinked wiki** of
markdown files that sits between you and your raw sources. Knowledge is **compiled once and kept
current**, so the wiki becomes a **compounding artifact** — cross-references, contradiction flags, and
synthesis already in place before you ask.

The design rests on the [[three-layer-architecture]] (raw sources → wiki → schema), three
[[wiki-operations|operations]] (ingest, query, lint), and two navigation files ([[index-and-log|index & log]]).
The human curates and questions; the LLM does all the bookkeeping. Its spiritual ancestor is Vannevar
Bush's [[memex]]; its enabling difference is that the LLM, unlike a human, never tires of maintenance.

## Key claims

- **RAG re-derives knowledge every query; a wiki accumulates it.** The wiki is a persistent, compounding artifact — see [[llm-wiki-pattern]] vs [[rag]].
- **The LLM writes and maintains the wiki; the human never (or rarely) does.** Human = sourcing, exploration, good questions. LLM = summarizing, cross-referencing, filing, bookkeeping.
- **A single ingest commonly touches 10–15 pages.** Bookkeeping at that scale is exactly what LLMs are good at and humans abandon.
- **The [[wiki-operations#Schema|schema file]] (CLAUDE.md / AGENTS.md) is the key config** — it makes the LLM a disciplined maintainer rather than a chatbot, and is co-evolved over time.
- **Good query answers should be filed back into the wiki** so explorations compound like ingested sources.
- **Index-first navigation replaces embedding RAG at moderate scale** (~100 sources, hundreds of pages).
- Workflow metaphor: **Obsidian is the IDE, the LLM is the programmer, the wiki is the codebase.**

## Notable quotes

> "The wiki is a persistent, compounding artifact."

> "Obsidian is the IDE; the LLM is the programmer; the wiki is the codebase."

> "LLMs don't get bored, don't forget to update a cross-reference, and can touch 15 files in one pass."

> "The human's job is to curate sources, direct the analysis, ask good questions, and think about what it all means. The LLM's job is everything else."

## Entities & concepts touched

- **Entities:** [[andrej-karpathy]], [[obsidian]], [[qmd]], [[vannevar-bush]] — plus red links to fill later: [[dataview]], [[marp]], [[obsidian-web-clipper]], [[notebooklm]], [[tolkien-gateway]]
- **Concepts:** [[llm-wiki-pattern]], [[rag]], [[three-layer-architecture]], [[wiki-operations]], [[index-and-log]], [[memex]]

## Open questions / follow-ups

- At what scale does index-first navigation break down and warrant [[qmd]] or a custom search tool?
- Best practice for batch-ingest with less supervision vs. one-at-a-time?
- How to structure image-heavy sources given LLMs can't read inline images in one pass?
