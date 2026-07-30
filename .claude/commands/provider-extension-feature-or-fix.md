---
name: provider-extension-feature-or-fix
description: Workflow command scaffold for provider-extension-feature-or-fix in openclaw.
allowed_tools: ["Bash", "Read", "Write", "Grep", "Glob"]
---

# /provider-extension-feature-or-fix

Use this workflow when working on **provider-extension-feature-or-fix** in `openclaw`.

## Goal

Implements or fixes a feature in a provider extension (such as Google, Discord, Slack, Feishu, Telegram, Minimax, Exa, etc.), including code, tests, and documentation updates.

## Common Files

- `extensions/{provider}/src/*.ts`
- `extensions/{provider}/*.test.ts`
- `docs/providers/{provider}.md`
- `docs/tools/{tool}.md`
- `CHANGELOG.md`

## Suggested Sequence

1. Understand the current state and failure mode before editing.
2. Make the smallest coherent change that satisfies the workflow goal.
3. Run the most relevant verification for touched files.
4. Summarize what changed and what still needs review.

## Typical Commit Signals

- Edit or add implementation files in extensions/{provider}/src/
- Edit or add test files in extensions/{provider}/src/ or extensions/{provider}/
- Update or add documentation in docs/providers/{provider}.md, docs/tools/{tool}.md, or related docs/
- Update CHANGELOG.md

## Notes

- Treat this as a scaffold, not a hard-coded script.
- Update the command if the workflow evolves materially.