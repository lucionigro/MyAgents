## Interaction Rules

- **Challenge bad ideas**: Do NOT agree with the developer just to be agreeable. If a proposed approach is suboptimal, has issues, or there's a better alternative, say so directly. Always prioritize finding the best solution over being accommodating.
- **Summary before code**: Before editing any code, first provide a concise summary of what the change involves — files affected, logic changes, potential side effects. Only proceed to implement after presenting the summary.
- **Simplicity first**: Write minimal, focused code. No speculative abstractions, no extra features, no future-proofing. Three similar lines beats a premature abstraction.
- **Surgical changes**: Edit only what's necessary. Match existing style, even if you'd do it differently. Do not refactor, rename, or clean up unrelated code in the same change.
- **Goal-driven execution**: Define verifiable success criteria before starting. Loop until criteria are met — don't declare done prematurely.

## Workspace Layout

Multi-repo root. Each subdirectory is an independent service or app.

Map repos in a table:

| Directory | What it is | Tech Stack |
|-----------|-----------|------------|
| **backend/** | Core API + business logic | — |
| **admin-web/** | Internal admin portal | — |
| **consumer-web/** | Consumer-facing app | — |

### Context Files

Keep AI context files in `context/` at the root — read these before exploring the codebase:
context/
module.md # Domain services, flows, integrations, entity relationships
schema.md # Complete DB schema — use this for queries instead of exploring
api.md # Frontend→backend endpoint mapping

For large cross-repo features, use a dedicated folder:
feature-project/
README.md # Index + ticket status
reference/ # Architecture docs
tickets/ # Per-ticket implementation notes

## Code & Architecture Patterns
Document your stack's conventions here. Example:
- **DI**: Convention-based registration by class suffix
- **Repos**: Base class inheritance; flag read-only queries explicitly
- **UoW**: Begin → operations → Save → Complete
- **Messaging**: Write to outbox before UoW commit for transactional guarantees
- **DB isolation**: Snapshot by default
## Skills (Claude Code)
Skills live in `~/.claude/skills/` (global) or `.claude/skills/` (project). Claude Code loads them automatically.
Invoke by typing the skill command in your message:
@skill-name do something

Build skills for repeated workflows: production support triage, full-stack context loading, commit conventions, branch creation.
## RTK — Token Optimization
RTK is a CLI proxy that strips noise from command output before it reaches Claude's context window (60–90% token savings).
```bash
rtk gain              # Show savings analytics
rtk gain --history    # Command history with savings
rtk discover          # Find missed optimization opportunities in Claude Code history
rtk proxy <cmd>       # Run command raw without filtering (debug)
