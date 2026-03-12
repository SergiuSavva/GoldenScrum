# Spec-Driven Development: The Golden Circle Ticket

## 1. The Spec as Primary Deliverable

### 1.1 Why Specs Matter More Than Code

AI can generate code from a complete spec in minutes. Incomplete specs generate code that looks right but behaves wrong. The math is simple:

- A perfect spec with no code = a potentially shippable product (AI builds it)
- Perfect code with a bad spec = guaranteed rework

In an AI-augmented team, spec quality is the single strongest predictor of project velocity. Every hour spent improving a spec saves multiple hours of AI-generated rework.

### 1.2 The Spec Quality Spectrum

Tickets progress through five quality levels. Only Level 4 enters a sprint.

| Level | Contains | Status | Who Advances It |
|---|---|---|---|
| 0 | Feature idea only | Needs Discovery Loop work | Product Owner |
| 1 | Why defined | Not ready for development | Product Owner |
| 2 | Why + What defined | Not ready for development | PO + Designer |
| 3 | Why + What + How skeleton | Ready for Tech Design Session | Technical Lead |
| 4 | Complete Golden Circle + acceptance criteria + DoD | **Ready for sprint** | Full team at Spec Refinement |

**The Level 4 gate is a hard requirement.** If a ticket is not Level 4, it does not enter Sprint Planning. If Sprint Planning reveals a ticket is not truly Level 4, it goes back to Spec Refinement.

---

## 2. The Golden Circle Ticket Format

### 2.1 Ticket Header

| Field | Description |
|---|---|
| ID | Unique identifier |
| Title | Clear, concise description of the deliverable |
| Spec Level | Current level (0–4) |
| Sprint Target | Target sprint (assigned at Sprint Planning) |
| Story Points | Estimate reflecting spec confidence + complexity |
| Owner | Human responsible for delivery |

### 2.2 WHY Section

The Why answers: **what user pain or opportunity does this address?**

| Field | Description | Owner |
|---|---|---|
| Problem Statement | What specific user problem does this solve? | Product Owner |
| Product Why Alignment | Which element of the product-level Golden Circle does this serve? | Product Owner |
| Business Value | What measurable outcome does completing this produce? | Product Owner |
| User Story | "As [persona] I need [outcome] because [reason]" | Product Owner |

**Quality check**: If the Why reads like a solution ("implement OAuth2"), it is actually a What. Rewrite it as a problem ("users cannot log in without creating yet another account").

### 2.3 WHAT Section

The What answers: **what will exist when this is done?**

| Field | Description | Owner |
|---|---|---|
| Deliverable | Precise description of what will exist when complete | Product Owner |
| Acceptance Criteria | Verifiable conditions in BDD format (Given/When/Then) | PO + QA |
| Out of Scope | Explicit list of what this ticket does NOT include | Product Owner |
| UX/UI Reference | Link to validated prototype artifacts or design components | Designer |
| Non-Functional Requirements | Performance, security, accessibility constraints | Tech Lead |

**Quality check**: Every acceptance criterion must be testable. If you cannot write a test for it, it is too vague.

### 2.4 HOW Section

The How answers: **how will this be built?**

| Field | Description | Owner |
|---|---|---|
| Technical Approach | Architecture decisions, patterns, libraries to use | Technical Lead |
| Component Map | Which files/modules/services are created or modified | Technical Lead |
| Data Model Changes | Schema changes, migrations required | Technical Lead |
| API Contracts | Endpoint definitions, request/response shapes | Technical Lead |
| AI Prompting Hints | Suggested prompt structure for AI code generation | Developer |
| Testing Approach | Unit, integration, E2E tests required | QA + Developer |
| Dependencies | Other tickets that must complete first | Technical Lead |

**Quality check**: Can a developer hand this How section directly to an AI coding assistant and get a useful first draft? If not, the How is under-specified.

### 2.5 Spec DoD Checklist

Before a ticket enters Sprint Planning, it must pass this gate:

- [ ] Why is traceable to the product-level Golden Circle
- [ ] Acceptance criteria are testable (can be automated)
- [ ] UX/UI reference is from a validated prototype, not speculation
- [ ] How has been reviewed by Technical Lead
- [ ] Out of scope is explicitly stated
- [ ] Dependencies are identified and sequenced
- [ ] Story point estimate reflects spec confidence, not just complexity

---

## 3. Spec-Writing Process

### 3.1 Who Writes What

| Golden Circle Layer | First Draft | Refined By | Final Review |
|---|---|---|---|
| Why | Product Owner | PO + Designer (Discovery Loop evidence) | Spec Refinement Session |
| What | Product Owner + Designer | QA (acceptance criteria) | Spec Refinement Session |
| How | Technical Lead | Developer (AI prompting hints) | Tech Design Session |

### 3.2 The Refinement Pipeline

Specs advance through levels via specific ceremonies (see [Ceremonies](04_ceremonies.md)):

