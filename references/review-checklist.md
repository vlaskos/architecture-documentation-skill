# Reviewing architecture documentation

Use this when checking a document before it ships — your own or someone else's. The two things to catch are **gaps** (a concern no view addresses) and **unreadability** (a reader cannot extract what they need). Review for the reader, not for conformance to a template.

## Fit for its readers

- [ ] Every important stakeholder has at least one view or section that answers their main concern. (Check against the stakeholder/concern table.)
- [ ] There is a reading guide telling each kind of reader where to start.
- [ ] Nothing is included that no named reader needs. Cut decoration.
- [ ] The level of detail matches the risk: the expensive-to-get-wrong parts are documented deeply; the rest is sketched.

## Readable on its own

- [ ] Every diagram has a key explaining its shapes, lines, and colours.
- [ ] Every diagram is introduced by prose that says what the reader is looking at and why it matters.
- [ ] All domain terms and acronyms are in the glossary and used consistently.
- [ ] Element names are consistent across views; where one view refines or re-slices another, the mapping is stated explicitly.
- [ ] A reader can trace a single element or flow across the views without guessing.

## Complete where it counts

- [ ] Scope and context are explicit: what the system is and is not responsible for, and everything that crosses its boundary.
- [ ] The top quality goals are stated and made concrete as testable scenarios, not left as adjectives ("fast", "scalable", "secure").
- [ ] Interfaces others depend on are documented, including semantics and error behaviour, not just syntax.
- [ ] Trust boundaries, data stores, and failure domains are visible to the security and operations readers.

## Honest about why and what's weak

- [ ] Significant decisions are recorded as ADRs with their context, the options rejected, and the consequences.
- [ ] Known risks and deliberate technical debt are written down, not hidden.
- [ ] Claims are backed: where the document asserts a quality is met, it points to a scenario, a test, a measurement, or a decision — not an assertion alone.

## Maintainable

- [ ] The document is close to the code (in the repo or linked from it) and carries an owner and a last-reviewed date.
- [ ] It is small enough that the team will actually keep it current. A smaller living document beats a larger stale one.

## Running a review with others

If you review with the stakeholders rather than for them, give each reviewer a concrete task tied to their concern ("as the on-call engineer, find where you'd look during a region outage") instead of asking "any comments?". Task-based review surfaces real gaps; open-ended review surfaces typos.
