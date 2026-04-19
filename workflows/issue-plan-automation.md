## Issue Plan Automation Workflow

This workflow runs automatically when a new GitHub issue is opened.

### What It Does

1. Builds a deterministic plan filename from the issue number and title.
2. Dispatches [.github/workflows/plan-generation.yml](./plan-generation.yml) with the issue title, body, and URL.
3. Waits for plan generation to finish successfully.
4. Verifies the generated plan file exists in [.github/plans](../plans).
5. Dispatches [.github/workflows/plan-implementation.yml](./plan-implementation.yml) for that plan.
6. Waits for implementation to finish.
7. Looks for the pull request opened by the implementation workflow.
8. Comments back on the issue with links to the generation run, implementation run, and PR when found.

### Defaults

1. Forked superpowers repo: `csheldrick/superpowers`
2. Forked ref: `main`
3. Agent path: `agents/plan-coordinator.agent.md`
4. Model: `openai/gpt-4.1`

### Requirements

1. The plan generation workflow must be able to commit the generated plan.
2. The implementation workflow must be able to create a PR.
3. `GH_MODELS_API_KEY` should be configured if you want model-generated plans and patches.

### Notes

1. This workflow runs on every newly opened issue.
2. It uses the existing generation and implementation workflows rather than duplicating their logic.
3. It relies on workflow run names to identify and wait for the correct downstream runs.
