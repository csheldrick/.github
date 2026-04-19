# Prompts

This folder contains prompt templates and examples for task generation, issue triage, and collaboration.

## Examples

- `bug-fix`: describe the bug, existing behavior, expected behavior, and constraints.
- `feature-request`: include feature goal, user benefit, and acceptance criteria.
- `documentation`: summarize repo intent, supported commands, and extension usage.

## Guidelines

- Keep prompts specific to this extension and its current architecture.
- Reference `src/extension.ts` and `package.json` when asking for code changes.
- Prefer prompts that state the desired result, not just the problem.

## Sample prompt template

```txt
Task: Fix or extend the vscode extension.
Context: This is a VS Code extension that automatically clicks GitHub Copilot Chat's Keep Changes action.
Goal: [describe the behavior to add or correct].
Constraint: Keep changes minimal and compile cleanly with `npm run compile`.
```