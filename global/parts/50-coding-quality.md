## Coding Quality

### Writing Code

Keep public APIs minimal and elegant.
Structure code around durable boundaries, not short-term convenience. Keep every file reasonably sized, and break it down when it gets large.
Prefer less code when clarity is preserved. Avoid duplicate logic by relying on types, validated interfaces, and existing guarantees.
Avoid defensive code. Do not add validation merely because data crosses a boundary. Rely on existing types and downstream behavior when invalid input already fails clearly or has an acceptable outcome. Add validation only to prevent a concrete harmful outcome or satisfy an explicit contract.
An existing error or exception is sufficient failure behavior by default. Let it propagate; do not add prechecks, catches, wrapping, or fallbacks unless the task explicitly requires different behavior. Preserve necessary cleanup.
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
Prefer the cheapest verification that establishes the requested behavior. A quick manual check is often sufficient; use existing automated checks when convenient. Do not add tests by default. Add them when they protect consequential behavior or a plausible regression that existing coverage misses. Keep test code and setup proportionate to the logic and risk; avoid building test infrastructure for a small change. Stop once the relevant behavior is established.
Fix causes of test failures; never weaken valid assertions to pass.
Justify lint or type-check suppressions; never bypass checks to make a task pass.
If the environment blocks verification, report it rather than adding a workaround.

### Committing

Create a branch (`<type>/<description>`) for substantial or risky changes. Direct commits to `main`/`master` are acceptable for low-risk work or early-stage projects.
Commit coherent changes autonomously. The user is responsible for pushing.
Follow the project's existing commit message convention. If none, use `<type>(<scope>): <description>`.
Run relevant checks before committing.
