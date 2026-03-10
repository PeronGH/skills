---
name: coding-quality
description: "Use this skill for coding tasks as a base layer of cross-cutting code-quality rules. It complements more specific language or framework skills rather than replacing them."
---

# Coding Quality

## Structure

Keep public APIs minimal. Structure code around durable boundaries, not short-term convenience. Prefer less code when clarity is preserved. Avoid duplicate logic by relying on types, validated interfaces, and existing guarantees.

## Dependencies

Prefer mature dependencies over bespoke code when they simplify the design. Remove dependencies that constrain the design.

## Correctness

If an abstraction is wrong, refactor or rewrite it instead of layering fixes on top. Do not introduce hacky workarounds without user approval.
If translating an idea from another language, rewrite it in the idioms of the target language instead of transliterating the source pattern.

## Testing

Add tests for new behavior and regressions. Every integration test must have a comment explaining what it covers and why it exists; add `Origin:` or `Spec:` when applicable.

## Documentation

When behavior or a public API changes, update related comments and docs in the same change. Keep the README to purpose, usage, and a minimal example.

## Before Commit

Before committing, formatter, linter, and tests must pass.
