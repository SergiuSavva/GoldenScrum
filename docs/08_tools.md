# Tools: The AI-Era Stack

## 1. Tool Selection Philosophy

### 1.1 Tools Serve Spec Quality and AI Generation

Every tool in the stack should either help write better specs or help AI generate better code. If a tool does neither, question whether you need it.

### 1.2 Prefer Tools with AI Integration

When choosing between alternatives, prefer the one with native AI integration. A tool that works with AI assistants is more valuable than one that is "better" in isolation.

### 1.3 The CONVENTIONS.md Anchor

Every project should maintain a `CONVENTIONS.md` file loaded into AI tools as context. See [Quality](06_quality.md) section 3.3 for the full specification of what this file should contain. The Technical Lead owns this file.

---

## 2. Discovery Loop Tools

### 2.1 Vibe-Coded Prototyping

| Tool | What It Does | Best For |
|---|---|---|
| v0.dev (Vercel) | Natural language to React UI components | Quick component prototypes |
| Bolt.new (StackBlitz) | Full-stack prototypes from prompts | Interactive prototypes with backend stubs |
| Lovable | AI-generated web apps | Full-page and multi-page prototypes |
| Cursor / Windsurf | AI-assisted IDE for controlled generation | When you need more control over the prototype |
| Figma + AI plugins | Traditional design with AI assist | Design system consistency, final UX references |

### 2.2 User Testing

| Tool | What It Does | Best For |
|---|---|---|
| Maze | Unmoderated usability testing | Async task-based tests at scale |
| Lyssna | First-impression and task-based testing | Quick 5-second tests, preference tests |
| UserTesting.com | Moderated user sessions | Deep qualitative research |
| Dovetail | AI-assisted research synthesis | Clustering and pattern-matching feedback |

---

## 3. Spec and Backlog Management

| Tool | Strength | Best For |
|---|---|---|
| Linear | Best native support for custom ticket fields (Spec Level) | Engineering-led teams wanting speed |
| Jira | Deeply configurable, extensive integrations | Teams already invested in Atlassian |
| GitHub Issues + templates | Custom templates for Golden Circle format | Small teams, open-source projects |
| Notion | Flexible databases, prose-heavy specs | Teams that prefer document-style specs |

**Recommendation**: Whichever tool you choose, create a **custom ticket template** that enforces the Golden Circle format (Why/What/How sections, Spec Level field, Spec DoD checklist). See [Specs](03_specs.md) for the format.

---

## 4. AI Development Tools

### 4.1 Code Generation

| Tool | What It Does | Best For |
|---|---|---|
| Cursor | IDE with AI pair programming, codebase-aware | Primary development environment |
| Claude Code | CLI-based AI assistant, architectural reasoning | Spec-to-code translation, complex refactoring |
| GitHub Copilot | Inline code suggestions | In-editor completion while coding |
| Windsurf | AI-assisted IDE with flow state | Alternative to Cursor |

### 4.2 Code Review Assist

| Tool | What It Does | Best For |
|---|---|---|
| GitHub Copilot PR summaries | Auto-summarizes PR changes | Quick PR understanding |
| CodeRabbit | Automated PR review against conventions | Catching consistency issues AI introduced |

### 4.3 AI Research and Drafting

| Tool | What It Does | Best For |
|---|---|---|
| Claude / ChatGPT | General-purpose AI assistant | Spec drafting, research, ticket writing |
| Perplexity | AI-powered research with sources | Technology evaluation, library selection |

---

## 5. CI/CD and Infrastructure

| Tool | What It Does | Best For |
|---|---|---|
| GitHub Actions | CI/CD pipeline automation | Most teams (integrated with GitHub) |
| Vercel | Frontend deployment with preview environments | Web applications, Next.js projects |
| Railway | Backend deployment with easy scaling | API services, databases |
| Docker | Containerized environments | Consistent dev/prod environments |
| Sentry | Error monitoring and alerting | Production insight → Discovery Loop feedback |

---

## 6. Communication and Async

| Tool | What It Does | Best For |
|---|---|---|
| Slack / Discord | Async team communication | Daily updates, quick questions |
| Loom | Async video messages | Prototype walkthroughs, ceremony replacements |
| Zoom / Google Meet | Video calls | Ceremonies that require real-time discussion |
| Linear/Jira + Slack integration | Automatic sprint progress updates | Reducing manual status reporting |

---

## 7. Tool Stack by Team Size

### Solo (1 person)

| Category | Recommended |
|---|---|
| Prototyping | v0.dev or Bolt.new |
| User testing | Maze (async) |
| Backlog | GitHub Issues or Notion |
| Development | Cursor + Claude Code |
| CI/CD | GitHub Actions + Vercel |
| Communication | N/A |

### Micro (2–3 people)

| Category | Recommended |
|---|---|
| Prototyping | v0.dev + Figma |
| User testing | Maze + occasional moderated sessions |
| Backlog | Linear or GitHub Issues |
| Development | Cursor + Claude Code |
| CI/CD | GitHub Actions + Vercel/Railway |
| Communication | Slack + Loom |

### Small to Standard (4–8 people)

| Category | Recommended |
|---|---|
| Prototyping | v0.dev/Bolt.new + Figma |
| User testing | Maze + Lyssna + UserTesting.com |
| Backlog | Linear or Jira |
| Development | Cursor + Claude Code + Copilot |
| Code review | CodeRabbit + GitHub Copilot PR summaries |
| CI/CD | GitHub Actions + Vercel/Railway + Docker |
| Monitoring | Sentry |
| Communication | Slack + Loom + Zoom |
