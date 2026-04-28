# CLAUDE.md

## CRITICAL: Read Before Every Response

These rules are NOT suggestions. Follow them on every interaction, every file, every change.

---

## Interaction Rules

**Challenge bad ideas.**
If a proposed approach is suboptimal, wrong, or has a better alternative — say so directly. Do NOT agree to be agreeable. Prioritize the best solution over accommodation.

**Summarize before coding.**
Before touching any file: state which files change, what logic changes, and what could break. THEN implement. Never skip this step.

**Simplicity is the goal.**
Write the minimum code that solves the problem. No abstractions for hypothetical future use. No helper functions for single call-sites. Three similar lines is better than a premature abstraction.

**Surgical edits only.**
Change only what the task requires. Do NOT refactor adjacent code, rename variables, fix unrelated style, or clean up while you're in there. One concern per change.

**Define done before starting.**
State verifiable success criteria at the start. Loop until met. Do not declare done prematurely.

---

## Clean Code Rules

**No comments that explain what the code does.**
Names explain what. Comments explain WHY — only when the reason is non-obvious (hidden constraint, workaround, subtle invariant). If removing the comment wouldn't confuse a future reader, don't write it.

**No dead code.**
Don't leave unused variables, commented-out blocks, or `// TODO remove this` stubs. Delete it.

**No defensive code for impossible cases.**
Don't add null checks, fallbacks, or error handling for scenarios that can't happen given the surrounding code. Trust the type system and framework guarantees. Only validate at real system boundaries (user input, external APIs).

**No backwards-compatibility hacks.**
No `_unused` suffixes, no re-exports to preserve old import paths, no shim layers. If something is unused, delete it.

**No speculative features.**
Do not add logging, metrics, feature flags, or error handling "just in case." Build what was asked.

**Naming is documentation.**
Functions and variables must be named so that their purpose is obvious. If a name needs a comment to explain it, rename it instead.