```
Stage 1: Raw idea → Level 1 spec
  PO creates ticket with Why defined
  Informed by: Discovery Loop outputs, stakeholder requests, production insights

Stage 2: Level 1 → Level 2 spec
  PO + Designer add What (deliverable, acceptance criteria, UX reference)
  Informed by: validated prototype evidence from Discovery Loop

Stage 3: Level 2 → Level 3 spec
  Spec Refinement Session adds skeleton How (high-level technical approach)
  Gate: if How is complex or uncertain → trigger Tech Design Session

Stage 4: Level 3 → Level 4 spec
  Tech Design Session (if triggered) completes the detailed How
  Spec Refinement Session validates all fields, runs Spec DoD checklist
  Gate: Level 4 spec enters Sprint Planning
```

### 3.3 Common Spec Failure Modes

| Failure | Symptom | Fix |
|---|---|---|
| Why is actually a What | "Implement OAuth2" instead of "Users can't log in easily" | Rewrite as user problem, not solution |
| What has no testable criteria | "The page should look good" | Add Given/When/Then acceptance criteria |
| How is under-specified | AI generates code that misses edge cases | Add component map, data shapes, explicit constraints |
| Implicit scope | Assumptions not written down cause scope creep | Add explicit Out of Scope list |
| No prototype evidence | UX reference is a wireframe, not validated design | Route through Discovery Loop first |

---

## 4. The Golden Circle at Three Levels

The Golden Circle operates at three connected levels. Each level's Why must trace upward:

```
Product Why: "We believe small teams should ship as fast as large companies"
    │
    ├── Epic Why: "Users need frictionless onboarding to start quickly"
    │       │
    │       ├── Ticket Why: "New users drop off at the account creation step"
    │       └── Ticket Why: "Users can't find the getting-started guide"
    │
    └── Epic Why: "Teams need real-time visibility into sprint progress"
            │
            ├── Ticket Why: "Scrum masters have no burndown chart"
            └── Ticket Why: "POs can't see which specs are blocking the sprint"
```

If a ticket's Why cannot trace to the product Why, the ticket should not exist.

---

## 5. Complete Ticket Example

### Ticket: User Onboarding Flow

**Header**

| Field | Value |
|---|---|
| ID | PROD-142 |
| Title | Implement guided onboarding for new users |
| Spec Level | 4 |
| Sprint Target | Sprint 12 |
| Story Points | 8 |
| Owner | Developer A |

**WHY**

- **Problem Statement**: 40% of new users abandon the product within the first 5 minutes because they don't understand how to create their first project.
- **Product Why Alignment**: "Small teams should ship as fast as large companies" — users can't ship if they can't get started.
- **Business Value**: Reduce first-session drop-off from 40% to under 15%.
- **User Story**: As a new user, I need step-by-step guidance through my first project setup because the current blank-slate experience gives me no direction.

**WHAT**

- **Deliverable**: A 4-step guided onboarding flow that walks new users through creating their first project, adding a team member, creating their first ticket, and viewing their board.
- **Acceptance Criteria**:
  - Given a user has just signed up, When they log in for the first time, Then they see the onboarding flow (not the empty dashboard)
  - Given a user is in step 2 of onboarding, When they click "Skip", Then they are taken to the dashboard with a dismissible "Resume onboarding" banner
  - Given a user has completed all 4 steps, When they reach the end, Then they see their populated board with the project they just created
  - Given a user has completed onboarding, When they log in again, Then they see the regular dashboard (onboarding does not repeat)
- **Out of Scope**: Email onboarding sequences, analytics dashboard for onboarding metrics, A/B testing different flows
- **UX/UI Reference**: Validated prototype from Discovery Loop Sprint 10 — [link to Figma with annotations]. User testing showed 4 steps is optimal; 3 steps left users confused, 5 steps caused drop-off.
- **Non-Functional**: Flow must load in under 2 seconds. Must be accessible (WCAG 2.1 AA).

**HOW**

- **Technical Approach**: New `OnboardingFlow` component using the existing step-wizard pattern from `src/components/Wizard`. State tracked in user profile (`onboarding_completed: boolean, onboarding_step: number`).
- **Component Map**:
  - Create: `src/components/Onboarding/OnboardingFlow.tsx`, `src/components/Onboarding/steps/` (4 step components)
  - Modify: `src/pages/Dashboard.tsx` (conditional render), `src/api/users.ts` (onboarding state endpoints)
  - Modify: Database migration for `users.onboarding_completed`, `users.onboarding_step`
- **Data Model Changes**: Add `onboarding_completed` (boolean, default false) and `onboarding_step` (integer, default 0) to users table.
- **API Contracts**: `PATCH /api/users/me/onboarding` with body `{ step: number, completed: boolean }`. Returns updated user object.
- **AI Prompting Hints**: "Use the existing Wizard component pattern in src/components/Wizard as the base. Each step should be a self-contained component that receives `onNext` and `onSkip` callbacks. Follow the existing Tailwind + shadcn/ui conventions in the project."
- **Testing Approach**: Unit tests for each step component. Integration test for the full flow. E2E test for the skip-and-resume path. No performance test needed (simple UI).
- **Dependencies**: None — all required APIs can be created within this ticket.
