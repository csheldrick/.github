---

## How to Use This Workflow

### Manual Trigger (Recommended)

1. Go to GitHub Actions → "Execute Implementation Plan"
2. Click "Run workflow"
3. Enter the plan file name (e.g., `add-pause-resume-command.md`)
4. Check "Invoke plan-coordinator agent" (default: yes)
5. Click "Run workflow"

### What Happens

1. **Validate Plan** — Checks that plan file exists and is readable
2. **Prepare Environment** — Installs dependencies, compiles code, runs tests
3. **Display Instructions** — Shows how to invoke plan-coordinator
4. **Ready Signal** — Confirms plan is ready for coordinator execution
5. **Track Results** — Creates artifact to track phase progress

### Next Steps (Manual)

After the workflow runs:

1. Open **GitHub Copilot Chat** in VS Code
2. Type: `/plan-coordinator`
3. Paste your plan from `.github/plans/add-pause-resume-command.md`
4. The agent will begin executing the multi-phase workflow

### Expected Execution Flow

```
Workflow starts
    ↓
Validate plan structure
    ↓
Prepare environment (npm install, compile, test)
    ↓
Display execution instructions
    ↓
Artifact created for tracking
    ↓
🎯 Ready for plan-coordinator agent to execute
    ↓
[In VS Code] Invoke plan-coordinator with plan
    ↓
Plan-coordinator dispatches mentor/worker pairs
    ↓
Each phase: mentor → worker → validate → approve/rework
    ↓
Documentation updates
    ↓
✅ Plan complete
```

## Monitoring Execution

Track plan progress using:

- **GitHub Copilot Chat output** (shows phase-by-phase progress)
- **Workflow artifacts** (execution-log.md tracks phase statuses)
- **Git commits** (worker commits changes for each phase)
- **Tests** (phase validation requires all tests passing)

## Available Plans

Current plans in `.github/plans/`:
- `add-pause-resume-command.md` — Add pause/resume commands with tests and docs

## Plan Format

Plans must follow `.github/prompts/new-plan-template.prompt.md` format:
- Clear phases with dependencies
- Success criteria per phase
- "Must Build" checklist
- Constraints and patterns to follow
- Estimated effort

## Troubleshooting

**Plan file not found?**
- Check file is in `.github/plans/` directory
- Verify filename matches exactly
- File must be `.md` format

**Compilation errors?**
- Workflow will show errors but continue
- Phase-worker will fix during implementation

**Tests failing?**
- Existing tests should pass before plan starts
- Phase-worker adds new tests during implementation
- All must pass for phase approval

**Mentor/Worker not dispatching?**
- Make sure you invoke plan-coordinator agent manually in VS Code
- Workflow prepares the plan; coordinator executes it
- Both are separate steps intentionally

## Integration Points

- `.github/prompts/new-plan-template.prompt.md` — Template for creating plans
- `.github/plans/` — Directory of plans to execute
- `.github/agents/plan-coordinator.agent.md` — Orchestrates execution
- `.github/agents/phase-mentor.agent.md` — Defines requirements
- `.github/agents/phase-worker.agent.md` — Implements features
- `.github/instructions/extension-best-practices.instructions.md` — Validation rules
- `.github/skills/ *.skill.md` — Pattern reference for workers

---

*Workflow created to support multi-phase, mentor/worker-driven implementation*
