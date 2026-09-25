# software-wiki

Personal LLM-maintained wiki for **Software Engineering** — the craft of
designing, building, testing, delivering, and maintaining software. Follows the
[Karpathy LLM-wiki pattern](https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f)
and is the software-engineering sibling of [`sat-wiki`](../sat-wiki/README.md).

Maintained with the [`git-wiki`](https://github.com/rarce/git-wiki) Claude Code
skill; the schema lives in [`CLAUDE.md`](CLAUDE.md).

## What's in here

- [`index.md`](index.md) — content catalog
- [`log.md`](log.md) — chronological operations log
- [`pages/`](pages/) — Maps of Content (curated domain maps)
- [`people/`](people/) — one file per thinker / author
- [`concepts/`](concepts/) — one file per concept, principle, or pattern
- [`sources/`](sources/) — raw source notes (immutable)

## Topics covered (so far)

Code quality (DRY, KISS, YAGNI, SOLID, refactoring, code smells, technical
debt), testing (unit testing, TDD, test pyramid), architecture (design
patterns, domain-driven design, microservices vs monolith, API design), and
delivery (CI/CD, DORA metrics, observability, code review).

## Building & browsing

The wiki is a plain directory of markdown — open it in Obsidian, VS Code, or
any editor. It is a Jekyll site (just-the-docs theme):

```sh
gem install jekyll
bundle exec jekyll serve        # http://localhost:4000
```

After editing pages, re-embed for search: `qmd embed`.
