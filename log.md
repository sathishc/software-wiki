# Log

> Append-only record of every wiki action.
> Format: `## [YYYY-MM-DD] <op> | <title>`
> Ops: setup, create, ingest, query, lint, refactor.
> Rotate to `log-YYYY.md` once past ~500 entries.

## [2026-09-25] setup | software-wiki initialized

Created the software-engineering sibling of `sat-wiki` at
`workspace/wiki/software-wiki/`. Structure: `pages/`, `people/`, `concepts/`,
`sources/`, `assets/`, plus `CLAUDE.md` (schema), `index.md`, `log.md`,
`README.md`, Jekyll config (`just-the-docs`), `Gemfile`, `.gitignore`, and the
four section-index nav files. Seeded with an initial corpus: Maps of Content,
canonical people, core concepts, and raw source notes (see subsequent
ingest entries).

## [2026-09-25] ingest | Initial software-engineering corpus (Fowler, Martin, Beck, Evans, Feathers, GoF, Cunningham, DORA)

Seeded the wiki with a canonical, cross-referenced corpus: 4 Maps of Content
(`pages/code-quality.md`, `pages/testing.md`, `pages/architecture.md`,
`pages/delivery.md`), 5 people (Fowler, Martin, Beck, Evans, Feathers), 20
concepts (SOLID, DRY, KISS, YAGNI, refactoring, code smells, technical debt,
clean code, TDD, unit testing, test pyramid, XP, design patterns, DDD, bounded
context, ubiquitous language, monolith, microservices, API design, CI/CD, DORA,
observability, code review, functional programming), and 7 raw source notes.
All pages link via relative paths; root index generated in sat-wiki style.

## [2026-09-25] lint | First health check — link style, tags, indices

Ran the lint pass: converted all ~200 `[[wikilinks]]` to relative-path markdown
links (house style, sat-wiki parity); fixed 6 mangled link targets
(`Technical-debt` casing, `functional-programming`/`xp` missing pages created,
two line-wrapped slugs); normalised non-canonical tags (`ert` typos, redundant
`ddd`) and extended the canonical tag set in `CLAUDE.md` with the real
sub-domain tags actually in use; generated the full root `index.md`
(4 pages, 5 people, 20 concepts, 7 sources); aligned `Gemfile`/`_config.yml`
with the sat-wiki family (github-pages + cayman); git initialised and first
commit made.

## [2026-11-06] lint | Pre-ingest analysis of coverage and link health

Reviewed the wiki before ingesting new material: 4 Maps of Content, 5 people,
20 concepts, 7 sources. No pages covered economics, queueing, or flow as
subjects. Link check found no orphans and no broken relative links in the
existing corpus. Pre-existing issues were reported but not changed: malformed
link syntax in `index.md` (Domain-Driven Design, Clean Code, Robert-Martin and
Kent Beck entries) and stray emphasis markers in several pages. Recorded in
`pages/lean-product-development.md` for a separate cleanup.

## [2026-11-06] ingest | The Principles of Product Development Flow — Donald G. Reinertsen (2009)

Added the Reinertsen source note (`sources/reinertsen-product-development-flow.md`,
compiled from secondary summaries, so principle codes are unverified), a
person page (`people/donald-reinertsen.md`), a Maps of Content page
(`pages/lean-product-development.md`, which also holds the coverage analysis),
and five concept pages: `concepts/cost-of-delay.md`, `concepts/queueing-and-utilization.md`,
`concepts/batch-size.md`, `concepts/wip-limits.md`, `concepts/littles-law.md`.
Updated `index.md` (new Lean & Flow section and entries), `pages/delivery.md`
(related-maps link), and `CLAUDE.md` (new `lean`, `flow`, `economics`,
`queueing` tags).
