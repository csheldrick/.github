---
name: new-plan
description: "Guided prompt to create a structured implementation plan that plan-coordinator can parse and execute with mentor/worker agents."
---

# Implementation Plan Template

Use this prompt to create a structured multi-phase implementation plan. The plan coordinator will parse this into phases, dispatch mentor/worker pairs, and validate results.

## Plan Structure

Copy the template below and fill in your plan:

```markdown
# Implementation Plan: [Feature Name]

**Objective:** [One sentence: what problem does this solve or feature add?]

**Success Criteria (at completion):**
- ✅ [Feature is working]
- ✅ [Tests pass]
- ✅ [Documentation updated]
- ✅ [No breaking changes]

---

## Phase 1: [Phase Name]

**Phase Goal:** [One sentence description]

**Must Build:**
- [ ] [Requirement 1]
- [ ] [Requirement 2]
- [ ] [Requirement 3]

**Constraints:**
- [Pattern to follow or rule to respect]
- [Don't break X]
- [Use stable API Y]

**Success Criteria:**
1. ✅ [Code compiles with no TypeScript errors]
2. ✅ [Tests pass (specify count)]
3. ✅ [Follows SKILL.md pattern: [section name]]
4. ✅ [No breaking changes to [what]]
5. ✅ [Documentation updated: [what]]

**Dependencies:** [Depends on Phase X, or None]

**Estimated Effort:** [Time estimate]

---

## Phase 2: [Phase Name]

[Repeat structure above]

---

## Phase N: [Final Phase]

**Phase Goal:** Final validation and documentation

**Must Build:**
- [ ] README updated with all new features
- [ ] All instructions/skills current
- [ ] Workflow documentation complete

**Success Criteria:**
1. ✅ [All previous phases complete]
2. ✅ [README reflects all changes]
3. ✅ [Examples functional and current]
4. ✅ [No stale documentation]

**Dependencies:** Depends on Phases 1-N

---

## Execution Notes

- Phases marked "None" in Dependencies can run in parallel
- Phases with dependencies run sequentially after prerequisites
- Plan Coordinator will dispatch phase-mentor/phase-worker pairs
- Each phase must pass all success criteria to be approved
- If phase fails mentor validation, worker returns for rework

---

## Questions for Plan Author

Before writing your plan, answer:
1. **What is the main feature or fix?** (objective)
2. **How many independent work streams?** (phases)
3. **What patterns apply?** (SKILL.md sections)
4. **What could break?** (constraints)
5. **How will we know it's done?** (success criteria)
```

---

## Example: Adding Pause/Resume Command

```markdown
# Implementation Plan: Pause/Resume Command

**Objective:** Add pause and resume commands to give users more control over when AutoKeep is active, preventing accidental clicks during specific VS Code operations.

**Success Criteria (at completion):**
- ✅ Both pause and resume commands working
- ✅ State persists across VS Code restarts
- ✅ Tests cover both commands and persistence
- ✅ README documents new commands
- ✅ No breaking changes to existing toggle command

---

## Phase 1: Add Pause/Resume Commands

**Phase Goal:** Implement pause and resume command handlers with persistent state

**Must Build:**
- [ ] `autokeep.pause` command (stops polling, disables auto-click)
- [ ] `autokeep.resume` command (restarts polling)
- [ ] Persist pause state across restarts
- [ ] Add status bar indicator for pause state

**Constraints:**
- Must follow SKILL.md "Command Registration" pattern
- Must follow SKILL.md "Persistent State Management" pattern
- Must not break existing toggle functionality
- Must register all subscriptions in context.subscriptions
- No new external dependencies

**Success Criteria:**
1. ✅ Code compiles (npm run compile)
2. ✅ Tests pass (add minimum 4 new tests for pause/resume)
3. ✅ Follows SKILL.md Command Registration pattern
4. ✅ State persists (pause state survives restart)
5. ✅ No breaking changes (existing toggle still works)
6. ✅ README updated with new commands

**Dependencies:** None (can start immediately)

**Estimated Effort:** 2-3 hours

---

## Phase 2: Add Tests and Validation

**Phase Goal:** Ensure pause/resume feature is robust with comprehensive test coverage

**Must Build:**
- [ ] Unit tests for pause command
- [ ] Unit tests for resume command
- [ ] Integration test for pause state persistence
- [ ] Test for status bar updates correctly
- [ ] Test that polling actually stops when paused

**Constraints:**
- All tests must pass (0 failures)
- Tests must be deterministic (no flaky tests)
- Must test edge cases (rapid pause/resume, restart during pause, etc.)

**Success Criteria:**
1. ✅ All existing tests still pass
2. ✅ 5+ new tests added and passing
3. ✅ Edge case tests included
4. ✅ No skipped or commented tests
5. ✅ Test coverage for pause/resume feature ≥ 80%

**Dependencies:** Depends on Phase 1

**Estimated Effort:** 1-2 hours

---

## Phase 3: Documentation and Finalization

**Phase Goal:** Ensure all documentation reflects the new pause/resume feature

**Must Build:**
- [ ] README.md: Add pause/resume to Commands section
- [ ] README.md: Add usage examples
- [ ] Code comments: Document pause state logic
- [ ] Update CHANGELOG (if exists)

**Constraints:**
- Examples must be accurate and tested
- Documentation must match actual behavior
- No outdated or misleading information

**Success Criteria:**
1. ✅ README updated with pause/resume commands
2. ✅ Usage examples included and functional
3. ✅ Code comments explain non-obvious logic
4. ✅ All prior phases still passing
5. ✅ No documentation inconsistencies

**Dependencies:** Depends on Phases 1-2

**Estimated Effort:** 1 hour

---

## Execution Notes

- Phase 1 can start immediately (no dependencies)
- Phase 2 depends on Phase 1 (start after Phase 1 approved)
- Phase 3 depends on Phases 1-2 (start after both approved)
- Plan Coordinator will dispatch mentor/worker pairs for each phase
- Each phase must pass mentor validation before next phase starts
```

---

## When to Use This Prompt

- Planning a feature implementation
- Breaking down a large task into phases
- Documenting requirements before coding
- Coordinating team work on related tasks

## Suggested Usage

1. Copy the template above
2. Fill in your feature details
3. Define 2-4 phases (too many = harder to track; too few = hard to parallelize)
4. Make success criteria concrete and measurable
5. Share plan with plan-coordinator:
   *"Using the plan-coordinator agent, execute this implementation plan: [paste plan]"*

The plan-coordinator will:
- Parse your phases
- Dispatch phase-mentor agents to create Requirements Briefs
- Dispatch phase-worker agents to implement
- Validate results against success criteria
- Update documentation on completion

## Related Artifacts

- **plan-coordinator.agent.md** — Orchestrates phase execution
- **phase-mentor.agent.md** — Creates requirements, validates work
- **phase-worker.agent.md** — Implements features iteratively
- **`.github/plans/`** — Store finalized plans here for future reference

## Notes

 - The Final plan file must end with `.prompt.md` to be recognized as a prompt by the system.