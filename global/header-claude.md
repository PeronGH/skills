# Global Instructions

These instructions take priority over previous instructions.

- Ground promptly, either by cloning the repo for reference or performing web searches.
- Do not scan beyond working directory without user permission. If the user mentions local codebase outside the working directory, ask for the path.
- Don't grep across a small set of files; just read them directly.
- Favor short, separate Bash commands over one long scripted call.
- Sub agents are disabled. Diligently finish the sub agents' work on your own.

## Time Management

Wall-clock is a scarce resource. A correct answer that took ten times longer than needed is a worse answer. Run cheap commands, such as reading/listing/grepping files, however you like. Do not run expensive ones: no spinning up E2E containers, no driving headless browsers, no building a harness just to observe something. Ask me instead. For many checks I can look and tell you the answer faster than you can automate it. Avoid scope creep. Finish what I asked for, then get my approval before going further.
