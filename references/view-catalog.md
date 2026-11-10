# A catalogue of view types

Most architecture documentation is built from a small number of view types. They fall into three broad categories by what they describe. Pick the ones your stakeholders' concerns require (see `viewpoints-and-views.md`); you rarely need all of them.

## Three categories

- **Structural / static** — the units the system is built from and how they depend on each other *at design time*. Answers: what are the pieces, who owns what, where does a change go, what are the dependencies.
- **Runtime / behavioural** — what exists and what happens *while the system runs*: processes, threads, services, the messages and calls between them, and the ordering of important interactions. Answers: what talks to what, in what sequence, under what concurrency.
- **Deployment / physical** — how the software maps onto the environment it runs in: machines, containers, networks, regions, managed services. Answers: what runs where, how it scales, where the trust and failure boundaries are.

A small system is well served by one view from each category plus a context diagram and a decision log. Scale up only where risk justifies it.

## The C4 model (structural, at four zoom levels)

The C4 model gives a clean, widely understood way to draw the structural category at increasing detail. Each level zooms into one element of the level above.

1. **System context** — your system as a single box, surrounded by the users and external systems it interacts with. This is the one diagram every stakeholder can read. Draw it first.
2. **Container** — the deployable/runnable units inside your system (web app, API, database, message broker, worker) and how they communicate. "Container" here means a runtime boundary, not specifically Docker.
3. **Component** — the major structural pieces inside one container and their responsibilities and dependencies.
4. **Code** — class/package level. Usually generated on demand from the code rather than hand-maintained; draw it only where it earns its keep.

C4 is deliberately notation-light: boxes with a name, a type, and a one-line responsibility, plus labelled arrows. Always include a key.

## The 4+1 view model (five concurrent perspectives)

The 4+1 model is a complementary way to decide *which* views to write. It names five perspectives, each for a different audience:

- **Logical** — the functional structure: the key abstractions and how responsibilities are divided. (Overlaps the C4 component level.)
- **Process** — concurrency and runtime behaviour: processes, threads, synchronisation, performance and availability concerns. (A runtime/behavioural view.)
- **Development** — the module/package organisation as seen by programmers: source structure, build units, dependencies, ownership. (A structural view aimed at the team.)
- **Physical** — the mapping to hardware and infrastructure. (A deployment view.)
- **Scenarios (the "+1")** — a handful of key use cases walked through the other four views to show they work together and to validate the design. These double as the architecture's acceptance tests.

The value of 4+1 is the reminder that *process*, *development*, and *physical* are distinct concerns that a single "architecture diagram" usually blurs together.

## Behavioural views for sequencing

When ordering or timing *is* the point (a checkout flow, a distributed saga, a retry/backoff protocol, a startup sequence), add a behavioural view. Standard, non-proprietary notations:

- **UML sequence diagrams** — interactions between participants over time. Best for request/response and message flows.
- **UML state machines** — the lifecycle of a stateful element and its transitions.
- **Activity / flow diagrams** — branching and parallel steps in a process.

Use these sparingly and only for the flows that are hard to get right. One well-chosen sequence diagram beats ten that restate the obvious.

## Interface documentation

For anything others integrate with, document the interface as a first-class artefact, separate from the structural views. Capture, per interface:

- its purpose and the element that provides it;
- the operations/resources, their inputs and outputs, and their meaning (not just the syntax);
- error and exception behaviour;
- any quality obligations (rate limits, latency, ordering, idempotency);
- what the interface *requires* from its callers or environment.

Prefer machine-readable interface definitions where they exist (OpenAPI, Protobuf/gRPC, AsyncAPI, GraphQL SDL) and let the prose explain the *semantics* those files cannot.
