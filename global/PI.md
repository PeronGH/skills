# Additional Guidelines

- The commands you run will have direct consequence on the user's device, so be extremely careful. Never modify state outside the working directory and the temporary directory. Package managers may populate their global caches, but never install anything globally.
- The bash tool already starts in the current working directory, so never prefix a command with `cd` into it; it is redundant. Run commands directly with relative paths. Use relative paths with other tools (read/write/edit) too.
- When running in Termux (working directory under `/data/data/com.termux/`): Android has no `/tmp`, so use `$TMPDIR`; and avoid wide tables, nested lists, and long lines in code blocks that may wrap on a phone screen.

## Discussion

Questions and tentative requests ("consider X", "check X", "should we X") ask for analysis, not changes. Inspect relevant code or search as useful; neither authorizes changes. Make changes only on a clear work order or explicit approval.

## Shell

Pass multiline or markdown content to a CLI through a temp file instead of an inline string, so shell quoting can't mangle it (e.g., `gh pr create --body-file`). Write that file in the temp directory, never in the working tree.

## Coding Quality

### Writing Code

Keep public APIs minimal and elegant.
Structure code around durable boundaries, not short-term convenience. Keep every file reasonably sized, and break it down when it gets large.
Prefer less code when clarity is preserved. Avoid duplicate logic by relying on types, validated interfaces, and existing guarantees.
Avoid defensive code. Verify uncertain external guarantees through documentation, search, or live data, then validate inputs once at the boundary and trust them downstream.
Let errors surface: fail fast and propagate with context. Never add a silent fallback or catch-and-continue; if one is genuinely needed, name it in your response.
If translating an idea from another language, rewrite it in the idioms of the target language instead of transliterating the source pattern.
Follow the idioms of the library version in use.

### Choosing Dependencies

Prefer mature dependencies over bespoke code when they simplify the design. Remove or replace dependencies that constrain the design.
Use the package manager for dependency changes so package names and versions come from current registry data, not memory. Hand-edit manifests only for details the package manager cannot express.

### Changing Existing Code

If an abstraction is wrong, refactor or rewrite it instead of layering fixes on top. Large-scale rewrites and breaking changes are encouraged when they are the right fix. The result should look as if it had been written this way from the beginning.
Update relevant documentation when behavior or public APIs change. Avoid comments; add one only to explain a non-obvious rationale or invariant.
Keep the README to purpose, usage, and a minimal example.

### Verifying

Use existing formatting and linting tools; add tooling only when the task warrants it.
Test meaningful behavior and regressions proportionally to risk; avoid tests that mirror the implementation or cover language, runtime, or dependency guarantees.
Fix causes of test failures; never weaken valid assertions to pass.
Justify lint or type-check suppressions; never bypass checks to make a task pass.
If the environment blocks verification, report it rather than adding a workaround.

### Committing

Create a branch (`<type>/<description>`) for substantial or risky changes. Direct commits to `main`/`master` are acceptable for low-risk work or early-stage projects.
Commit coherent changes autonomously. The user is responsible for pushing.
Follow the project's existing commit message convention. If none, use `<type>(<scope>): <description>`.
Run relevant checks before committing.

## Markdown

Never hard-wrap prose, unless the file already is or a formatter enforces a column limit.

## Preferred Tools

Prefer a suitable installed CLI tool over an ad-hoc script, for example `jq` for JSON, `yq` for YAML, and `gh` for GitHub.
If the tool is missing and it matters, ask the user to install it.
