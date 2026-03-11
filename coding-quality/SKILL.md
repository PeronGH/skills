---
name: coding-quality
description: "Use this skill for all types of coding tasks. Always load it when you are coding, alongside any language-specific skills."
---

# Coding Quality

## Structure

Keep public APIs minimal. Structure code around durable boundaries, not short-term convenience. Prefer less code when clarity is preserved. Avoid duplicate logic by relying on types, validated interfaces, and existing guarantees.

## Dependencies

Prefer mature dependencies over bespoke code when they simplify the design. Remove dependencies that constrain the design.

## Refactoring

If an abstraction is wrong, refactor or rewrite it instead of layering fixes on top. Large-scale rewrites and breaking changes are encouraged when they are the right fix. Do not introduce hacky workarounds without user approval.

## Idioms

If translating an idea from another language, rewrite it in the idioms of the target language instead of transliterating the source pattern.

## Testing

Add tests for new behavior and regressions. Only test code that has meaningful logic (branching, transformations, error handling). Don't test code that can only break if the language, runtime, or a dependency breaks.

## Documentation

When behavior or a public API changes, update related comments and docs in the same change. Keep the README to purpose, usage, and a minimal example.

## Before Commit

Before committing, formatter, linter, and tests must pass.
