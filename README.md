# architecture-documentation-skill

A Claude skill for producing and reviewing software architecture documentation, grounded in open standards rather than any single textbook.

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Claude skill](https://img.shields.io/badge/Claude-skill-8A5CF6.svg)](https://docs.claude.com/en/docs/claude-code/skills)

## What it does

Point Claude at a system and this skill walks it through the work an architect does when documenting: figure out **who reads the docs and what they need**, choose the **views** that answer those needs, draw them with proven notations, and **record the decisions and the reasoning behind them** (the part most documentation skips). It also works in reverse, as a reviewer: give it an existing architecture doc and it checks for gaps and unreadability against a concrete checklist.

It produces documentation a new developer, an operator, and a security reviewer can each actually use, instead of a pile of diagrams with no key and no "why".

## What it's built on

The method is assembled from open, freely available standards and models:

- **ISO/IEC/IEEE 42010** — the vocabulary of architecture description (stakeholders, concerns, viewpoints, views, decisions, rationale).
- **The C4 model** (Simon Brown) — structural diagrams at four zoom levels.
- **The 4+1 view model** (Philippe Kruchten) — five complementary perspectives.
- **arc42** (Creative Commons) — a complete document structure.
- **Architecture Decision Records** (Michael Nygard's ADR format) — capturing rationale, one decision per file.

This is an original work. It does not reproduce any copyrighted templates, case studies, or text; it teaches a method built on the open standards above. See [Further reading](#further-reading).

## Structure

```
SKILL.md                              the method and routing
references/
  viewpoints-and-views.md             stakeholders → concerns → viewpoints → views
  view-catalog.md                     the view types (C4, 4+1, behavioural, interfaces)
  documentation-template.md           a full section-by-section skeleton
  decisions-and-rationale.md          ADRs: when, how, with examples
  review-checklist.md                 reviewing docs for gaps and readability
  frameworks-map.md                   how 42010 / arc42 / C4 / 4+1 / ADRs fit together
```

## Install

**Claude Code (CLI):**

```bash
git clone https://github.com/vlaskos/architecture-documentation-skill.git \
  ~/.claude/skills/architecture-documentation-skill
```

Claude Code discovers skills under `~/.claude/skills/`. The skill activates when you ask it to document or review a software architecture.

**Claude Desktop / claude.ai:** zip the skill folder and upload it as a skill in the app's skills/capabilities settings.

## Use it

Ask naturally, for example:

- "Document the architecture of this service for a new developer and an on-call engineer."
- "Which views should I write for this system?"
- "Turn this design decision into an ADR."
- "Review this architecture doc — what's missing?"

## Further reading

The discipline of documenting architecture has a rich literature. For deeper study:

- ISO/IEC/IEEE 42010:2022, *Software, systems and enterprise — Architecture description.*
- Simon Brown, *The C4 model for visualising software architecture* — [c4model.com](https://c4model.com).
- Philippe Kruchten, "Architectural Blueprints — The 4+1 View Model of Software Architecture," *IEEE Software*, 1995.
- The arc42 template — [arc42.org](https://arc42.org) (Creative Commons).
- Michael Nygard, "Documenting Architecture Decisions," 2011.
- Clements et al., *Documenting Software Architectures: Views and Beyond* (SEI Series, Addison-Wesley) — the seminal, in-depth treatment of architecture views.

## License

[MIT](LICENSE) © 2026 Vladyslav Kosyi
