# Gas Town Worker Context

> **Context Recovery**: Run `gt prime` for full context after compaction or new session.

## The Propulsion Principle (GUPP)

**If you find work on your hook, YOU RUN IT.**

No confirmation. No waiting. No announcements. The hook having work IS the assignment.
This is physics, not politeness. Gas Town is a steam engine - you are a piston.

**Failure mode we're preventing:**
- Agent starts with work on hook
- Agent announces itself and waits for human to say "ok go"
- Human is AFK / trusting the engine to run
- Work sits idle. The whole system stalls.

## Critical Constraints

**NEVER use EnterPlanMode.** All Gas Town agents run unattended in tmux sessions.
Plan mode requires interactive UI approval that cannot be provided programmatically.
Using plan mode WILL stall your session indefinitely. Instead:
- Read the code, understand the task, then implement directly
- If the task is complex, break it into steps yourself — do not ask for approval
- Write code immediately. Do not propose changes first.

**Verification: build + unit tests locally, E2E via CI.**
- Run `npm run build` and `npm test -- --run` locally. These MUST pass before committing.
- Do NOT run E2E tests (`npm run test:e2e`) locally — they consume too much context and will kill your session.
- E2E tests run automatically in CI when you push to your branch / create a PR.
- After pushing, check CI status with `gh run list --branch <your-branch> --limit 1` and wait for it to pass.
- If CI fails, read the logs with `gh run view <run-id> --log-failed`, fix the issue, and push again.
- NEVER mark work as done if build or unit tests fail locally, or if CI E2E tests fail.

**Write tests FIRST. Test plan must exist and be approved before implementation begins.** This is a TDD shop. Follow red-green-refactor:
- Unit tests must cover all business logic, edge cases, and error paths
- E2E tests must cover user-facing functionality
- Tests must FAIL before implementation (red) and PASS after (green)
- Commit test files BEFORE production code — the git log must show test-first ordering
- Do NOT weaken test assertions to make them pass — fix the production code instead

## Context Budget Hygiene

Your session has a 200K token context window. Long command outputs (npm install, builds, test results) consume it fast. Protect your budget:
- Pipe verbose commands to files: `npm install > /tmp/install.log 2>&1 && echo "Install done, exit $?"`
- For test results, use: `npm test -- --run 2>&1 | tail -20` to see just the summary
- Avoid reading entire large files when you only need a few lines — use line offsets
- Commit and push EARLY. If your session dies after committing, the work survives.

## Startup Protocol

1. Check your hook: `gt mol status`
2. If work is hooked → EXECUTE (no announcement, no waiting)
3. If hook empty → Check mail: `gt mail inbox`
4. Still nothing? Wait for user instructions

## Key Commands

- `gt prime` - Get full role context (run after compaction)
- `gt mol status` - Check your hooked work
- `gt mail inbox` - Check for messages
- `bd ready` - Find available work (no blockers)
- `bd sync` - Sync beads changes

## Session Close Protocol

Before signaling completion:
1. git status (check what changed)
2. git add <files> (stage code changes)
3. bd sync (commit beads changes)
4. git commit -m "..." (commit code)
5. bd sync (commit any new beads changes)
6. git push (push to remote)
7. `gt done` (submit to merge queue and exit)

**Polecats MUST call `gt done` - this submits work and exits the session.**
