# AI-Assisted Development: Building From Spec

## 1. The Development Loop Overview

### 1.1 Inputs

Level 4 specs from the backlog — tickets with complete Why, What, and How sections that have passed the Spec DoD checklist (see [Specs](03_specs.md)).

### 1.2 The Cycle

```
Spec (Level 4) → AI Generation → Human Review → Integration → Validation → Ship
```

At each step, the human and AI have distinct responsibilities:

| Step | Human Does | AI Does |
|---|---|---|
| Spec → Prompt | Reads the How, loads context, crafts the prompt | — |
| AI Generation | — | Generates code draft from prompt |
| Human Review | Reviews for architecture, edge cases, security | — |
| Integration | Connects components, resolves conflicts | Suggests refactoring |
| Validation | Reviews test results, judges acceptance criteria | Runs tests, generates test scaffolding |
| Ship | Approves deployment, monitors production | Runs CI/CD pipeline |

### 1.3 The Core Principle

The developer is **accountable for all code**, regardless of whether a human or AI wrote it. AI generation is a tool, not a delegation of responsibility.

---

## 2. Spec-to-Prompt Translation

### 2.1 Reading the How Section as an AI Prompt

The How section of a Level 4 spec is written to be AI-execution-ready (see [Specs](03_specs.md) section 2.4). The developer's job is to translate it into an effective prompt by adding:

1. **Context**: What existing code does the AI need to know about?
2. **Constraints**: What conventions must the AI follow? (Load `CONVENTIONS.md`)
3. **Output format**: What exactly should the AI produce? (File, function, component, test)

### 2.2 Prompt Engineering for Code Generation

A good AI coding prompt has four parts:

```
1. CONTEXT
   "In the project at [path], using [framework/language], following
   the conventions in CONVENTIONS.md..."

2. TASK
   "Implement [ticket title]: [paste the How section]"

3. CONSTRAINTS
   "Follow these patterns: [reference existing file/pattern].
   Handle these edge cases: [paste from What section].
   Do NOT: [paste Out of Scope items]."

4. OUTPUT
   "Create the following files: [from Component Map].
   Write tests covering: [paste acceptance criteria]."
```

### 2.3 Iterative Prompting

When AI output is wrong, it usually means the spec is incomplete — not that the AI is bad. The feedback loop:

1. AI produces incorrect output
2. Developer identifies what's wrong
3. Developer checks: is this a **spec gap** or an **AI limitation**?
4. If spec gap → update the How section, then re-prompt
5. If AI limitation → manually correct and note the pattern for future prompts

**Track spec gaps discovered during development.** These feed back into improving the spec-writing process at the Sprint Retrospective.

---

## 3. The Human Review Cycle

### 3.1 What to Review in AI-Generated Code

AI-generated code requires focused review in specific areas:

**Architecture Conformance**
- Does it follow the patterns defined in `CONVENTIONS.md`?
- Does it integrate with existing code in the way the How section specified?
- Are there unnecessary abstractions or over-engineering?

**Edge Case Coverage**
- Did the AI miss scenarios not explicitly in the spec?
- Are error states handled?
- What happens with empty data, null values, boundary conditions?

**Security**
- Input validation at system boundaries
- Authentication and authorization checks
- Data handling and storage patterns
- No hardcoded credentials or keys

**Performance**
- O(n) operations on large datasets
- Database query patterns (N+1 queries, missing indexes)
- Unnecessary re-renders or recomputations

**Test Quality**
- Are AI-generated tests testing the right things?
- Do they test behavior (acceptance criteria) or implementation details?
- Are edge cases from the spec covered?

### 3.2 Code Review Practices

- **Smaller PRs are more important in AI-era teams, not less.** AI can generate large volumes of code quickly. Review in small, focused chunks.
- **Review for intent, not just syntax.** Does this code do what the spec says, or does it do something that looks similar?
- **The spec is the review checklist.** Walk through each acceptance criterion and verify the code satisfies it.
- **Flag AI patterns.** AI tends to generate plausible-looking code that handles the happy path perfectly but misses edge cases. Train your review eye for this.

---

## 4. The SDLC in the AI Era

The traditional SDLC phases still exist but are transformed:

