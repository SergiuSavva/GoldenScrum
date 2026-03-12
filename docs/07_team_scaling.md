# Team Scaling: From Solo to Full Team

## 1. The New Scaling Model

### 1.1 Old Scaling: Add More Humans

Traditional Scrum scales by adding people. More features? Hire more developers. Falling behind? Add more QA. This approach hits diminishing returns quickly — communication overhead grows exponentially with team size.

### 1.2 New Scaling: Add AI Tools Before Adding Humans

In the 24K Framework, the first response to increased workload is to improve AI tooling and spec quality — not to hire. AI handles execution volume; humans handle judgment. Add humans only when **judgment bottlenecks** appear.

### 1.3 The AI-Augmentation Capacity Model

- 1 human + AI ≈ 2–3 traditional humans (in execution capacity)
- The bottleneck is judgment, not execution
- Add humans when judgment bottlenecks appear, not when execution slows

**Signs of a judgment bottleneck** (add humans):
- Spec quality is declining (specs are rushed, missing acceptance criteria)
- Code review quality is dropping (bugs escaping to production)
- Discovery Loop is falling behind Development Loop by 2+ sprints
- One person is combining 3+ roles and dropping balls

**Signs of an execution bottleneck** (improve AI tooling):
- Specs are clear but code generation is slow
- Tests are well-defined but take too long to write
- Documentation is lagging behind features
- Boilerplate is consuming developer time

---

## 2. Solo Configuration (1 Human + AI)

### 2.1 Role Coverage

One person holds all roles: PO + Designer + Tech Lead + Developer + QA. AI augments every function.

### 2.2 How It Works

- **Discovery Loop**: Vibe-code prototypes solo, test with 3–5 users asynchronously (Maze, Lyssna)
- **Spec Writing**: Write Why/What yourself, use AI to draft the How, then review
- **Development**: Full AI-pair workflow — spec → prompt → review → ship
- **Quality**: AI generates tests; you do exploratory testing yourself

### 2.3 Ceremony Adaptations

Canonical cadences are defined in [Ceremonies](04_ceremonies.md). Solo adaptations below are shorter and more frequent:

| Ceremony | Solo Adaptation (vs. canonical) |
|---|---|
| Discovery Review | Weekly self-check: review prototype findings, update specs (30 min) |
| Spec Refinement | Weekly, 30 min (canonical: bi-weekly, 60–90 min) |
| Sprint Planning | Weekly: pick 2–3 Level 4 tickets for the week (15 min) |
| Daily Sync | Daily 5-min check-in with yourself: what's the one thing to ship today? |
| Sprint Review | Bi-weekly: share shipped work with 1–2 trusted users or advisors |
| Sprint Retrospective | Bi-weekly: written reflection — what specs were unclear, what AI output needed most revision? (15 min) |

### 2.4 What Breaks at This Scale

- **User empathy becomes echo chamber**: You are the PO, designer, and developer — you start building for yourself, not users. Mitigate: schedule regular user sessions (at least bi-weekly).
- **No code review**: No one catches your mistakes or AI's. Mitigate: use AI code review tools (CodeRabbit, GitHub Copilot review) as a partial substitute.
- **Burnout**: You own everything. AI creates a false sense of infinite capacity. Mitigate: strict sprint commitments, time-box work days.

---

## 3. Micro Team (2–3 Humans + AI)

### 3.1 Recommended Split

| Person | Roles | Focus |
|---|---|---|
| Person A | PO + Designer | Runs the Discovery Loop full-time |
| Person B | Tech Lead + Developer | Runs the Development Loop full-time |
| Person C (optional) | Developer + QA | Builds + validates |

### 3.2 How the Loops Interact

Person A is always 1–2 sprints ahead, feeding validated specs to Person B. They sync at weekly Spec Refinement (30 min) and Discovery Review (30 min).

### 3.3 Ceremony Adaptations

All ceremonies are shortened from canonical cadences (see [Ceremonies](04_ceremonies.md)). Most communication is async.

| Ceremony | Micro Adaptation (vs. canonical) |
|---|---|
| Discovery Review | Weekly, 20 min — Person A presents to Person B |
| Spec Refinement | Weekly, 30 min (canonical: bi-weekly, 60–90 min) |
| Sprint Planning | Per sprint, 30 min — lightweight commitment |
| Daily Sync | 10 min or async (Slack/Loom update) |
| Sprint Review | Per sprint, 30 min — demo to each other + 1 stakeholder |
| Sprint Retrospective | Per sprint, 20 min — written, then 10 min discussion |

---

## 4. Small Team (4–6 Humans + AI)

### 4.1 Full Role Coverage

This is where the full framework starts operating as designed. Recommended structure:

| Role | People |
|---|---|
| Product Owner | 1 |
| UI/UX Designer | 1 |
| Technical Lead | 1 |
| Developer | 1–2 |
| QA | 1 (can combine with Developer) |

Scrum Master responsibilities can be absorbed by the PO or Tech Lead, or rotated.

### 4.2 Full Framework Mode

All ceremonies run as specified in [Ceremonies](04_ceremonies.md). The Discovery Loop and Development Loop run as separate tracks with the Designer operating independently ahead of the team.

### 4.3 Key Advantage

At this scale, the Discovery Loop and Development Loop truly decouple. The Designer is never blocked by development, and development is never blocked by design.

---

## 5. Standard Team (6–8 Humans + AI)

### 5.1 Full Separation of Roles

| Role | People |
|---|---|
| Product Owner | 1 |
| Scrum Master | 1 (dedicated) |
| UI/UX Designer | 1 |
| Technical Lead | 1 |
| Developer | 2–3 |
| QA | 1 |

### 5.2 Parallel Spec Execution

Multiple developers can work on different Level 4 tickets simultaneously. The Technical Lead coordinates architecture consistency across parallel work streams.

### 5.3 Sub-Tracks for Large Epics

When an epic spans multiple sprints, assign a developer to own the epic end-to-end rather than distributing tickets across the team. This preserves context and reduces handoff overhead.

---

## 6. When to Split into Multiple Teams

### 6.1 Signal: Multiple Product Owners Needed

If the product has distinct areas that require separate vision and priority decisions, split into separate teams — each with their own Discovery Loop and Development Loop.

### 6.2 Signal: Discovery Loop Falling Behind

If the Discovery Loop is more than 2 sprints behind the Development Loop (development is outpacing validated specs), either:
- Add a second Designer to the Discovery Loop, or
- Split the product into two smaller teams with focused scope

### 6.3 Anti-Pattern: Splitting Because Headcount Grew

Do not split teams just because you hired more people. Split when **judgment bottlenecks** require separate decision-making authority. A team of 8 with clear specs and good process outperforms two teams of 4 with coordination overhead.

### 6.4 Coordination Between Teams

When multiple teams exist:
- Each team runs independently with their own loops and ceremonies
- A shared **Spec Refinement Session** (monthly) handles cross-cutting concerns
- Technical Leads sync on architecture consistency weekly (30 min)
- Product Owners align on product-level Golden Circle quarterly
