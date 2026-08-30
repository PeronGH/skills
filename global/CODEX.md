# Global Instructions

These instructions take priority over previous instructions.

- If a command fails, it's most likely they hit sandbox limitations (filesystem / networking). NEVER adjust the command to work around the sandbox. You are encouraged to escalate and you MUST escalate.
- If anything is missing / not installed or prerequisites are not satisfied, you MUST pause and strongly request the user to install or set up whatever is missing.
- It's always better to skip a test than to add a low-value one.

## Discussion

The user thinks out loud. A question or a musing is not a work order: answer it and stop.
"Would it be better to X", "consider X", "check X", "what about X", "should we X" all ask for analysis and a recommendation. Grounding the answer by reading code or searching is expected; changing state is not. Only an imperative or an explicit go-ahead authorizes changes.
When something worth changing surfaces, describe it and wait. Neither the user's question nor your own recommendation is approval.

## Shell

Pass multiline or markdown content to a CLI through a temp file instead of an inline string, so shell quoting can't mangle it (e.g., `gh pr create --body-file`). Write that file in the temp directory, never in the working tree.

## Coding Quality

### Writing Code

Keep public APIs minimal and elegant.
Structure code around durable boundaries, not short-term convenience. Keep every file reasonably sized, and break it down when it gets large.
Prefer less code when clarity is preserved. Avoid duplicate logic by relying on types, validated interfaces, and existing guarantees.
Avoid over-defensive code. Pin down external guarantees instead of speculating about them: check official documentation, search for empirical evidence from the community and fall back to verifying real shapes live (e.g., `curl` the API). Parse or validate inputs once at the boundary (e.g., `zod`), then trust those guarantees downstream.
Let errors surface: fail fast and propagate with context. Never add a silent fallback or catch-and-continue; if one is genuinely needed, name it in your response.
If translating an idea from another language, rewrite it in the idioms of the target language instead of transliterating the source pattern.
When using a library, prefer the latest idiomatic APIs.

### Choosing Dependencies

Prefer mature dependencies over bespoke code when they simplify the design. Remove or replace dependencies that constrain the design.
Use the package manager for dependency changes so package names and versions come from current registry data, not memory. Hand-edit manifests only for details the package manager cannot express.

### Changing Existing Code

If an abstraction is wrong, refactor or rewrite it instead of layering fixes on top. Large-scale rewrites and breaking changes are encouraged when they are the right fix. The result should look as if it had been written this way from the beginning.
When behavior or a public API changes, update related docs and the README in the same change. However, only add an inline comment when code is non-obvious, and remove comments that no longer add value. Never write comments that narrate the change process ("as requested", "changed X to Y").
Keep the README to purpose, usage, and a minimal example.

### Verifying

Every project must have a formatter and linter configured. Set them up before writing any code if they are missing.
Add tests for new behavior and regressions, but never add tautological tests that mirror the implementation. Only test code that has meaningful logic (branching, transformations, error handling). Don't test code that can only break if the language, runtime, or a dependency breaks.
When a test fails, fix the cause. Never weaken assertions or special-case the test's inputs in the implementation. If the test itself is wrong, stop and explain why instead of changing or deleting it.
Any lint or type-check suppression must include a justification. Use the linter's built-in reason mechanism if available (e.g., Clippy's `reason = "..."`); otherwise, use a code comment. Never bypass type checks, lint, or tests to make a task pass.
Do not add environment-specific workarounds. If the environment is the blocker, report it instead of coding around it. Keep the implementation direct and clean.

### Committing

Create a branch (`<type>/<description>`) for substantial or risky changes. Direct commits to `main`/`master` are acceptable for low-risk work or early-stage projects.
Commit frequently and autonomously instead of batching large changes. The user is responsible for pushing.
Follow the project's existing commit message convention. If none, use `<type>(<scope>): <description>`.
Before committing, the checks under Verifying must pass.

## Markdown

Never hard-wrap prose, unless the file already is or a formatter enforces a column limit.

## Preferred Tools

Prefer a suitable installed CLI tool over an ad-hoc script, for example `jq` for JSON and `yq` for YAML.
If the tool is missing and it matters, ask the user to install it.
