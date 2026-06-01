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

---

## Agent Roles

Each agent executing work in this repository must operate under a designated role, adhering to the responsibilities and restrictions of that role:

- **Orchestrator Agent**: Manages high-level goal decomposition, task assignment, progress tracking, and ensures transitions between lifecycle phases are correct. Does not write source code or run builds directly.
- **Repo Worker Agent**: Executes codebase modifications, creates assets, implements features, and modifies permitted files as defined by the current task template.
- **Research Agent**: Performs analysis, gathers resources, scans files, reads documentation, and creates plans/reports. Restricted from editing any source files (operates in a report-only fashion).
- **QA Agent**: Runs tests, audits security/compliance rules, verifies build outcomes, and inspects files. Prohibited from modifying source code except for test configuration and test script adjustments.
- **Build Agent**: Compiles files, packages assets, generates static builds, and executes CI/CD or build commands. Only permitted to write to build artifact directories (e.g., `dist/`).

---

## Standard Task Lifecycle

Every agent task must progress strictly through the following ten steps:

1. **Read current-state.json**: Read `.ops/current-state.json` to verify the active project, current phase, branch, and last completed gate.
2. **Read the assigned task**: Parse the assigned task file/object to understand task goals, allowed files, and constraints.
3. **Confirm branch**: Verify that the current git branch matches the branch designated in the task template.
4. **Confirm allowed files**: Crosscheck the list of files to be modified against the `allowed_files` array in the task template.
5. **Perform report-only review first if required**: If `requires_report_only_first` is set, review the files, analyze the requirements, and output a detailed status report before making edits.
6. **Make edits only after approval**: Confirm that any required approvals before edit (e.g., `approval_required_before_edit`) have been granted by a human reviewer.
7. **Run required commands**: Run all specified verification, build, or test commands listed in `commands_to_run`.
8. **Show git diff**: Run a git diff of the modified files to review changes for cleanliness and correctness.
9. **Show git status**: Run git status to ensure only allowed and untracked files are staged or modified.
10. **Wait for human approval before commit or merge**: Wait for explicit human approval before attempting to commit changes to the branch or merging the branch.

---

## Report-Only Task Rules

- **Strict Mode**: Under a report-only task, the agent has zero permission to write to, delete, or create source files in the repository.
- **Goal**: Gather context, check system state, list directory trees, find patterns, analyze errors, or draft plans.
- **Violation consequence**: Any write operation performed under a report-only task constitutes a fatal rule violation and fails the task checkpoint immediately.

## Edit Task Rules

- **Scope Limit**: Edits must strictly be confined to the files listed in `allowed_files`.
- **Pre-requisite**: An edit task can only proceed once any report-only phases are completed and approved.
- **Backup/Safety**: Before editing, review the `rollback_plan` within the task details.

## Git Workflow Rules

- **No Committing to Main**: Agents must never commit directly to the `main` or default branch.
- **Descriptive Branches**: Branches must be named according to the template prefix (e.g., `setup/*`, `task/*`, `ops/*`).
- **Diff Requirement**: Git diff must be reviewed line-by-line during the task run and shown in the output.
- **Pull Requests**: Code must be merged via Pull Requests. No direct fast-forward merges are allowed unless specifically overridden by a human.

## Forbidden Actions

- **Forbidden Files**: Never touch files explicitly listed in `forbidden_files`.
- **Forbidden Actions**: Never perform actions (such as network access, system configuration changes, installing globally cached packages, deleting git history) listed in `forbidden_actions`.
- **Commit Without Review**: Committing changes before running `git diff` and presenting it to the user is forbidden.
- **Bypassing Gates**: Proceeding to the next task or phase when `requires_human_review` is true without explicit human approval is forbidden.

## Gate Approval Rules

- **Definition**: Gates are key control points at the end of each development phase.
- **Review Log**: Every gate status must be recorded in `.ops/gate-log.md`.
- **Verification**: The human reviewer must check the `expected_output` and `success_criteria` of all tasks in the phase before marking a gate as `Completed`.

## Failure Conditions

A task execution is considered a failure if:
1. Any file not in the `allowed_files` list is modified, created, or deleted.
2. Any edit is performed during a report-only task or phase.
3. Git diff contains syntax errors, debugging statements, or placeholder code.
4. Required verification commands fail to run or exit with non-zero codes.
5. The agent proceeds to commit or merge without satisfying the required approval gates.
