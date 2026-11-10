---
name: architecture-documentation-skill
description: Produce and review software architecture documentation grounded in open standards — ISO/IEC/IEEE 42010, the arc42 template, the C4 model, the 4+1 view model, and Architecture Decision Records. Use when you need to document a system's architecture, decide which views to write for which stakeholders, structure an architecture description, capture decisions with their rationale, or review existing architecture docs for completeness and clarity.
license: MIT
---

# Documenting software architectures

Architecture documentation exists to answer questions that stakeholders will otherwise ask you in meetings for the lifetime of the system: *How is this put together? Why is it this way? Where do I change X? Will it hold under Y?* Good documentation answers those once, in writing, in a form each reader can actually use.

This skill is a method for producing that documentation, and for reviewing documentation someone else wrote. It is built on open, freely available standards and models, not on any single copyrighted text:

- **ISO/IEC/IEEE 42010** — the international standard for architecture description. It gives the vocabulary used throughout: *stakeholder*, *concern*, *viewpoint*, *view*, *model*, *architecture decision*, *rationale*.
- **The C4 model** (Simon Brown) — a lightweight set of structural diagrams at four zoom levels: context, container, component, code.
- **The 4+1 view model** (Philippe Kruchten) — five concurrent perspectives: logical, process, development, physical, and scenarios that tie them together.
- **arc42** — a Creative-Commons documentation template whose section structure is a practical skeleton for a full architecture description.
- **Architecture Decision Records** (the ADR format popularised by Michael Nygard) — one short file per significant decision.

## The method

Documentation is driven by *who reads it* and *what they need to decide or do*. Work in this order.

1. **Identify stakeholders and their concerns.** List who depends on the architecture (developers, operators, security reviewers, product owners, integrators, auditors) and what each needs the documentation to answer. A concern is a question or quality that matters to someone: "can I deploy this without downtime?", "where does customer data live?", "how do I add a new payment provider?". Concerns determine everything that follows. See `references/viewpoints-and-views.md`.

2. **Select viewpoints that cover the concerns.** A viewpoint is a reusable *kind* of view: the conventions for building one type of representation (what elements it shows, what relationships, what notation). Choose the smallest set of viewpoints that, together, address every important concern. Do not write a view nobody needs. See `references/view-catalog.md`.

3. **Build the views.** Each view is one representation of the system from one viewpoint: a diagram plus the prose that explains it. Most systems need a *structural* view (what the pieces are and how they depend on each other), a *runtime* view (what happens at execution time: processes, flows, interactions), and a *deployment* view (how software maps to infrastructure). Add behavioural views for the parts where timing or sequencing is the whole point. The C4 levels and the 4+1 perspectives are concrete, proven ways to populate these. See `references/view-catalog.md`.

4. **Capture decisions and their rationale.** The single most valuable and most frequently missing part of architecture documentation is *why*. Record each significant decision (the context, the options considered, the choice, and the consequences) as an Architecture Decision Record. Rationale is what lets the next person change the system safely instead of guessing. See `references/decisions-and-rationale.md`.

5. **Assemble the description and add orientation.** A pile of views is not a document. Add the connective tissue: a one-page system overview, a statement of scope and context, a glossary, and an explicit note on how the views relate to each other (the same element seen in two views is the reader's main source of confusion, so resolve it). Use `references/documentation-template.md` for a complete section skeleton.

6. **Review before you ship it.** Run the documentation against `references/review-checklist.md`. The two failure modes are *incompleteness* (a concern no view addresses) and *unreadability* (diagrams without keys, undefined terms, no statement of what the reader is looking at).

## How to use this skill

- Starting from scratch → follow the six steps above, using `references/documentation-template.md` as the target structure.
- Deciding what to write → `references/viewpoints-and-views.md` (concerns → viewpoints) and `references/view-catalog.md` (the catalogue of view types).
- Recording a decision → `references/decisions-and-rationale.md` (ADR format and examples).
- Reviewing existing docs → `references/review-checklist.md`.
- Choosing between frameworks or mapping one onto another → `references/frameworks-map.md`.

## Principles

- **Write for a reader, not for completeness.** Every view, diagram, and paragraph should trace to a stakeholder concern. If you cannot name who needs it, cut it.
- **Every diagram needs a key.** Notation that "looks obvious" is not. State what boxes and lines mean. An unexplained diagram is a guess waiting to go wrong.
- **Record rationale as you go.** Decisions are cheap to capture at the moment you make them and expensive to reconstruct later.
- **Keep it close to the code and keep it current.** Documentation that drifts from reality is worse than none, because people trust it. Prefer a smaller document you will maintain over a large one you will not.
- **Let the system's risk set the depth.** Document the parts where being wrong is expensive in detail; sketch the rest.
