# Roles: The AI-Augmented Team

## 1. Role Philosophy

### 1.1 Roles Define Judgment Ownership, Not Task Lists

In traditional Scrum, roles are defined by what people do: developers write code, QA writes tests, designers make mockups. In the AI era, AI can do most of those tasks. Roles are now defined by what **judgment** a human owns — the decisions that require empathy, context, ethics, and experience.

### 1.2 One Human, Multiple Roles

AI expands what one person can accomplish. A developer with AI tools can also handle QA responsibilities. A Product Owner with AI research tools can absorb business analysis. This is not cutting corners — the quality bar remains the same. The staffing model changes because AI handles execution volume.

Role-stacking is a feature of this framework, not a compromise.

### 1.3 Minimum Viable Team Configurations

| Configuration | Humans | Typical Setup |
|---|---|---|
| Solo | 1 + AI | Founder mode — one person holds all roles |
| Micro | 2–3 + AI | 1 Discovery-focused + 1–2 Build-focused |
| Small | 4–6 + AI | Full role coverage, some combining |
| Standard | 6–8 + AI | Full separation of all roles |

See [Team Scaling](07_team_scaling.md) for detailed configurations.

---

## 2. Core Roles

### 2.1 Product Owner / Vision Keeper

The Product Owner owns the **Why** at all times. They define and guard the product-level Golden Circle, and they are the final authority on what gets built and what does not.

**Human Owns**:
- Product vision and strategy
- Priority decisions and trade-offs
- Stakeholder relationships
- Deciding what the product is — and what it is not
- Accepting or rejecting specs as ready for development

**AI Augments**:
- Drafting ticket descriptions from bullet points
- Suggesting acceptance criteria from user stories
- Summarizing stakeholder feedback into backlog items
- Market research and competitor analysis
- Sprint report generation

**Key Skill Shift**: The PO's primary craft becomes spec clarity. A vague idea must become a precise Why + What before it enters the development pipeline. AI helps draft; the human ensures truth.

---

### 2.2 UI/UX Designer / Discovery Engine

This role is **fundamentally transformed** from traditional Scrum. The Designer is not a service function that delivers mockups on request. The Designer runs the **Discovery Loop** — a continuous process of prototyping and user testing that stays 1–2 sprints ahead of the development team.

**Human Owns**:
- Reading users — interpreting behavioral signals, not just opinions
- Framing hypotheses about what users need
- Deciding what to prototype and what to test
- Knowing when a prototype has generated enough evidence
- Making the call to throw away a prototype and start over
- Translating user feedback into refined specs

**AI Augments**:
- Vibe-coded prototype generation from natural language descriptions
- Design variant creation for A/B testing
- Generating component states from a single described state
- Accessibility checks
- User testing synthesis

**Primary Output**: Validated insights that become refined specs — not final designs, not production code.

**Secondary Output**: Design system components and UX references for the development team.

**Prompt Pattern Example**: "Generate a React prototype of a [feature description] following these interaction rules: [list]. Use Tailwind for styling. This is throwaway code for user testing only — optimize for speed, not production quality."

---

### 2.3 Technical Lead / Architecture Guardian

The Technical Lead owns the **How** at system level. They define AI prompting conventions, code standards, and architectural boundaries. In an AI-augmented team, the Tech Lead's most important job is ensuring that AI-generated code conforms to the system's architecture — not writing code themselves.

**Human Owns**:
- System architecture decisions
- Technology selection and trade-offs
- Code review judgment (especially AI-generated code)
- Security architecture
- Technical debt decisions
- Mentoring developers on AI-assisted workflows

**AI Augments**:
- Generating architecture diagrams from descriptions
- Reviewing How sections for completeness
- Suggesting technology trade-offs
- Generating Architecture Decision Record (ADR) drafts
- Boilerplate and scaffolding generation

**Key Responsibility**: Maintaining the project's `CONVENTIONS.md` — the document loaded into AI tools that defines naming, structure, patterns, and anti-patterns (see [Quality](06_quality.md) section 3.3 for the full specification). This is the mechanism by which the Tech Lead influences every line of AI-generated code.

