# How the frameworks relate

The standards and models this skill draws on are not competitors; they operate at different layers and compose well. This note shows how they fit together so you can mix them without confusion.

## What each one gives you

| Framework | Layer | What it provides | Licensing |
|---|---|---|---|
| ISO/IEC/IEEE 42010 | Meta / vocabulary | The concepts and their relationships: stakeholder, concern, viewpoint, view, architecture decision, rationale. It says *what an architecture description is made of*, not what to draw. | International standard (purchasable); concepts are freely usable |
| arc42 | Document structure | A 12-section skeleton for a complete architecture description. | Creative Commons |
| C4 model | Structural notation | Four zoom levels (context, container, component, code) for drawing the static structure. | Free to use |
| 4+1 view model | View selection | Five perspectives (logical, process, development, physical, scenarios) reminding you which concerns to cover. | Published model, freely usable |
| ADRs | Decision capture | A one-file-per-decision format for recording rationale. | Open convention |

## How they stack

- **42010 is the frame.** Its vocabulary describes everything the others produce. A C4 container diagram *is* a view; the "operator" is a stakeholder; "survive an AZ failure" is a concern; the choice of event sourcing is an architecture decision with rationale. You do not "draw 42010" — you use its words to stay precise.
- **arc42 is where the output lives.** Its sections are the document; the views and ADRs slot into specific sections (structural view → building-block section, decisions → section 9). See `documentation-template.md`.
- **C4 and 4+1 populate the view sections.** They are two lenses on the same need — "which views do I write, and how do I draw them?". C4 answers it for structure, bottom-up by zoom level; 4+1 answers it by audience/perspective. They overlap cleanly: C4's container/component levels are the 4+1 *logical* and *development* views; a C4 deployment diagram is the *physical* view; 4+1's *process* perspective is your runtime/behavioural view; 4+1's *scenarios* are your runtime flows.
- **ADRs are orthogonal.** They capture *why* and are referenced from every other part. They are not a view.

## A practical default

For a typical service, you do not need all of this. A solid, standards-grounded default is:

1. A C4 **system context** and **container** diagram (structure), each with a key.
2. One or two **runtime** sequence diagrams for the flows that matter.
3. A **deployment** diagram marking trust and failure boundaries.
4. A short **quality-scenarios** list making the top quality goals testable.
5. A growing set of **ADRs**.
6. A one-page **overview** and a **glossary** tying it together.

Reach for the fuller arc42 structure and additional 4+1 perspectives only when the system's size or risk earns the extra pages.
