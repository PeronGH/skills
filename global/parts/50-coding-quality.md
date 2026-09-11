## Coding Quality

### Writing Code

Do not add validation when existing types or downstream behavior already reject invalid input or handle it acceptably. Add validation only to prevent concrete harm or meet an explicit requirement.
An existing error or exception is sufficient failure behavior. Let it propagate without adding prechecks, catches, wrapping, or fallbacks unless the task explicitly requires different behavior. Preserve necessary cleanup.

### Choosing Dependencies

Use the package manager to add, remove, or update dependencies so package names and versions come from current registry data, not memory. Edit manifests by hand only for details the package manager cannot express.

### Changing Existing Code

Update relevant documentation when behavior or public APIs change. Avoid comments; add one only to explain a non-obvious rationale or invariant.
Keep the README to purpose, usage, and a minimal example.

### Verifying

Use existing formatting and linting tools; add tooling only when the task warrants it.
Use the cheapest sufficient check; quick manual verification often suffices. Stop once behavior is established. Don't add tests by default; reserve proportional tests for consequential behavior or uncovered regression risks.
Fix causes of test failures; never weaken valid assertions to pass.
Justify lint or type-check suppressions; never bypass checks to make a task pass.
If the environment blocks verification, report it rather than adding a workaround.

### Committing

Create a branch (`<type>/<description>`) for substantial or risky changes. Direct commits to `main`/`master` are acceptable for low-risk work or early-stage projects.
Commit coherent changes autonomously. The user is responsible for pushing.
Follow the project's existing commit message convention. If none, use `<type>(<scope>): <description>`.
Run relevant checks before committing.
