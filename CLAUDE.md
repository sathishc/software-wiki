# CLAUDE.md — software-wiki schema

This file is the schema the LLM follows when maintaining this wiki. It is
loaded automatically by Claude Code whenever you work from this directory.
Edit it to change the conventions; the `git-wiki` skill defers to what is
written here.

This wiki follows the [Karpathy LLM-wiki pattern][gist] and is the
software-engineering sibling of [`sat-wiki`](../sat-wiki/README.md). Unlike
traditional RAG (re-derives knowledge per query), the wiki compiles knowledge
once, keeps it current, and pre-builds the cross-references and synthesis.

## Division of labour

The human curates sources and directs the analysis. The LLM summarizes,
cross-references, files pages, and maintains consistency. A good ingest
compounds: one source can touch 10-15 pages.

## The three layers

1. **Raw sources** under `sources/` — immutable; capture them once, never
   rewrite. Corrections go in the wiki pages, never the raw notes.
2. **Wiki pages** under `pages/`, `people/`, `concepts/` — LLM-maintained
   synthesis. This is where knowledge compounds.
3. **Schema** (this file) — the conventions the LLM follows.

## Layout

| path          | purpose                                                        |
|---------------|----------------------------------------------------------------|
| `index.md`    | content catalog, grouped by category. Update on every ingest.  |
| `log.md`      | append-only log. Prefix: `## [YYYY-MM-DD] <op> \\| <title>`. |
| `pages/`      | Maps of Content — curated domain maps, not reference pages.    |
| `people/`     | one file per thinker/author, kebab-case (e.g. `martin-fowler.md`). |
| `concepts/`   | one file per concept, principle, or pattern.                   |
| `sources/`    | raw source notes (books, essays, articles). Immutable.         |
| `assets/`     | images/diagrams referenced by pages.                           |

## Page format

Every wiki page (people/concepts/pages) begins with YAML frontmatter:

```yaml
---
title: Human-readable title
tags: [tag1, tag2]
created: YYYY-MM-DD
updated: YYYY-MM-DD
sources: [sources/<file>.md, ...]
layout: default
parent: People        # or Concepts / Pages / Sources
---
```

The body is standard markdown. Link to other wiki pages with **relative
paths**, e.g. `[Martin Fowler](../people/martin-fowler.md)` or
`[Refactoring](./refactoring.md)`. Link **every** mention of an entity or
concept that has its own page — first occurrence at minimum, ideally every
occurrence. Isolated pages are invisible; every page should link to at least
2 other pages and be linked from at least 2.

## Tags

Use a consistent, lowercase, hyphenated tag set. Prefer existing tags; add a
new tag only if it names a real sub-domain and add it to the index of tags
below. A loose canonical set for this wiki:

- **Code quality:** `dry`, `kiss`, `yagni`, `solid`, `refactoring`, `code-smells`, `technical-debt`, `clean-code`, `simplicity`, `code-quality`, `legacy-code`
- **Testing:** `testing`, `unit-testing`, `tdd`, `bdd`, `quality`, `xp`, `test-pyramid`
- **Architecture:** `design-patterns`, `architecture`, `domain-driven-design`, `microservices`, `monolith`, `api-design`, `functional-programming`, `bounded-context`, `ubiquitous-language`, `modeling`, `oop`
- **Delivery:** `ci-cd`, `devops`, `dora`, `observability`, `deployment`, `delivery`, `agile`
- **Culture:** `code-review`, `craftsmanship`, `philosophy`
- **Meta:** `person`, `moc`, `comparison`

## Log format

`log.md` is append-only. Every entry starts with a level-2 heading:

```
## [YYYY-MM-DD] <op> | <title>
```

where `<op>` is one of `setup`, `ingest`, `query`, `lint`, `refactor`,
`create`. The body is a short note describing what changed and which files
were touched. Keep it grep-friendly:

```sh
grep '^## \[2026-09' log.md        # everything from September 2026
grep 'ingest |' log.md              # every ingest
```

## Index format

`index.md` is organized by category (Pages / People / Concepts / Sources).
Each entry is a single line: link, short description, optional tags.

```markdown
## Concepts
- [Refactoring](concepts/refactoring.md) — restructuring code without changing
  its behaviour. Tags: `refactoring`, `code-quality`.
```

Keep entries roughly alphabetical within a category. When a category exceeds
~40 entries, split it into sub-sections by theme.

## Search

This wiki is intended to be indexed by [`qmd`][qmd]. Prefer `qmd` over raw
grep for queries:

```sh
qmd query   "<natural-language question>"   # hybrid, best quality
qmd search  "keyword"                       # BM25, fast
qmd get     "concepts/refactoring.md"       # retrieve a page
qmd embed                                   # re-embed after edits
```

After any write to the wiki, run `qmd embed` so new content is searchable.

## Operations

- **create** — initialize the structure (this wiki's bootstrap).
- **ingest** — save a raw source under `sources/`, then create/update the
  related people/concepts/pages, update `index.md`, append to `log.md`,
  commit, and `qmd embed`.
- **query** — read `index.md`, run `qmd query`, synthesize an answer citing
  the wiki pages. Append a one-line `query` entry to `log.md`. File novel
  findings back as new pages (the compounding step).
- **lint** — health check: stale `updated` dates, orphan pages (no inbound
  links), broken relative links, index drift, missing cross-references,
  contradictions. Report before mutating.

## Page thresholds

- **Create a page** when an entity/concept is central to a source or appears
  across 2+ sources.
- **Add to an existing page** when a source mentions something already covered.
- **Don't create a page** for passing mentions or out-of-domain trivia.
- **Split a page** when it exceeds ~200 lines; **archive** fully-superseded
  pages into `_archive/` and remove them from the index.

## Maps of Content (`pages/`)

Pages are navigational synthesis — a curated map of a domain that pulls
together the related concepts and people, with a sequencing/table of contents,
a "how these fit together" synthesis, and cross-framework connections. They
are not reference pages (that's the `concepts/` job) and not raw notes.

[carpathy-wiki]: https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f
[gist]: https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f
[qmd]: https://github.com/tobi/qmd
