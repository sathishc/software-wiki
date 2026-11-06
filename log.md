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

## [2026-11-06] ingest | Architecture Patterns with Python — Harry Percival & Bob Gregory (2020)

Added the source note (`sources/architecture-patterns-with-python.md`, written from
general knowledge and checked against secondary summaries, so unverified against the
text), a people page (`people/percival-gregory.md`), and eight concept pages:
`concepts/repository-pattern.md`, `concepts/service-layer.md`,
`concepts/unit-of-work.md`, `concepts/aggregate.md`, `concepts/domain-events.md`,
`concepts/ports-and-adapters.md`, `concepts/dependency-injection.md`, and
`concepts/cqrs.md`. Added a synthesis section to `pages/architecture.md` and
index entries in `index.md`. No new tags were needed.

## [2026-11-06] lint | Health check before expansion

Reported before mutating. Findings: no orphan pages (every page has at least two inbound
files); no broken relative links in the wiki (only `../sat-wiki/README.md`, a sibling repo
not present in this checkout, and example links inside `CLAUDE.md`); index entries and
files match one-to-one; no page over ~200 lines; every page has frontmatter.
Fixed: six malformed link fragments in `index.md` (Domain-Driven Design, Clean Code,
Robert-Martin, Kent Beck, TDD, Ubiquitous Language); non-canonical topic tags removed from
`concepts/cost-of-delay.md`, `concepts/queueing-and-utilization.md` and
`sources/reinertsen-product-development-flow.md`; Architecture & Design index section
sorted alphabetically.
Not fixed, for your decision: stray emphasis markers in `pages/delivery.md` (11 lines),
`pages/architecture.md` (3), `pages/code-quality.md` (2) and `concepts/dora-metrics.md` (1),
which need a rewrite rather than a mechanical fix; truncated index descriptions ending in an
ellipsis; a stray fragment in `concepts/functional-programming.md` ("two core moves:.");
33 older pages whose `updated` date predates today but whose content may still be correct.

## [2026-11-06] refactor | Expanded 13 concept pages from Lean and Architecture Patterns ingests

Added worked examples, "when not to use it" and "common mistakes" sections to
`concepts/cost-of-delay.md`, `concepts/queueing-and-utilization.md`,
`concepts/batch-size.md`, `concepts/wip-limits.md`, `concepts/littles-law.md`,
`concepts/repository-pattern.md`, `concepts/service-layer.md`, `concepts/unit-of-work.md`,
`concepts/aggregate.md`, `concepts/domain-events.md`, `concepts/ports-and-adapters.md`,
`concepts/dependency-injection.md`, and `concepts/cqrs.md`. Updated their `updated` dates.
