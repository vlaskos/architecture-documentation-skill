# Stakeholders, concerns, viewpoints, and views

This is the core vocabulary from ISO/IEC/IEEE 42010, in plain terms, with how to apply it.

## The four words

- **Stakeholder** — anyone with a stake in the system: the people who build it, run it, pay for it, audit it, integrate with it, or depend on it. Roles, not names.
- **Concern** — something a stakeholder cares about: a question they need answered, a quality they need assured, a change they need to make. "How do we recover from a region outage?" is a concern. "Where is PII stored and who can read it?" is a concern.
- **Viewpoint** — a reusable *kind* of view. It defines the conventions for one type of representation: which elements appear, which relationships, what notation, and which concerns it is meant to frame. Think of a viewpoint as the template; a view is one filled-in instance.
- **View** — one representation of the architecture, built according to a viewpoint, addressing one or more concerns. A view is usually one or more diagrams plus the prose that makes them readable.

The relationship is simple: **stakeholders have concerns; a viewpoint frames a set of concerns; a view (built per a viewpoint) addresses those concerns for the system at hand.**

## Why start from concerns

The common mistake is to start from diagrams ("we need a component diagram and a sequence diagram") instead of from the people who will read them. That produces documents that are simultaneously too long (views nobody needs) and incomplete (a concern no view covers).

Instead, make a short table before you draw anything:

| Stakeholder | Concerns | Addressed by view |
|---|---|---|
| New developer | Where does my change go? What depends on what? | Structural view (C4 container + component) |
| Operator / SRE | What runs where? How is it deployed and scaled? | Deployment view |
| Security reviewer | Trust boundaries, data stores, authN/authZ flow | Structural + runtime view, annotated |
| Integrator | What interfaces are exposed and how do I call them? | Interface documentation |
| Product owner | What are the main pieces and what can change cheaply? | System overview + context view |

If a row has no view, you have a gap. If a view maps to no row, you have waste. This table is also the backbone of the review checklist.

## Elements, relationships, and the "same thing in two views" problem

Every view is made of **elements** (the things) and **relationships** (how they connect). The elements in a structural view are units of code; in a deployment view they are runtime nodes and infrastructure; in a runtime view they are active processes or components exchanging messages.

Readers get confused when the *same* real thing appears in two views under two names, or when they cannot tell whether two elements in different views are related. Two habits fix this:

- **Name consistently** across views, and
- **State the mapping explicitly** when a view refines or re-slices another ("each component in the component view runs inside the `api` container shown in the deployment view").

See `view-catalog.md` for the concrete view types and `documentation-template.md` for where the stakeholder/concern table and the cross-view mapping live in the finished document.
