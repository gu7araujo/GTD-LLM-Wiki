---
type: entity
entity_type: tool
tags: [llm-wiki, tooling, obsidian]
created: 2026-07-10
updated: 2026-07-10
sources: ["[[llm-wiki-pattern-source]]"]
---

# Obsidian

_The markdown knowledge-base app used as the front-end for this wiki — "the IDE" in the
[[llm-wiki-pattern|LLM Wiki]] metaphor. This vault is an Obsidian vault._

## Overview

Obsidian stores notes as plain markdown files with `[[wikilinks]]`, a graph view, and a plugin
ecosystem. In the LLM Wiki workflow the human keeps Obsidian open on one side and the LLM agent on the
other: the LLM edits pages, the human browses the results live — following links, checking the graph,
reading updated pages.

## Key facts / features used

- **Wikilinks & backlinks** — the `[[page]]` cross-references that hold the wiki together.
- **Graph view** — best way to see the wiki's shape: hubs, clusters, and orphan pages.
- **[[obsidian-web-clipper|Web Clipper]]** — browser extension converting web articles to markdown into `raw/`.
- **Attachment download** — hotkey to pull a clipped article's images into `raw/assets/` for local viewing.
- **[[dataview|Dataview]]** — queries YAML frontmatter into dynamic tables (also core **Bases**).
- **[[marp|Marp]]** — markdown slide decks generated from wiki content.
- **Canvas** — a spatial output format for query answers.
- Enabled here: templates, graph, backlinks, properties, canvas, bases, daily-notes.

## Relationships

- Front-end for → [[llm-wiki-pattern]] / [[three-layer-architecture]].
- Hosts plugins → [[dataview]], [[marp]], [[obsidian-web-clipper]].
- Alternative/adjacent tooling → [[qmd]] (search over the wiki's markdown).

## Sources

- [[llm-wiki-pattern-source]]
