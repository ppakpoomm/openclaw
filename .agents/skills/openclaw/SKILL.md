```markdown
# openclaw Development Patterns

> Auto-generated skill from repository analysis

## Overview

This skill teaches you the core development patterns, coding conventions, and workflow automation used in the `openclaw` TypeScript backend, built with Express. You'll learn how to contribute features, fixes, and refactors to both the core logic and provider extensions, manage CI/release workflows, and maintain consistent code and test quality.

## Coding Conventions

- **File Naming:**  
  Use kebab-case for all file and directory names.  
  _Example:_  
  ```
  src/agents/message-handler.ts
  extensions/google/src/google-provider.ts
  ```

- **Import Style:**  
  Mixed usage of default and named imports.  
  _Example:_  
  ```ts
  import express from 'express';
  import { handleRequest } from './request-handler';
  ```

- **Export Style:**  
  Prefer named exports for modules.  
  _Example:_  
  ```ts
  // src/agents/message-handler.ts
  export function handleMessage(msg: string) { ... }
  ```

- **Commit Messages:**  
  Use [Conventional Commits](https://www.conventionalcommits.org/).  
  Prefixes: `fix`, `refactor`, `perf`, `docs`  
  Keep messages concise (~45 characters).  
  _Example:_  
  ```
  fix: correct provider token refresh logic
  refactor: split gateway and agent handlers
  ```

## Workflows

### Provider Extension Feature or Fix

**Trigger:** When adding or fixing a feature in a provider extension (e.g., Google, Discord, Slack, etc.)  
**Command:** `/provider-feature`

1. Edit or add implementation files in `extensions/{provider}/src/`
2. Edit or add test files in `extensions/{provider}/src/` or `extensions/{provider}/`
3. Update or add documentation in `docs/providers/{provider}.md`, `docs/tools/{tool}.md`, or related docs
4. Update `CHANGELOG.md`

_Example:_
```ts
// extensions/google/src/google-provider.ts
export function searchGoogle(query: string) { ... }
```
```ts
// extensions/google/src/google-provider.test.ts
import { searchGoogle } from './google-provider';
```

### Core Feature or Fix with Tests and Changelog

**Trigger:** When adding or fixing a feature in core OpenClaw logic (agents, plugins, gateway, etc.)  
**Command:** `/core-fix`

1. Edit or add implementation files in `src/agents/`, `src/plugins/`, `src/gateway/`, etc.
2. Edit or add test files in the same directory (matching `*.test.ts`)
3. Update `CHANGELOG.md`

_Example:_
```ts
// src/agents/auto-reply-agent.ts
export function autoReply(msg: string) { ... }
```
```ts
// src/agents/auto-reply-agent.test.ts
import { autoReply } from './auto-reply-agent';
```

### CI or Release Workflow Update

**Trigger:** When changing CI validation, release process, or workflow automation  
**Command:** `/ci-update`

1. Edit or add `.github/workflows/*.yml` files
2. Edit or add files in `scripts/` or `test/scripts/`
3. Update related documentation in `docs/ci.md`, `docs/reference/RELEASING.md`, `AGENTS.md`, etc.
4. Update `package.json` if needed

_Example:_
```yaml
# .github/workflows/ci.yml
name: CI
on: [push, pull_request]
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - run: npm ci
      - run: npm test
```

### Plugin Cache or Registry Refactor

**Trigger:** When refactoring or optimizing plugin cache/registry logic  
**Command:** `/plugin-cache-refactor`

1. Edit or add implementation files in `src/plugins/` (cache, registry, loader, etc.)
2. Edit or add corresponding test files (`*.test.ts`) in `src/plugins/`

_Example:_
```ts
// src/plugins/plugin-cache.ts
export function updateCache() { ... }
```
```ts
// src/plugins/plugin-cache.test.ts
import { updateCache } from './plugin-cache';
```

### Extension Package Batch Update

**Trigger:** When bumping or updating `package.json` files for multiple extensions  
**Command:** `/batch-extension-update`

1. Edit `package.json` files in multiple `extensions/*/` directories
2. Update `CHANGELOG.md`

_Example:_
```json
// extensions/google/package.json
{
  "name": "openclaw-google-extension",
  "version": "1.2.0"
}
```

## Testing Patterns

- **Framework:** [Vitest](https://vitest.dev/)
- **Test File Pattern:** `*.test.ts`  
  Place test files alongside implementation or in the same directory.

_Example:_
```ts
// src/agents/auto-reply-agent.test.ts
import { describe, it, expect } from 'vitest';
import { autoReply } from './auto-reply-agent';

describe('autoReply', () => {
  it('should return a reply', () => {
    expect(autoReply('hello')).toBeDefined();
  });
});
```

## Commands

| Command                  | Purpose                                                      |
|--------------------------|--------------------------------------------------------------|
| /provider-feature        | Add or fix a feature in a provider extension                 |
| /core-fix                | Add or fix a feature in core logic with tests and changelog  |
| /ci-update               | Update CI or release workflow files and related docs         |
| /plugin-cache-refactor   | Refactor or optimize plugin cache/registry logic             |
| /batch-extension-update  | Batch update extension packages and changelog                |
```