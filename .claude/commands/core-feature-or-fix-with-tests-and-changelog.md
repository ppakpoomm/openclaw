---
name: core-feature-or-fix-with-tests-and-changelog
description: Workflow command scaffold for core-feature-or-fix-with-tests-and-changelog in openclaw.
allowed_tools: ["Bash", "Read", "Write", "Grep", "Glob"]
---

# /core-feature-or-fix-with-tests-and-changelog

Use this workflow when working on **core-feature-or-fix-with-tests-and-changelog** in `openclaw`.

## Goal

Implements or fixes a feature in core agent/plugin/gateway code, with corresponding tests and CHANGELOG update.

## Common Files

- `src/agents/**/*.ts`
- `src/plugins/**/*.ts`
- `src/gateway/**/*.ts`
- `src/infra/**/*.ts`
- `src/auto-reply/**/*.ts`
- `src/commands/**/*.ts`

## Suggested Sequence

1. Understand the current state and failure mode before editing.
2. Make the smallest coherent change that satisfies the workflow goal.
3. Run the most relevant verification for touched files.
4. Summarize what changed and what still needs review.

## Typical Commit Signals

- Edit or add implementation files in src/agents/, src/plugins/, src/gateway/, etc.
- Edit or add test files in the same directory (matching *.test.ts or similar).
- Update CHANGELOG.md

## Notes

- Treat this as a scaffold, not a hard-coded script.
- Update the command if the workflow evolves materially.