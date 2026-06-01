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
