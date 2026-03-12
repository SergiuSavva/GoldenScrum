# Philosophy: Why We Build This Way

## 1. The New Development Reality

### 1.1 What AI Changed

AI can generate working code from a clear specification in minutes. This fundamentally shifts where teams should invest their time:

- **Old world**: Most effort goes into writing and debugging code. Specs are lightweight because humans need flexibility during implementation.
- **New world**: Most effort goes into writing precise specs. Code is generated quickly — but only if the spec is complete, unambiguous, and validated against real user needs.

The constraint is no longer typing speed or developer capacity. The constraint is **human clarity** — knowing exactly what to build and why.

### 1.2 What Did Not Change

- Users still need to want the thing you build
- Bad specs still produce bad products — just faster
- Feedback loops are still the only way to learn what users actually need
- Architectural decisions still require human judgment
- Security, ethics, and edge cases still require human attention

AI accelerates execution. It does not accelerate understanding.

---

## 2. The Golden Circle at Product Level

Simon Sinek's Golden Circle provides the strategic structure for everything in this framework. It operates at three levels: product, epic, and ticket. Here we define the product level.

### 2.1 Why: Purpose Drives Everything

Every product has a core **Why** — the fundamental reason it exists. This is not a feature list. It is a belief about what the world should look like for your users.

The Why is defined once and referenced in every ticket. It acts as a filter: if a feature does not serve the Why, it does not get built.

**Example**: "We believe small teams should be able to ship software as fast as large companies — without the overhead."

### 2.2 What: The Product Promise

The **What** defines the product's promise in terms of outcomes, not features. What measurable change will users experience?

**Example**: "A project management tool that reduces time-from-idea-to-shipped-feature by 50% for teams under 10 people."

### 2.3 How: The Framework Itself

The **How** is this framework: the Discovery Loop, the Development Loop, the spec-driven process, and the AI-augmented team model. The How describes the methods and processes by which the team delivers on the What and serves the Why.

---

## 3. Core Principles

### 3.1 Spec First, Code Second

The spec is the primary deliverable at every stage of this framework. A completed spec represents a working product mentally — all decisions have been made, all edge cases considered, all acceptance criteria defined.

AI can build from a great spec. No one can save a bad one.

**Implications**:
- Spec quality is the primary team performance metric
- A ticket without a complete spec (Level 4) does not enter a sprint
- Time spent improving a spec is never wasted; time spent coding from a bad spec always is

### 3.2 Prototypes Are Disposable

The purpose of a prototype is to extract truth from users — not to build the product. Prototypes are built fast with AI tools, tested with real users, and thrown away.

**Why throw away working code?**

Prototype code is built without error handling, accessibility, security, edge cases, or integration with real data. "Cleaning it up" is consistently more expensive than rebuilding from a clear spec. The discipline of throwing away is architectural hygiene.

**The outputs of a prototype are**:
- Behavioral evidence from user testing
- A refined spec (Why/What) informed by what users actually did
- UX references (screenshots, flows, annotations)

**The outputs are never**:
- Code to be merged
- A "starting point" for production
- Technical architecture decisions

### 3.3 Humans Augmented, Not Replaced

AI expands what one person can accomplish. It does not eliminate the need for human judgment. This framework defines roles by **judgment domains** — the decisions that require human insight — rather than by task lists.

**AI handles**: code generation, test generation, documentation drafting, research synthesis, boilerplate, refactoring suggestions.

**Humans handle**: purpose decisions, user empathy, architectural choices, ethical judgment, spec clarity, team dynamics, knowing when to stop.

One human with AI tools can carry the cognitive load of two to three traditional roles when specs are clear. Role-stacking is a feature of this framework, not a compromise forced by budget.

### 3.4 Discovery Runs Ahead

Design is never a blocker for development. The UI/UX Designer operates in a continuous Discovery Loop that runs 1–2 sprints ahead of the Development Loop.

This means:
- The development team never waits for design
- Specs entering the sprint have already been validated through prototypes
- User feedback is captured before code is written, not after
- The designer is always exploring what comes next while the team builds what's been validated

---

## 4. The Definition of Done Has Changed

### 4.1 Spec DoD (for a ticket to enter development)

- [ ] Why is traceable to the product-level Golden Circle
- [ ] Acceptance criteria are testable and can be automated
- [ ] UX/UI reference is from a validated prototype, not speculation
- [ ] How has been reviewed by Technical Lead
- [ ] Out of scope is explicitly stated
- [ ] Dependencies are identified and sequenced

### 4.2 Build DoD (for a feature to ship)

See [Development](05_development.md) sections 6.2 and 6.3 for the complete Development DoD and Ship DoD checklists. The key gates:

- Code conforms to architecture; all acceptance criteria pass
- AI-generated tests cover happy path; human-written tests cover at least 2 edge cases
- Code reviewed by at least one other human
- QA validation complete; production metrics confirmed post-deployment

---

## 5. What This Framework Deliberately Does Not Include

- **SAFe, LeSS, and other scaling frameworks** — this framework is optimized for small, fast teams. See [Team Scaling](07_team_scaling.md) for scale guidance.
- **Waterfall design phases** — design is continuous, not a phase.
- **Dedicated QA departments** — quality is embedded in every role, not siloed.
- **Prototype-to-production code promotion** — prototypes die. Always.
- **Estimation rituals as performance metrics** — story points reflect spec confidence, not developer speed.
