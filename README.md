# architecture-documentation-skill

A Claude skill for writing and reviewing software architecture documentation, based on open standards.

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Claude skill](https://img.shields.io/badge/Claude-skill-8A5CF6.svg)](https://docs.claude.com/en/docs/claude-code/skills)

## What it does

Point Claude at a system and the skill walks through what an architect does when documenting: find out who reads the docs and what they need, pick the views that answer it, draw them in standard notations, and record the decisions with their reasons. It also works as a reviewer. Give it an existing architecture doc and it checks it for gaps and readability against a checklist.

A new developer, an operator and a security reviewer each get the views they need, with a legend and the reasoning behind each decision.

## What it's built on

The method is assembled from open, freely available standards and models:

- **ISO/IEC/IEEE 42010**: the vocabulary of architecture description (stakeholders, concerns, viewpoints, views, decisions, rationale).
- **The C4 model** (Simon Brown): structural diagrams at four zoom levels.
- **The 4+1 view model** (Philippe Kruchten): five complementary perspectives.
- **arc42** (Creative Commons): a complete document structure.
- **Architecture Decision Records** (Michael Nygard's ADR format): rationale, one decision per file.

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
- "Review this architecture doc. What's missing?"

## Further reading

For deeper study:

- ISO/IEC/IEEE 42010:2022, *Software, systems and enterprise — Architecture description.*
- Simon Brown, *The C4 model for visualising software architecture*, [c4model.com](https://c4model.com).
- Philippe Kruchten, "Architectural Blueprints — The 4+1 View Model of Software Architecture," *IEEE Software*, 1995.
- The arc42 template, [arc42.org](https://arc42.org) (Creative Commons).
- Michael Nygard, "Documenting Architecture Decisions," 2011.
- Clements et al., *Documenting Software Architectures: Views and Beyond* (SEI Series, Addison-Wesley), the in-depth reference on architecture views.

## License

[MIT](LICENSE) © 2026 Vladyslav Kosyi
