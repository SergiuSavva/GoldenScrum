# Ceremonies: The Meeting Architecture

## 1. Ceremony Philosophy

### 1.1 Meetings Serve the Spec or Serve the Team — Nothing Else

Every ceremony in this framework exists for one of two reasons:
1. To improve spec quality (Discovery Review, Spec Refinement, Tech Design, Sprint Planning)
2. To improve team performance (Daily Sync, Sprint Review, Sprint Retrospective)

If a meeting does neither, it should not exist.

### 1.2 Ceremony Cost Model

Time multiplied by participants equals investment. Every ceremony must have a clear return on that investment. A 90-minute meeting with 6 people costs 9 person-hours — it must produce 9 person-hours of value or more.

### 1.3 Async-First

Most status updates happen asynchronously (Slack, Linear updates, Loom videos). Ceremonies are reserved for **decisions that require real-time discussion** — not for information that could be read.

---

## 2. The Two-Loop Ceremony Structure

### 2.1 Discovery Loop Ceremonies (continuous, designer-led)

| Ceremony | Cadence | Duration | Owner |
|---|---|---|---|
| Discovery Review | Weekly | 30 min | Designer |

### 2.2 Development Loop Ceremonies (sprint-based)

| Ceremony | Cadence | Duration | Owner |
|---|---|---|---|
| Sprint Planning | Per sprint | 60–90 min | Scrum Master |
| Daily Sync | Daily | 15 min | Team |
| Sprint Review | Per sprint | 45–60 min | Product Owner |
| Sprint Retrospective | Per sprint | 45–60 min | Scrum Master |

### 2.3 Bridge Ceremonies (connect both loops)

| Ceremony | Cadence | Duration | Owner |
|---|---|---|---|
| Spec Refinement Session | Bi-weekly | 60–90 min | PO + Scrum Master |
| Tech Design Session | Per ticket (triggered) | 60–90 min | Technical Lead |

---

## 3. Discovery Loop Ceremonies

### 3.1 Discovery Review

**Cadence**: Weekly, 30 minutes
**Owner**: UI/UX Designer
**Participants**: Designer, Product Owner, optional Technical Lead

**Purpose**: Review prototype outputs and user feedback from the past week. Decide which hypotheses to promote, pivot, or kill.

**Agenda**:

| Time | Activity |
|---|---|
| 10 min | What prototypes were tested this week? Show key screens and flows. |
| 10 min | What did users do? Behavioral signals only — not opinions. |
| 10 min | Decisions: Which specs need updating? Which hypotheses are promoted to backlog? Which are killed? |

**Output**: List of spec updates to bring to the next Spec Refinement Session.

**What this replaces**: Ad-hoc design reviews scattered across sprints in traditional Scrum.

---

## 4. Bridge Ceremonies

### 4.1 Spec Refinement Session

**Cadence**: Bi-weekly, 60–90 minutes
**Owner**: Product Owner + Scrum Master co-facilitate
**Participants**: PO, SM, Designer, Technical Lead, 1–2 senior developers

**Purpose**: Advance specs from lower levels to Level 4 (sprint-ready). This is the ceremony where the Discovery Loop's outputs enter the Development Loop's pipeline.

**Agenda**:

| Time | Activity | Spec Level Transition |
|---|---|---|
| 15 min | Review Discovery Loop inputs — spec updates from latest Discovery Review | — |
| 20 min | Promote tickets: review Why + What for tickets at Level 1 | Level 1 → Level 2 |
| 20 min | Add skeleton How to Level 2 tickets | Level 2 → Level 3 |
| 15 min | Spec DoD gate check for Level 3 → Level 4 candidates | Level 3 → Level 4 |
| 10 min | Sprint readiness check: do we have enough Level 4 tickets for next sprint? | — |

**Output**: Updated backlog with correct spec levels. Sprint-ready (Level 4) tickets identified.

**Key distinction**: This is NOT estimation. Estimation happens at Sprint Planning. This ceremony is about spec quality, not effort.

**What this replaces**: Backlog Grooming / Backlog Refinement in traditional Scrum.

### 4.2 Tech Design Session

**Cadence**: As needed — triggered during Spec Refinement when a ticket's How is genuinely complex or uncertain
**Owner**: Technical Lead
**Participants**: Technical Lead, relevant developers, QA, optional Designer

**Trigger**: Any ticket at Level 3 (has skeleton How) where the How section requires significant technical analysis or has multiple viable approaches.

**Purpose**: Complete the How section of the spec in sufficient detail for AI-assisted development, advancing the ticket from Level 3 to Level 4.

**Agenda**:

| Time | Activity |
|---|---|
| 15 min | Walk through the What — confirm everyone understands the deliverable |
| 20 min | Explore solution options — evaluate trade-offs, commit to one approach |
| 25 min | Complete the How section (component map, data model, API contracts, AI prompting hints) |
| 10 min | AI Execution Readiness Check: Can a developer hand this How to an AI tool and get a useful first draft? |
| 10 min | Confirm the ticket advances to Level 4 |

