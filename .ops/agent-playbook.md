# Agent Playbook

This document defines the strict rules that all agents must follow when executing tasks in the **Small Ad Agency** repository.

## Core Rules

1. **Document-First**: Every change, design decision, and plan must be thoroughly documented first before any source code is modified.
2. **Branch-Per-Step**: Work must be done on a dedicated branch per task step. Never work directly on the main/default branch.
3. **Report-Only Tasks**: If a task is marked as report-only, the agent must perform analysis, verification, or scanning only and make **no edits** whatsoever.
4. **Allowed Files Only**: Agents are strictly prohibited from modifying files outside of the explicitly specified `allowed_files` list in the task configuration.
5. **Diff Before Commit**: Agents must run and review a git diff before making any commit to ensure no unintended files or changes are introduced.
6. **PR Before Merge**: All branch merges must go through a Pull Request/Merge Request process. Direct merges are forbidden.
7. **Scaffold Approval First**: No generated output files or artifacts may be produced until the build scaffold is explicitly approved.
8. **No Premature Published Status**: No metadata, database entry, or status may be marked as "Published" until the actual output files exist and are verified.
9. **Human Gate Approval**: Explicit human approval is required to pass any designated gate in the operating system.
10. **Report-Only Violation Policy**: If an agent performs any file edits during a task designated as report-only, the checkpoint automatically fails.

## Reviewer, Fact-Checker, and Human Approval Workflow

### Reviewer Agent
Checks process compliance:
- correct branch
- allowed files only
- forbidden files untouched
- required status updates
- JSON validity where applicable
- diff cleanliness
- no forbidden actions
- no scope drift
- required commands run
- report includes status and diff

Reviewer Agent may approve process-only tasks when human_content_gate is false and human_approval_required_before_commit is false.

### Fact Checker Agent
Checks truth and support:
- factual claims match source files or cited sources
- citations support the specific claims they are attached to
- unresolved claims remain marked [Citation Needed] or [Verification Needed]
- author recommendations are labeled [Author Recommendation]
- exact pricing, limits, billing behavior, credits, rollover, expiration, deployment costs, Agent mode behavior, and platform rules are not asserted without verified support
- low-confidence research is not promoted to final fact

Fact Checker Agent returns one of:
- PASS
- PASS WITH REQUIRED MARKERS
- REVISE
- BLOCK

### Human Approver
Approves product judgment:
- product strategy
- outline structure
- chapter content before commit
- final manuscript
- build/package output
- publish/release decisions

Human approval is required when:
- human_content_gate is true
- human_approval_required_before_commit is true
- final.md is edited
- generated release artifacts are created
- metadata status is changed to Published
- product strategy or outline structure changes

### Approval Rules
- Reviewer approval is required for every task after report-only.
- Fact-checker approval is required for research, outline, draft, final, build/package/publish, and any task containing factual product claims.
- Human approval is required for content gates, final manuscript, build outputs, and publish/release actions.
- Reviewer Agent and Fact Checker Agent must not be the same agent as the Repo Worker Agent for the same task.
- Fact Checker Agent must not rewrite creatively; it flags unsupported claims and suggests safer wording only.
- Ops-only task definitions can proceed to commit with reviewer approval only if human_content_gate is false and human_approval_required_before_commit is false.
- Chapter drafts require reviewer approval, fact-checker approval, and human approval before commit.

### Recommended Defaults by Task Type

| Task Type | reviewer_approval_required | fact_checker_required | human_content_gate | human_approval_required_before_commit |
|---|---:|---:|---:|---:|
| Ops-only task definition | true | false | false | false |
| Ops workflow/playbook change | true | false | false | true |
| Product setup/scaffold | true | false | false | true |
| Research/source audit | true | true | false | true |
| Outline | true | true | true | true |
| Chapter draft | true | true | true | true |
| Final manuscript | true | true | true | true |
| Build/package | true | false | true | true |
| Publish/release | true | true | true | true |