---

### 2.4 Developer / AI-Pair Programmer

The Developer's workflow has shifted from writing code to **directing AI code generation and reviewing the output**. The developer is responsible for translating the How section of a spec into AI prompts, reviewing what the AI produces, and ensuring the code meets the spec's acceptance criteria.

**Human Owns**:
- Spec interpretation — understanding the intent behind the How
- Prompt crafting — translating specs into effective AI instructions
- Code review judgment — catching what AI misses
- Integration logic — connecting AI-generated components
- Edge case recognition — identifying scenarios not in the spec
- All code, regardless of generation source (developer is accountable)

**AI Augments**:
- Code generation from specs
- Unit test generation
- Refactoring suggestions
- Documentation drafts
- Boilerplate and repetitive code

**The Review Contract**: Every AI-generated code block requires human review before merge. The developer is accountable for all code in their name, regardless of whether a human or AI wrote it.

**Prompt Pattern Example**: "Implement [ticket title] following the spec: [paste How section]. Use the patterns established in [reference existing file]. Write tests that cover these acceptance criteria: [paste from What section]."

---

### 2.5 Scrum Master / Process Keeper

The Scrum Master facilitates ceremonies and owns **spec quality enforcement**. In the AI era, the most common blocker is not a technical impediment — it is a spec clarity issue. The Scrum Master ensures that no under-specified ticket enters a sprint.

**Human Owns**:
- Team health and interpersonal dynamics
- Process adaptation — knowing when to change the process
- Spec quality enforcement (the Level 4 gate)
- Removing blockers in both the Discovery Loop and Development Loop
- Facilitating retrospectives focused on spec quality

**AI Augments**:
- Retro facilitation prompts and templates
- Ceremony note-taking and action item tracking
- Process metric tracking and visualization
- Sprint report drafting

---

### 2.6 QA Engineer / Validation Lead

Quality is no longer a final gate — it is embedded throughout the spec-to-ship pipeline. The QA Engineer's primary input is the ticket's **What section** (acceptance criteria). Their primary output is a judgment on whether test coverage matches spec intent.

**Human Owns**:
- Acceptance criteria co-authoring (part of spec writing, not after)
- Exploratory testing — the irreplaceable human contribution to quality
- User acceptance judgment — validating the Why was achieved, not just the What
- AI-generated test review — are the tests testing the right things?
- Edge case design — identifying scenarios the spec missed

**AI Augments**:
- Test case generation from acceptance criteria
- Regression suite maintenance
- Test data generation
- Performance test scaffolding

**Key Shift**: QA writes acceptance criteria as part of the spec (during refinement), not test cases after development. AI generates tests from those criteria; QA validates that the generated tests match the spec's intent.

---

## 3. Role Combinations

When one human covers multiple roles with AI support:

| Combination | Name | Works Best When |
|---|---|---|
| PO + Scrum Master | Process + Vision Lead | Team < 6 people; ceremonies are lightweight |
| PO + Designer | Product Discovery Lead | Early-stage product; prototype loop drives backlog |
| Tech Lead + Developer | AI Build Lead | Micro teams; one person owns architecture and builds |
| Developer + QA | Full-Stack Quality Engineer | Mature codebase; AI generates tests; human reviews |
| Scrum Master + QA | Quality Process Lead | Stable teams; quality and process closely aligned |

**Anti-pattern**: Combining PO + Developer. The person who decides what to build should not be the same person who builds it — they will unconsciously scope to what's easy to code, not what's valuable to users.

---

## 4. Roles Absorbed or Transformed

| Traditional Role | In the 24K Framework |
|---|---|
| Business Analyst | Absorbed into Product Owner with AI research tools |
| Dedicated QA Department | Embedded QA in every developer; dedicated QA role is validation lead |
| Technical Writer | AI-generated docs, human-edited; owned by developer who built the feature |
| DevOps Engineer | AI-assisted pipelines, owned by Technical Lead |
| Project Manager | Absorbed into Scrum Master + Product Owner |
