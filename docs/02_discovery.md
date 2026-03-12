# The Discovery Loop: Continuous Vibe-Coded Prototyping

## 1. What the Discovery Loop Is

### 1.1 Definition

The Discovery Loop is a **continuous, parallel process** that runs 1–2 sprints ahead of the Development Loop. Its purpose is to convert user uncertainty into validated specs.

While the development team builds what has been validated, the Designer explores what comes next. The two loops run simultaneously but operate independently — the Discovery Loop feeds the Development Loop through validated specs, and the Development Loop feeds the Discovery Loop through production insights.

### 1.2 Goal

Turn hypotheses about user needs into **behavioral evidence** that sharpens specs before a single line of production code is written.

### 1.3 Primary Owner

The UI/UX Designer (see [Roles](01_roles.md) section 2.2). In smaller teams, the Product Owner + Designer combination may run this loop together.

### 1.4 Inputs

- Product-level Why (from [Philosophy](00_philosophy.md))
- Current backlog (ideas at Spec Level 0–1)
- User feedback from production (from Sprint Reviews)
- Stakeholder requests
- Market observations

### 1.5 Outputs

- Validated specs ready to advance to Level 2 (Why + What defined, backed by evidence)
- UX references (annotated Figma files, flow diagrams)
- User testing observations and behavioral evidence
- Design system components for the development team

---

## 2. Vibe-Coded Prototyping

### 2.1 What "Vibe-Coded" Means

Vibe-coded prototyping uses AI tools to generate working UI prototypes from natural language descriptions. The Designer describes what they want to test, and AI generates a functional prototype — not a static mockup, but something users can interact with.

The Designer acts as **director**, not implementer. Speed matters more than code quality. Prototype code is never reviewed, never refactored, never merged. It exists only to put something real in front of users.

### 2.2 Prototype Fidelity Levels

Use the **lowest fidelity** that answers your question:

| Level | What It Is | Build Time | Use When |
|---|---|---|---|
| Concept Sketch | AI-generated wireframe from feature description | 30 minutes | Testing whether users understand a concept at all |
| Interactive Mock | Clickable prototype, real UI but fake data | 2–4 hours | Testing navigation, flow, and interaction patterns |
| Functional Vibe-Code | Working prototype with stubbed backend | 4–8 hours | Testing complex interactions that need real behavior |

**Rule**: If a Concept Sketch can answer your question, do not build an Interactive Mock. Over-investing in prototype fidelity wastes the time advantage that AI gives you.

### 2.3 Tools for Vibe-Coded Prototyping

**Design-to-code**:
- v0.dev (Vercel) — natural language to React UI components
- Bolt.new (StackBlitz) — full-stack prototypes from prompts
- Lovable — AI-generated web apps for rapid prototyping
- Cursor / Windsurf with UI frameworks — for more controlled generation

**Traditional mockup with AI assist**:
- Figma with AI plugins — for design system consistency

**User testing platforms**:
- Maze — unmoderated usability testing
- Lyssna — first-impression and task-based testing
- UserTesting.com — moderated sessions
- Dovetail — AI-assisted research synthesis

### 2.4 The Prototype Death Rule

**Every prototype has an end date**: the moment user testing sessions are complete.

**No prototype code ever enters a production repository.** This rule has no exceptions.

**Why this matters**: Prototypes accumulate the wrong decisions at speed. They are built without error handling, accessibility, security, edge case coverage, or integration with real data. A prototype that "works" is not a product that works.

Teams that skip this discipline — "we already built it, let's just clean it up" — consistently produce worse production code than teams that rebuild from specs. The reasons:

1. **Prototype shortcuts become production debt.** Every hardcoded value, skipped validation, and missing error state must be found and fixed. Finding them takes longer than writing from scratch.
2. **Prototype architecture reflects exploration, not production needs.** The component structure of a prototype reflects the order the designer explored ideas, not the optimal structure for maintenance.
3. **Cleaning up feels faster but is slower.** Developers spend time understanding someone else's throwaway code instead of writing code they understand from a clear spec.

**The handoff is insights and specs, never code.**

---

## 3. The User Feedback Session

### 3.1 Session Design

Every user testing session starts with a **question**, not a prototype. The question determines what you build and what you observe.

Examples of good questions:
- "Do users understand that they can invite team members from the project settings?"
- "Which of these two onboarding flows leads to faster first-project creation?"
- "Do users notice the notification badge, and do they understand what it means?"

Examples of bad questions:
- "Do users like the design?" (opinion, not behavior)
- "Is this easy to use?" (too vague to observe)

### 3.2 Who Participates

**Real users**, not stakeholders, not team members, not the PO's friend. Even 3 users is enough to identify major usability issues. Five users catch approximately 85% of usability problems.

