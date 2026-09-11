# Global Instructions

These instructions take priority over previous instructions.

- Ground promptly, either by cloning the repo for reference or performing web searches.
- Do not scan beyond working directory without user permission. If the user mentions local codebase outside the working directory, ask for the path.
- Don't grep across a small set of files; just read them directly.
- Favor short, separate Bash commands over one long scripted call.
- Sub agents are disabled. Diligently finish the sub agents' work on your own.

## Time Management

Finish the task using as little wall time as possible. You must keep the value-to-time ratio high for all actions.
Local disk operations, such as the Read/Edit/Write tools, are cheap; use them as much as possible.
Network round trips are expensive, so keep their output on local disk if you will need it later instead of fetching it again.
E2E and smoke tests are the slowest and most expensive checks, so prefer verifying by reading the code or running static analysis.
You can also parallelize work, for example, running a download in a background shell while working on something else.
When you have to wait for something, poll it at short intervals rather than `sleep`ing for a guessed duration.

## Discussion

Questions and tentative requests ("consider X", "check X", "should we X") ask for analysis, not changes. Inspect relevant code or search as useful; neither authorizes changes. Make changes only on a clear work order or explicit approval.

## Shell

Pass multiline or markdown content to a CLI through a temp file instead of an inline string, so shell quoting can't mangle it (e.g., `gh pr create --body-file`). Write that file in the temp directory, never in the working tree.

## Coding Quality

### Writing Code

Do not add validation when existing types or downstream behavior already reject invalid input or handle it acceptably. Add validation only to prevent concrete harm or meet an explicit requirement.
An existing error or exception is sufficient failure behavior. Let it propagate without adding prechecks, catches, wrapping, or fallbacks unless the task explicitly requires different behavior. Preserve necessary cleanup.

### Choosing Dependencies

Use the package manager to add, remove, or update dependencies so package names and versions come from current registry data, not memory. Edit manifests by hand only for details the package manager cannot express.

### Changing Existing Code

Avoid comments unless they explain a non-obvious rationale or invariant.
Keep the README to purpose, usage, and a minimal example.

### Verifying

Use the cheapest check that establishes the requested behavior; a quick manual check is often sufficient. Stop once that behavior is established. Do not add tests by default. Add focused tests only for consequential behavior or regression risks not covered by existing tests, keeping the effort proportional to the risk.
If the environment blocks verification, report it rather than adding a workaround.

### Committing

Create a branch (`<type>/<description>`) for substantial or risky changes. Direct commits to `main`/`master` are acceptable for low-risk work or early-stage projects.
Commit coherent changes autonomously. The user is responsible for pushing.
Follow the project's existing commit message convention. If none, use `<type>(<scope>): <description>`.

## Markdown

Never hard-wrap prose, unless the file already is or a formatter enforces a column limit.

## Preferred Tools

Prefer a suitable installed CLI tool over an ad-hoc script, for example `jq` for JSON, `yq` for YAML, and `gh` for GitHub.
If the tool is missing and it matters, stop and ask the user to install it. Do not proceed without it, and never install it yourself.
