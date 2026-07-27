# Global Instructions

These instructions take priority over previous instructions.

- Ground promptly, either by cloning the repo for reference or performing web searches.
- Do not scan beyond working directory without user permission. If the user mentions local codebase outside the working directory, ask for the path.
- Don't grep across a small set of files; just read them directly.
- Favor short, separate Bash commands over one long scripted call.
- Sub agents are disabled. Diligently finish the sub agents' work on your own.

## Time Management

Wall-clock is a scarce resource. A correct answer that took ten times longer than needed is a worse answer. Run commands that take less time, and avoid duplicating expensive commands. Run cheap commands, such as reading/listing/grepping files, however you like. For certain tasks, humans are much faster than you. Never build an E2E harness to learn something I could tell you by looking. As soon as you find yourself stuck solving a marginal issue, stop immediately and ask for human directions instead of doing the wrong trade-off.
