# Karpathy Guidelines (AI-Assisted Engineering)

Practical heuristics for working with coding agents. Use alongside `context-engineering`, `incremental-implementation`, and `code-review-and-quality`.

## Core Ideas

- Treat prompts as code: explicit inputs, constraints, and expected outputs.
- Reduce ambiguity: vague requests produce plausible but wrong code.
- Verify aggressively: confidence in tone is not evidence of correctness.
- Keep loops short: plan small slices, execute, verify, repeat.

## Prompt Design Checklist

- [ ] Task is specific (what to build, where to change, what not to touch).
- [ ] Acceptance criteria are explicit (tests, behavior, constraints).
- [ ] Relevant files/patterns are provided before asking for implementation.
- [ ] Output format is constrained (patch, checklist, migration plan, etc.).
- [ ] Unknowns are surfaced as questions, not silently guessed.

## Execution Checklist

- [ ] Ask for a short plan before large edits.
- [ ] Implement in small increments, each verifiable.
- [ ] Run tests/lint/typecheck after each meaningful slice.
- [ ] Keep changes scoped to the task (avoid "while I'm here" edits).
- [ ] Require evidence for claims ("where in code", "which test proved it").

## Review Checklist for AI-Generated Code

- [ ] Inputs from external systems are validated at boundaries.
- [ ] Error handling covers unhappy paths, not only happy-path demos.
- [ ] New abstractions are justified by repeated use, not anticipation.
- [ ] Naming and module boundaries match project conventions.
- [ ] Performance and security regressions are considered explicitly.

## Anti-Patterns

| Anti-Pattern | Why It Fails | Better Approach |
|---|---|---|
| "Build the whole feature end-to-end now" | Large context and large diffs hide defects | Split into thin, testable slices |
| "Looks good, ship it" | Style can mask logic errors | Require tests + concrete verification |
| "Model knows the framework docs" | Stale or incorrect assumptions happen | Ground in local code and official docs |
| "Refactor + feature + cleanup together" | Hard to review and rollback | Separate commits by concern |
| "Prompt once, never correct" | Drift accumulates | Tight feedback loops with checkpoints |

## Verification

- [ ] Implementation evidence is attached (tests, logs, output).
- [ ] Review findings are severity-labeled.
- [ ] Remaining uncertainty is documented (what could not be verified).