**Output**: Completed How section written into the ticket spec.

**Key difference from traditional Technical Design Workshop**: The session ends with a **written spec**, not a verbal agreement. If it's not written in the ticket, it didn't happen.

**AI Execution Readiness Check**:
- [ ] Does the How reference existing code patterns the AI should follow?
- [ ] Are data shapes and types specified?
- [ ] Are the top 3 edge cases listed?
- [ ] Are explicit non-goals stated (what this ticket does NOT do)?
- [ ] Can a developer hand this How directly to an AI pair and get a useful first draft?

---

## 5. Development Loop Ceremonies

### 5.1 Sprint Planning

**Cadence**: Every sprint start, 60–90 minutes
**Owner**: Scrum Master facilitates
**Participants**: Entire development team
**Prerequisite**: Sprint backlog contains only Level 4 specs

**Purpose**: Commit to sprint goal, assign ownership, confirm estimates.

**Agenda**:

| Time | Activity |
|---|---|
| 10 min | Sprint goal: what is the one sentence that describes this sprint's value? |
| 30 min | Walk Level 4 tickets: confirm every builder understands the Why/What/How |
| 20 min | Estimate: story points reflect spec confidence + complexity |
| 10 min | Assign ownership: who is the human responsible for each ticket's AI-build cycle? |
| 10 min | Identify dependencies and sequencing |

**What changed**: Planning is fast because all design decisions were made during Spec Refinement and Tech Design Sessions. Sprint Planning is confirmation, not discovery.

**Red flag**: If planning takes more than 90 minutes, the specs are not truly Level 4. Send them back to Spec Refinement.

### 5.2 Daily Sync

**Cadence**: Daily, 15 minutes maximum
**Owner**: Team self-organizes; Scrum Master facilitates if needed
**Participants**: Development team

**Format**: Walking the board — move left to right through the sprint board columns (spec → in-progress → review → done).

**Three questions, reframed for AI-era**:

1. What spec did I work on yesterday, and what AI output did it produce?
2. What am I working on today?
3. Is any spec unclear enough to be blocking AI generation?

**Key change**: Blockers are almost always **spec clarity issues**, not capacity issues. When someone says "I'm blocked," the first question is "What's unclear in the spec?"

### 5.3 Sprint Review

**Cadence**: Every sprint end, 45–60 minutes
**Owner**: Product Owner facilitates
**Participants**: Team + stakeholders

**Purpose**: Validate shipped work against the Golden Circle. Feed insights back to the Discovery Loop.

**Agenda**:

| Time | Activity |
|---|---|
| 5 min | Sprint goal: did we achieve it? |
| 25 min | Demo completed features against their Why/What acceptance criteria |
| 15 min | Stakeholder feedback capture: map feedback to spec implications |
| 10 min | Discovery Loop handoff: which feedback should inform next prototype cycle? |

**Key change**: Sprint Review explicitly feeds the Discovery Loop. Stakeholder reactions and production insights become inputs for the Designer's next hypothesis.

### 5.4 Sprint Retrospective

**Cadence**: Every sprint end, 45–60 minutes
**Owner**: Scrum Master
**Participants**: Entire team

**Three questions, reframed for AI-era**:

1. Where did spec quality help or hurt our AI-build velocity?
2. Where did human judgment add value that AI could not?
3. What one process change would make next sprint's specs better?

**Output**: 1–3 concrete action items, owned by named individuals, with deadlines.

**What to watch for**:
- Recurring spec gaps → improve spec templates or refinement process
- AI generating consistently wrong patterns → update CONVENTIONS.md
- Developers skipping spec review and "just prompting" → spec discipline problem
- Prototype code sneaking into production → enforce the Prototype Death Rule

---

## 6. Ceremonies Eliminated

| Traditional Ceremony | Why It's Gone | Where It Went |
|---|---|---|
| Pre-Refinement Meeting | Redundant when specs have explicit levels | Absorbed into Spec Refinement Session (Why/What review) |
| Separate Backlog Grooming | Overlapped with refinement | Replaced by Spec Refinement Session |
| Standing Technical Design Workshop | Not all tickets need one | Replaced by triggered Tech Design Sessions (per-ticket) |

---

## 7. Quick Reference

| Ceremony | Cadence | Duration | Loop | Key Output |
|---|---|---|---|---|
| Discovery Review | Weekly | 30 min | Discovery | Spec updates for refinement |
| Spec Refinement Session | Bi-weekly | 60–90 min | Bridge | Level 4 specs for sprint |
| Tech Design Session | Per ticket | 60–90 min | Bridge | Written How section |
| Sprint Planning | Per sprint | 60–90 min | Development | Sprint commitment |
| Daily Sync | Daily | 15 min | Development | Blockers surfaced |
| Sprint Review | Per sprint | 45–60 min | Development | Stakeholder feedback → Discovery Loop |
| Sprint Retrospective | Per sprint | 45–60 min | Development | Process improvements |