### 3.3 Session Formats

| Format | Duration | Best For |
|---|---|---|
| Moderated usability session | 30–45 min | Complex flows, exploring user mental models |
| Unmoderated task test (Maze, Lyssna) | Async | Validating specific interactions at scale |
| 5-second first impression test | 5 seconds | Testing whether users understand the purpose of a screen |
| A/B variant test | Varies | Comparing two prototype approaches |

### 3.4 What to Capture

Capture **behavioral signals**, not opinions:

- **Do**: "3 out of 5 users clicked the wrong button first"
- **Don't**: "Users said they liked the blue color"
- **Do**: "Users took an average of 45 seconds to find the settings page"
- **Don't**: "Users said the layout was intuitive"

What people do reveals truth. What people say reveals politeness.

### 3.5 Session Frequency

Minimum **one user testing session per sprint** in the Discovery Loop. The Designer should be testing something every week — even if it is a 5-second test on a Concept Sketch.

---

## 4. Converting Feedback into Spec Refinements

### 4.1 The Insight Extraction Process

```
Raw feedback (session recordings, task completion data)
    → Behavioral patterns (what did multiple users do similarly?)
    → Spec implications (what does this mean for the Why, What, or How?)
```

AI can assist with synthesis — clustering feedback, identifying patterns, suggesting spec implications. But the **human judgment** about which insights matter and which are noise is not delegatable.

### 4.2 Updating the Spec

Every insight maps to a specific spec element:

| Insight Type | Spec Impact | Example |
|---|---|---|
| Users don't understand the purpose | Update the **Why** — the problem statement may be wrong | "Users thought this was a reporting tool, not a planning tool" |
| Users can't complete the task | Update the **What** — the deliverable or acceptance criteria need change | "Users expected a confirmation step before submitting" |
| Users find a workaround | Update the **How** — the technical approach should support the natural behavior | "Users copy-pasted instead of using the drag-and-drop" |

### 4.3 When Feedback Invalidates the Why

Sometimes user testing reveals that the fundamental assumption behind a feature is wrong. This is not a failure — this is the Discovery Loop working as intended. The escalation path:

1. Designer identifies that the Why is invalid based on user behavior
2. Designer presents evidence to Product Owner at Discovery Review
3. Product Owner reviews against the product-level Golden Circle
4. Decision: pivot the feature, kill it, or reframe the Why

Better to discover this in a throwaway prototype than in production.

---

## 5. The Discovery Loop Cycle

```
1. HYPOTHESIZE
   What behavior do we want to test?
   What is our assumption about what users need?

2. PROTOTYPE
   Vibe-code a prototype at the lowest fidelity that answers the question
   Time budget: hours, not days

3. TEST
   Put it in front of real users (3–5 is enough)
   Capture behavioral evidence, not opinions

4. ANALYZE
   Extract insights: what did users actually do?
   Map insights to spec implications (Why, What, or How)

5. DECIDE
   → Pivot: the hypothesis was wrong, try a different approach
   → Iterate: partially validated, run another round with refinements
   → Promote: enough evidence to write a refined spec for the backlog

6. HAND OFF (if promoting)
   Write refined What definition for backlog ticket
   Attach UX reference (annotated Figma, not prototype code)
   Present at Discovery Review ceremony

7. THROW AWAY
   Delete the prototype code
   The insights and spec are the deliverable, not the code
```

---

## 6. Discovery Loop Ceremonies

### 6.1 Discovery Review

- **Cadence**: Weekly, 30 minutes
- **Owner**: UI/UX Designer
- **Participants**: Designer, Product Owner, optional Technical Lead
- **Purpose**: Review prototype outputs and user feedback from the past week

**Agenda**:
1. What prototypes were tested this week? (10 min)
2. What did users do? Behavioral signals, not opinions. (10 min)
3. Which specs need updating? Which hypotheses should be promoted, pivoted, or killed? (10 min)

**Output**: List of spec updates to bring to the next Spec Refinement Session.

### 6.2 Spec Refinement Session

See [Ceremonies](04_ceremonies.md) section 4.1 — this ceremony sits at the boundary between the Discovery Loop and the Development Loop.

---

## 7. Discovery Loop Metrics

| Metric | What It Measures | Target |
|---|---|---|
| Prototype cycle time | Idea → user testing session | Under 1 week |
| Spec invalidation rate | How often user feedback significantly changes the spec | 20–40% is healthy (lower means you're not testing risky enough ideas) |
| User insight density | Actionable insights per testing session | 3–5 per session |
| Spec readiness rate | % of backlog items at Level 2+ (have validated What) | > 60% of upcoming sprint candidates |
| Prototype disposal rate | % of prototypes actually thrown away | 100% (this is a discipline metric) |
