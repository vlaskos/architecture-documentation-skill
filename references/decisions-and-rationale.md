# Decisions and rationale (ADRs)

The most valuable part of architecture documentation is the record of *why*. Code shows what the system does now; it cannot show what you rejected, what you traded away, or what would break if someone undoes a choice. That knowledge walks out the door with whoever made the decision unless you write it down.

An **Architecture Decision Record (ADR)** is one short file capturing one significant decision. The format below is the widely used one popularised by Michael Nygard. ADRs are small, immutable, and numbered; you supersede an old one rather than editing it.

## When a decision deserves an ADR

Record a decision if it is **significant and costly to reverse** — it affects the structure, a quality attribute, a key dependency, an interface contract, or the way the team works. Skip the reversible, local choices. A good test: *would a new senior engineer be surprised by this, or want to undo it without knowing the history?* If yes, write the ADR.

## The template

```
# ADR-000N: <short title of the decision>

Status: proposed | accepted | superseded by ADR-000M | deprecated
Date: YYYY-MM-DD

## Context
The forces at play: the problem, the constraints, the requirements, and the
relevant facts. What made a decision necessary now. Written so someone with no
memory of the meeting can understand the situation.

## Decision
The choice, stated in the active voice: "We will ...". One specific decision per
ADR.

## Options considered
The alternatives you weighed and, briefly, why each was not chosen. This is what
stops the decision from being re-litigated every six months.

## Consequences
What becomes easier and what becomes harder as a result — both the good and the
bad. Include new obligations the decision creates (things the team must now do)
and the conditions under which you would revisit it.
```

## Example

```
# ADR-0007: Use optimistic concurrency for inventory updates

Status: accepted
Date: 2026-03-14

## Context
Multiple services adjust stock levels for the same SKU concurrently. Lost updates
during flash sales caused oversell incidents. We need correctness under high
contention without serialising all writes through one lock.

## Decision
We will use optimistic concurrency control: each inventory row carries a version,
writes are conditional on the version, and the caller retries on conflict.

## Options considered
- Pessimistic row locking — rejected: contention on hot SKUs collapsed throughput
  in load tests.
- A single-writer queue per SKU — rejected: added an operational component and
  tail latency we could not justify for the common low-contention case.

## Consequences
Writers must handle retry and surface a clear error after N attempts. Hot-SKU
behaviour is now bounded by retry budget, which we must monitor. Reads stay
lock-free. Revisit if sustained conflict rates exceed ~10% on any SKU.
```

## Practice

- Keep ADRs in the repository, next to the code, under `docs/adr/` or `docs/decisions/`, one Markdown file per decision, zero-padded and numbered.
- Link them from section 9 of the architecture description (`documentation-template.md`) and from the solution strategy, so the overview and the rationale stay connected.
- Never rewrite an accepted ADR. When a decision changes, write a new ADR and set the old one's status to "superseded by ADR-000M". The trail of superseded decisions *is* the architecture's history.
- Write the ADR when the decision is made, not at the end of the project. The context is clear in your head exactly once.
