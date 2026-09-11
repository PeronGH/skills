# Global Instructions

These instructions take priority over previous instructions.

- If a command fails, it's most likely they hit sandbox limitations (filesystem / networking). NEVER adjust the command to work around the sandbox. You are encouraged to escalate and you MUST escalate.
- If anything is missing / not installed or prerequisites are not satisfied, you MUST pause and strongly request the user to install or set up whatever is missing.
- It's always better to skip a test than to add a low-value one.

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
Run relevant checks before committing.

## Markdown

Never hard-wrap prose, unless the file already is or a formatter enforces a column limit.

## Preferred Tools

Prefer a suitable installed CLI tool over an ad-hoc script, for example `jq` for JSON, `yq` for YAML, and `gh` for GitHub.
If the tool is missing and it matters, stop and ask the user to install it. Do not proceed without it, and never install it yourself.
