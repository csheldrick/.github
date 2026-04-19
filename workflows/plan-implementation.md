## Implement Plan From Library Workflow

This workflow executes a selected plan from [.github/plans](../plans) using agent instructions from a forked superpowers repository.

### Triggers

1. workflow_dispatch
2. issue_comment with /implement-plan <plan-file.md>

### Inputs (workflow_dispatch)

1. plan_file: required plan filename inside .github/plans.
2. superpowers_repo: required forked superpowers repository (owner/repo).
3. superpowers_ref: optional branch, tag, or SHA from the fork.
4. superpowers_agent_path: optional path to agent file in the fork.
5. model: optional GitHub Models model id.
6. apply_changes: when true, generated patch is applied.
7. commit_changes: when true and create_pr is false, changes are committed and pushed to the current branch.
8. create_pr: when true, the workflow commits to a generated branch and opens a pull request automatically.

### What It Does

1. Validates plan selection and file safety.
2. Loads an agent definition from your forked superpowers repo.
3. Falls back to local [.github/agents/plan-coordinator.agent.md](../agents/plan-coordinator.agent.md) if the forked file is unavailable.
4. Builds an implementation prompt from the selected plan and agent instructions.
5. Generates a unified diff patch through GitHub Models when GH_MODELS_API_KEY is configured.
6. Optionally applies and commits the patch.
7. Optionally pushes a dedicated branch and opens a pull request for manual review.
8. Uploads artifacts with prompt, model response, and patch output.

### Required Secret

1. GH_MODELS_API_KEY is needed for model-based patch generation.

### Recommended Usage

1. First run with apply_changes=false and commit_changes=false.
2. Review artifacts and patch output.
3. Re-run with apply_changes=true after validation.
4. Keep create_pr=true to send completed work to a reviewable pull request.
5. Use commit_changes=true only when you want push-without-PR behavior on the current branch.
