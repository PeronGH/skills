---
name: coding-quality
description: "Use this skill for all types of coding tasks. It encodes specific conventions that must be followed. Always load it when you are coding, alongside any language-specific skills."
---

# Coding Quality

## Structure

Keep public APIs minimal. Structure code around durable boundaries, not short-term convenience. Prefer less code when clarity is preserved. Avoid duplicate logic by relying on types, validated interfaces, and existing guarantees.

## Dependencies

Prefer mature dependencies over bespoke code when they simplify the design. Remove dependencies that constrain the design.
Use the package manager for dependency changes so package names and versions come from current registry data, not memory. Hand-edit manifests only for details the package manager cannot express.

## Refactoring

If an abstraction is wrong, refactor or rewrite it instead of layering fixes on top. Large-scale rewrites and breaking changes are encouraged when they are the right fix. Do not introduce hacky workarounds without user approval.

## Idioms

If translating an idea from another language, rewrite it in the idioms of the target language instead of transliterating the source pattern.

## Testing

Add tests for new behavior and regressions. Only test code that has meaningful logic (branching, transformations, error handling). Don't test code that can only break if the language, runtime, or a dependency breaks.

## Documentation

When behavior or a public API changes, update related comments and docs in the same change. Keep the README to purpose, usage, and a minimal example.

## Git

Create a branch (`<type>/<description>`) for substantial or risky changes. Direct commits to `main`/`master` are acceptable for low-risk work or early-stage projects.
Commit frequently and autonomously instead of batching large changes.
Follow the project's existing commit message convention. If none, use `<type>(<scope>): <description>`.

## Tooling

Every project must have a formatter and linter configured. Set them up before writing any code if they are missing.

Any lint or type-check suppression must include a justification — use the linter's built-in reason mechanism if available (e.g., Clippy's `reason = "..."`), otherwise a code comment.

## Before Commit

Before committing, formatter, linter, and tests must pass.
