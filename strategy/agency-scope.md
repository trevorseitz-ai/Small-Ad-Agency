# Digital Publishing Strategy & Scope

This document establishes the strategy, scope, and tool framework for the **Small Ad Agency** publishing workflow.

> [!NOTE]
> **Core Identity Clarification**: This agency is dedicated exclusively to digital publishing and productized guide creation. It does not produce local community newsletters, print flyers, local business ad kits, or operate live ad-serving networks.

---

## 1. Selected Product Lane

The primary product lane for this agency is **Professional mini tutorial/workbook/textbook guides for digital sale**. These paid digital publishing products include:
- Mini-guides
- Workbooks
- Survival manuals
- Short technical textbooks
- Tutorial PDFs
- EPUB/PDF guide bundles
- Productized educational downloads

### Why This Lane is the POC Focus
- **High Value Density**: Selling digital products demands premium quality in copywriting, layout, and visual formatting, creating a high benchmark for agent execution.
- **Strict Template Rules**: Guides follow repeatable layout rules (cover pages, multi-level headers, warning callouts, code formatting blocks, cheat sheets) that map perfectly to automated document compilation.
- **Clear Verification**: The compiled output format (PDF/EPUB) is easy to inspect for layout bugs and formatting errors.

---

## 2. Sub-Lanes & Chosen Focus

### Proposed Sub-Lanes
1. **AI Tool Survival Manuals** (e.g., Quick reference books for complex developer platforms or developer APIs).
   - *Pros*: Leverages code-generation capabilities where LLMs excel; clear and concise structural format.
   - *Cons*: APIs change rapidly, requiring content updates; formatting requires careful code-block syntax rendering.
2. **Beginner Founder Workbooks** (e.g., Startup validation templates, financial planning exercises).
   - *Pros*: Reusable workbook grids; high startup market interest.
   - *Cons*: Design requires fillable PDF forms or print-to-scale tables which complicate CSS layout rendering.
3. **Niche Technical Mini-Textbooks** (e.g., Concise books detailing specific computer science algorithms).
   - *Pros*: Commands high digital sales prices; leverages academic layout styles.
   - *Cons*: Writing logic is complex; indexing and mathematical notation rendering require complex compiler setups.

### Chosen Sub-Lane: AI Tool Survival Manuals
For the POC phase, the agency will focus exclusively on producing **AI Tool Survival Manuals** (similar to the Replit Survival Manual format). This sub-lane provides a clean, developer-focused format that is highly compatible with structured agent-driven content compilation.

---

## 3. POC Boundaries & Scope

### In-Scope
- Drafting technical copy and code block tutorials.
- Building static HTML and Vanilla CSS design templates for the guide layout (alert callouts, code rendering, headers/footers).
- Running automated PDF compilation from templates.
- Executing formatting and proofreading QA checks.
- Human review gates at key phase completions.

### Out-of-Scope
- Creating online user portals or membership hubs.
- Payment gateway integrations or checkout systems.
- Live active databases or hosting of responsive web versions.
- Programmatic newsletter delivery systems or automated social media posting.

---

## 4. Agent Topology & Model/Tool Split

- **Antigravity**:
  - *Role*: **Repo Worker**.
  - *Authorized Tools*: File system modifications, template writes, local workspace editing.
- **Google AI Studio / Gemini**:
  - *Role*: **Research and Drafting Support**.
  - *Authorized Tools*: Sourcing technical documentation, copywriting guide sections, composing tutorials.
- **ChatGPT Plus**:
  - *Role*: **Orchestrator and QA**.
  - *Authorized Tools*: Task routing, project planning, document validation, text proofreading, layout evaluations.
- **Claude Code Pro** (used sparingly):
  - *Role*: **Hard Automation & Build Tasks**.
  - *Authorized Tools*: Troubleshooting script execution, fixing layout page-break CSS bugs, resolving compiler pipeline errors.

---

## 5. Post-Foundation Milestone Roadmap

The first three gates following the Ops Foundation are:

1. **Gate: Agency Scope (Current)**
   - *Goal*: Finalize guide product strategy, roles, and boundaries.
   - *Deliverable*: `strategy/agency-scope.md`.
2. **Gate: Product Scaffold**
   - *Goal*: Establish layout stylesheets, headers/footers, and guide HTML template systems.
   - *Deliverable*: Layout stylesheet files (`src/`) and HTML structures (`templates/`).
3. **Gate: Production Build**
   - *Goal*: Compile text copy and scaffold styles into a complete, placeholder-free PDF guide.
   - *Deliverable*: The final guide asset (`dist/manual.pdf`).
