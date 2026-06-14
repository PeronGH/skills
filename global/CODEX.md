# User Instructions

- If a command fails, it's most likely they hit sandbox limitations (filesystem / networking). NEVER adjust the command to work around the sandbox. You are encouraged to escalate and you MUST escalate.
- If anything is missing / not installed or prerequisites are not satisfied, you MUST pause and strongly request the user to install or set up whatever is missing.
- It's always better to skip a test than to add a low-value one.

# Coding Quality

## Writing Code

Keep public APIs minimal and elegant.
Structure code around durable boundaries, not short-term convenience. Keep every file reasonably sized, and break it down when it gets large.
Prefer less code when clarity is preserved. Avoid duplicate logic by relying on types, validated interfaces, and existing guarantees.
Avoid over-defensive code. Pin down external guarantees instead of speculating about them: check official documentation, validate inputs once at the boundary (e.g., `zod`), verify real shapes empirically (e.g., `curl` the API), then trust those guarantees downstream.
Let errors surface: fail fast and propagate with context. No silent fallbacks or catch-and-continue without user approval.
If translating an idea from another language, rewrite it in the idioms of the target language instead of transliterating the source pattern.
When using a library, prefer the latest idiomatic APIs.

## Choosing Dependencies

Prefer mature dependencies over bespoke code when they simplify the design. Remove or replace dependencies that constrain the design.
Use the package manager for dependency changes so package names and versions come from current registry data, not memory. Hand-edit manifests only for details the package manager cannot express.

## Changing Existing Code

If an abstraction is wrong, refactor or rewrite it instead of layering fixes on top. Large-scale rewrites and breaking changes are encouraged when they are the right fix. The result should look as if it had been written this way from the beginning.
When behavior or a public API changes, update related comments and docs in the same change.
Keep comments concise. Only comment on non-obvious code. Update a comment only when it's wrong due to code change. Never write comments that narrate the change process ("as requested", "changed X to Y").
Keep the README to purpose, usage, and a minimal example.

## Verifying

Every project must have a formatter and linter configured. Set them up before writing any code if they are missing.
Add tests for new behavior and regressions, but never add tautological tests that mirror the implementation. Only test code that has meaningful logic (branching, transformations, error handling). Don't test code that can only break if the language, runtime, or a dependency breaks.
When a test fails, fix the cause. Never weaken assertions, special-case the test's inputs in the implementation, or delete or skip failing tests without user approval.
Any lint or type-check suppression must include a justification. Use the linter's built-in reason mechanism if available (e.g., Clippy's `reason = "..."`); otherwise, use a code comment. Do not add shortcuts that bypass type checks, lint, or tests without user approval.
Do not add environment-specific workarounds without user approval. Keep the implementation direct and clean.

## Committing

Create a branch (`<type>/<description>`) for substantial or risky changes. Direct commits to `main`/`master` are acceptable for low-risk work or early-stage projects.
Commit frequently and autonomously instead of batching large changes. The user is responsible for pushing.
Follow the project's existing commit message convention. If none, use `<type>(<scope>): <description>`.
Before committing, the checks under Verifying must pass.

# Extra Tools

This environment provides the following extra CLI tools:

- `fd`
- `jq`
- `rg`
- `sd`
- `web` for searching and browsing the web. Get started with `web --help`.
- `yq`
