# A documentation template

A complete architecture description needs more than views; it needs the orientation that makes the views usable. The structure below follows the spirit of the arc42 template (Creative Commons), adapted and reworded. Treat it as a menu: include the sections your system's risk and audience justify, and drop the rest. A small system might use only sections 1, 3, 5, 7, and 9.

Keep each section short and link outward to detail (ADRs, interface specs, code) rather than inlining everything.

## 1. Introduction and goals
What the system is for, in a paragraph. The top functional requirements. The **top quality goals** (the three to five quality attributes that actually shape the architecture, e.g. "p95 latency under 300 ms", "survive a single-AZ failure", "new tenant onboarded in a day"). The key stakeholders and their concerns (the table from `viewpoints-and-views.md` lives here).

## 2. Constraints
The things that are fixed and not up for architectural debate: mandated technologies, regulatory requirements, deadlines, team/skill limits, existing systems you must integrate with. Note why each is a constraint.

## 3. Context and scope
The system as one box and its environment: users, external systems, and the data that crosses the boundary (business context), plus the technical interfaces and protocols at the edge (technical context). This is the C4 **system context** diagram plus a short table of external dependencies. State clearly what is *in* scope and what is *out*.

## 4. Solution strategy
The handful of fundamental decisions that set the shape of everything else: the overall decomposition approach, the key technologies and why, how the top quality goals are met at a high level. One page. Each item here should point to an ADR (section 9) for the full rationale.

## 5. Building-block view (structural)
The static decomposition, top-down. Start with the C4 **container** level, then zoom into the containers that need it at the **component** level. For each building block give a name, a responsibility (one line), and its important dependencies. This is the view a new developer opens first.

## 6. Runtime view (behavioural)
How the building blocks collaborate for the important scenarios: the key flows, as sequence or activity diagrams, with a sentence of setup each. Cover the flows that are complex, risky, or central, not every operation.

## 7. Deployment view (physical)
How the software maps to infrastructure: nodes, containers, networks, regions, managed services, and the mapping of building blocks onto them. Mark trust boundaries and failure domains. This is the operator's and security reviewer's primary view.

## 8. Cross-cutting concepts
The patterns and rules that apply across many building blocks: the domain model, persistence approach, error handling, logging/observability, security model, internationalisation, and any shared conventions. Documenting these once here keeps them out of every individual view.

## 9. Architecture decisions
The log of significant decisions, each as an ADR (see `decisions-and-rationale.md`). This is the *why* of the whole document and the section future maintainers will thank you for.

## 10. Quality requirements and scenarios
The quality goals from section 1, made concrete as testable scenarios (a stimulus, the conditions, and a measurable response). This turns vague words like "scalable" into things you can verify. A simple tree that groups scenarios by quality attribute and ranks them by importance helps readers see what the architecture is optimised for.

## 11. Risks and technical debt
The known weak spots: risks you are carrying, debt you took on deliberately, and areas you are unsure about. Writing these down is a sign of a mature document, not a weak one.

## 12. Glossary
Define every domain term and every acronym the first time a reader might stumble. A shared glossary prevents the most common and most expensive documentation failure: two people using the same word for different things.

---

## Orientation every document needs regardless of sections used

- **A reading guide** — one or two sentences telling each kind of reader where to start.
- **A key on every diagram** — what the shapes, lines, and colours mean.
- **Consistent element names** across views, and an explicit note wherever one view refines or re-slices another.
- **A "last reviewed" date and an owner** — so readers know how much to trust it and whom to ask.