| SDLC Phase | Traditional | AI-Era (24K Framework) |
|---|---|---|
| Planning | Sprint Planning meetings | Sprint Planning with Level 4 specs (decisions already made) |
| Design | Design phase before dev | Discovery Loop — continuous, ahead of development |
| Implementation | Developers write code | Developers prompt AI + review output |
| Testing | QA tests after development | AI generates tests from spec; QA validates coverage |
| Deployment | Manual or scripted releases | AI-assisted CI/CD, human-approved gate |
| Maintenance | Bug fixes and updates | AI-assisted debugging; specs updated for fixes |

---

## 5. The Sprint Execution Flow

### 5.1 Sprint Start (Day 1)

- Sprint Planning confirms goal, assigns ticket ownership
- Each developer reviews their assigned specs in detail
- Developer sets up AI context for their tickets (loads relevant code, CONVENTIONS.md, spec)

### 5.2 Daily Cycle

**Daily Sync** (15 min, walking the board):
1. What spec did I work on yesterday, and what AI output did it produce?
2. What am I working on today?
3. Is any spec unclear enough to be blocking AI generation?

Blockers in AI-augmented teams are almost always **spec clarity issues**, not capacity issues.

### 5.3 Feature Development Cycle (Per Ticket)

```
Step 1: Re-read the full spec (Why/What/How) before generating any code
        → Understand the intent, not just the tasks

Step 2: Load relevant context into AI tool
        → Existing code patterns, CONVENTIONS.md, related files

Step 3: Generate from the How spec
        → Use the prompt engineering pattern from section 2.2

Step 4: Review AI output against acceptance criteria
        → Walk each Given/When/Then criterion

Step 5: Write or review AI-generated tests
        → AI generates happy path; human adds edge cases

Step 6: Submit for peer review
        → Reviewer uses the spec as their review checklist

Step 7: QA validation against acceptance criteria
        → QA validates the What, not the How

Step 8: Merge and ship
        → CI/CD pipeline runs; human approves production deploy
```

### 5.4 Sprint Close

- **Sprint Review**: Demo completed features against their Why. Capture stakeholder feedback. Route insights back to the Discovery Loop.
- **Sprint Retrospective**: Focus on spec quality and AI-build velocity (see section 6).

---

## 6. Definition of Done

### 6.1 Spec DoD (before entering sprint)

See [Specs](03_specs.md) section 2.5.

### 6.2 Development DoD (before QA review)

- [ ] Code conforms to architecture established in How section
- [ ] All acceptance criteria from What section pass
- [ ] AI-generated tests cover the happy path
- [ ] Human-written tests cover at least 2 edge cases
- [ ] Code reviewed by at least one other human
- [ ] No new security vulnerabilities introduced
- [ ] Performance meets non-functional requirements from What section
- [ ] Documentation updated (AI-drafted, human-approved)

### 6.3 Ship DoD (before production deploy)

- [ ] QA validation complete against full acceptance criteria set
- [ ] Deployed to staging, smoke-tested
- [ ] Production metrics baseline captured
- [ ] Insights logged for Discovery Loop (what did production reveal?)

---

## 7. Continuous Integration in the AI Era

### 7.1 Every Commit Runs the Full Test Suite

AI-generated code must pass the same CI gates as human-written code. No exceptions.

### 7.2 PR Gate

Every PR description includes:
- Link to the source ticket (Level 4 spec)
- Acceptance criteria checklist (checked off by the developer)
- Note on which code was AI-generated vs. hand-written (for review context)

### 7.3 Deployment

- **Staging**: Automated deploy on merge to main
- **Production**: Human-approved gate before production deploy
- **Monitoring**: Post-deploy metrics checked against the non-functional requirements from the spec

---

## 8. Sustainable Pace in an AI-Augmented Team

AI tooling creates pressure to go faster constantly. The feeling of infinite capacity is an illusion.

**What AI speeds up**: Code generation, test scaffolding, documentation, boilerplate.

**What AI does not speed up**: Spec writing, code review judgment, user research, architectural decisions, team communication.

Sprint commitments must respect human cognitive limits for judgment-heavy work. A developer who writes specs, reviews AI output, and debugs edge cases all day is doing demanding cognitive work — even if the AI writes 10x more code than a human would.

The Scrum Master should watch for signs that AI velocity is being mistaken for sustainable pace:
- Increasing spec gaps discovered during development
- Declining code review quality
- More bugs escaping to production
- Team members skipping the spec review step and "just prompting"
