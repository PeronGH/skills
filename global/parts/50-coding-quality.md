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
