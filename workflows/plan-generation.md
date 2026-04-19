## Generate Implementation Plan Workflow

This workflow generates a markdown implementation plan in [.github/plans](../plans) from a user request.

### Triggers

1. `workflow_dispatch`
2. `issue_comment` with `/plan <request text>`

### Inputs (workflow_dispatch)

1. `user_request` (required): natural-language request to plan.
2. `plan_name` (optional): output file name without extension.
3. `superpowers_repo` (required): your forked `superpowers` repo (`owner/repo`).
4. `superpowers_ref` (optional): branch/tag/SHA in your fork.
5. `superpowers_agent_path` (optional): agent file path in fork.
6. `model` (optional): GitHub Models ID.
7. `commit_plan` (optional): commit generated plan back to branch.

### Secrets

1. `GH_MODELS_API_KEY` (optional): when set, the workflow calls GitHub Models for AI plan generation.
2. If missing, the workflow falls back to a deterministic template-based plan.

### Output

- Generated file: `.github/plans/<plan_name>.md`
- Artifact: `generated-plan-<plan_name>`
- Optional commit to the triggering branch (workflow_dispatch only)

### Notes

- The workflow checks out your forked `superpowers` repository and tries to load the specified agent file.
- If the agent file is unavailable, it falls back to local [.github/agents/plan-coordinator.agent.md](../agents/plan-coordinator.agent.md).
- For issue comments, commit is disabled automatically and a status comment is posted with artifact details.
