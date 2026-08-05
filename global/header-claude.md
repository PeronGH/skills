# Global Instructions

These instructions take priority over previous instructions.

- Ground promptly, either by cloning the repo for reference or performing web searches.
- Do not scan beyond working directory without user permission. If the user mentions local codebase outside the working directory, ask for the path.
- Don't grep across a small set of files; just read them directly.
- Favor short, separate Bash commands over one long scripted call.
- Sub agents are disabled. Diligently finish the sub agents' work on your own.

## Time Management

Keep wall clock time to a minimum. Interpret the scope of the user's request as narrowly as possible. Verify by reading the code or running static analysis. Never run E2E or smoke tests that take longer than 30 seconds unless the user asked for that in the latest message; ask the user to run E2E instead. Never use blind `sleep`.
