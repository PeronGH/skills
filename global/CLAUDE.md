# User Instructions

- Do not bundle unrelated commands in a single Bash tool call.
- Do not add decorative output or comments to commands whose output only you will see.
- Do not use subagents unless you can parallelize them. If you only need one subagent, do the work directly instead.
- Search whenever I mention something new or you are about to speculate. For knowledge-recall tasks, search to validate even when you're confident, except for widely known common-sense facts.
- When you search, dig past SEO garbage for authoritative, original sources. Be wary of AI-generated articles. When you find good sources, fetch the full page rather than relying on snippets. Flag community-sourced info (Reddit, forums, blogs) as such.
- Clone repos instead of web-fetching code from GitHub.

# Coding Quality

## Structure

Keep public APIs minimal. Structure code around durable boundaries, not short-term convenience. Prefer less code when clarity is preserved. Avoid duplicate logic by relying on types, validated interfaces, and existing guarantees.

## Dependencies

Prefer mature dependencies over bespoke code when they simplify the design. Remove dependencies that constrain the design.
Use the package manager for dependency changes so package names and versions come from current registry data, not memory. Hand-edit manifests only for details the package manager cannot express.

## Refactoring

If an abstraction is wrong, refactor or rewrite it instead of layering fixes on top. Large-scale rewrites and breaking changes are encouraged when they are the right fix. The result should look as if it had been written this way from the beginning.

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
Before committing, formatter, linter, and tests must pass.

## Tooling

Every project must have a formatter and linter configured. Set them up before writing any code if they are missing.

Any lint or type-check suppression must include a justification — use the linter's built-in reason mechanism if available (e.g., Clippy's `reason = "..."`), otherwise a code comment.

## Workarounds

Do not add shortcuts that bypass type checks, lint, or tests without user approval.
Do not add environment-specific workarounds without user approval. Keep the implementation direct and clean.
DIRTY
