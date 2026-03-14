# Claude Code README

- Do not bundle unrelated commands in a single Bash tool call.
- Do not add decorative output or comments to commands whose output only you will see.
- Do not use subagents unless you can parallelize them. If you only need one subagent, do the work directly instead.
- Always load the coding-quality skill before writing or reading code.
