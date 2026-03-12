# 24K Scrum: AI-Era Development Framework

> Agile Scrum + SDLC + Golden Circle, rebuilt for teams where humans write specs and AI writes code.

**"Designers discover continuously. Specs define precisely. AI builds rapidly. Humans validate relentlessly."**

---

## Why This Framework Exists

The speed of AI-generated code has outpaced the speed of spec writing. Teams can now generate working software in hours — but only if the spec is clear. Unclear specs produce fast garbage.

The bottleneck in modern software development is no longer coding capacity. It is **clarity**: knowing exactly what to build, why it matters, and how it should work. This framework is designed for that reality.

24K Scrum combines three proven methodologies — **Agile Scrum**, **SDLC**, and **Simon Sinek's Golden Circle (Why/What/How)** — and rebuilds them for AI-augmented teams where:

- **Specifications are the primary deliverable**, not code
- **Prototypes are disposable** — built to learn, then thrown away
- **AI amplifies every role** — one human with AI tools can carry the load of two to three traditional roles
- **Smaller teams move faster** — a 4-person AI-augmented team outperforms a 10-person traditional team when specs are tight

---

## What Is Different From Traditional Scrum

| Dimension | Traditional Scrum | 24K AI-Era Framework |
|---|---|---|
| Primary bottleneck | Developer execution capacity | Spec clarity and user validation |
| Design role | Creates designs before dev starts | Runs continuous Discovery Loop, always ahead of dev |
| Prototyping | Optional, may feed into design phase | Mandatory, continuous, explicitly disposable |
| Code origin | Humans write code | AI generates from spec, humans review |
| Spec quality | Nice-to-have, refined during grooming | Hard gate: Level 4 spec required before sprint entry |
| QA | Separate phase after development | Embedded in spec (acceptance criteria) and developer workflow |
| Team size ideal | 5–9 humans | 2–8 humans + AI tools (sweet spot: 4–6) |
| Scaling model | Add humans | Add AI tools first, then humans at judgment bottlenecks |
| Ticket format | User story + acceptance criteria | Full Golden Circle (Why/What/How) with Spec Level gate |
| Prototype fate | May become production code | Always thrown away |
| Retro focus | What went well / what to improve | Where did spec quality affect AI build velocity? |

---

## How The Framework Flows: The Two-Loop Model

The 24K Framework runs on two parallel loops:

```
┌─────────────────────────────────────────────────────────────┐
│                    DISCOVERY LOOP                           │
│            (continuous, designer-led)                       │
│                                                             │
│  Hypothesis → Vibe-Code Prototype → User Testing            │
│       → Behavioral Evidence → Refine Spec or Pivot          │
│       → Promote to Backlog → Throw Away Prototype           │
│                                                             │
│  Runs 1–2 sprints AHEAD of the Development Loop             │
└──────────────────────┬──────────────────────────────────────┘
                       │ Validated Specs (Level 4)
                       ▼
┌─────────────────────────────────────────────────────────────┐
│                   DEVELOPMENT LOOP                          │
│              (sprint-based, spec-fed)                       │
│                                                             │
│  Sprint Planning → AI-Assisted Build → Human Review         │
│       → QA Validation → Ship → Production Insights          │
│                                                             │
│  Production insights feed back into the Discovery Loop      │
└─────────────────────────────────────────────────────────────┘
```

The **Discovery Loop** is where uncertainty is resolved. The **Development Loop** is where certainty is executed. The handoff between them is a **validated spec** — a Level 4 Golden Circle ticket with complete Why, What, and How.

---

## Who This Is For

- **Small, AI-augmented product teams** (2–8 humans)
- **Solo founders** with AI assistance
- **Established teams** transitioning from traditional Scrum to AI-assisted development

---

## Quick Start

| If you are... | Start with |
|---|---|
| New to the framework | [Philosophy](docs/00_philosophy.md) |
| A designer | [The Discovery Loop](docs/02_discovery.md) |
| A developer | [Specs](docs/03_specs.md) + [Development](docs/05_development.md) |
| A product owner | [Specs](docs/03_specs.md) + [Ceremonies](docs/04_ceremonies.md) |
| Setting up team process | [Ceremonies](docs/04_ceremonies.md) + [Team Scaling](docs/07_team_scaling.md) |
| Choosing tools | [Tools](docs/08_tools.md) |

---

## Full Documentation

| # | Document | Description |
|---|---|---|
| 00 | [Philosophy](docs/00_philosophy.md) | Why this framework exists; core principles; the Golden Circle at product level |
| 01 | [Roles](docs/01_roles.md) | AI-augmented roles; what humans own vs. what AI handles; role combining |
| 02 | [Discovery Loop](docs/02_discovery.md) | Continuous vibe-coded prototyping; user feedback; prototype-to-spec handoff |
| 03 | [Spec-Driven Development](docs/03_specs.md) | Golden Circle ticket format; Spec Levels 0–4; spec quality gates |
| 04 | [Ceremonies](docs/04_ceremonies.md) | All meetings: Discovery Loop ceremonies, Development Loop ceremonies |
| 05 | [AI-Assisted Development](docs/05_development.md) | Building from spec; the AI generation cycle; Definition of Done |
| 06 | [Quality](docs/06_quality.md) | Quality in the AI era; testing strategy; QA role transformation |
| 07 | [Team Scaling](docs/07_team_scaling.md) | Solo to full team configurations; when to add humans vs. AI tools |
| 08 | [Tools](docs/08_tools.md) | Tool stack for discovery, spec management, AI development, and CI/CD |

---

## Core Concepts at a Glance

### The Golden Circle (Why / What / How)

Every ticket, every epic, and the product itself is defined through three layers:

- **Why**: The purpose — what user pain or opportunity does this address?
- **What**: The deliverable — what will exist when this is done? (acceptance criteria, out-of-scope)
- **How**: The approach — architecture, patterns, AI prompting hints, testing strategy

### Spec Levels

Tickets progress through quality levels before entering a sprint:

| Level | Contains | Status |
|---|---|---|
| 0 | Idea only | Needs Discovery Loop work |
| 1 | Why defined | Not ready for development |
| 2 | Why + What defined | Not ready for development |
| 3 | Why + What + How skeleton | Ready for Tech Design Session |
| 4 | Complete Golden Circle + acceptance criteria | **Ready for sprint** |

Only Level 4 specs enter Sprint Planning. This is a hard gate, not a suggestion.

### The Prototype Death Rule

Every prototype has an end date: the moment user testing sessions are complete. No prototype code ever enters a production repository. The Designer's validated spec and UX reference are the only artifacts that move forward. Prototype code is thrown away — always.

---

*This framework is under active development. Previous versions are archived in `docs/archive/v1/`.*
