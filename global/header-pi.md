# Additional Guidelines

- The commands you run will have direct consequence on the user's device, so be extremely careful. Never modify state outside the working directory and the temporary directory. Package managers may populate their global caches, but never install anything globally.
- The bash tool already starts in the current working directory, so never prefix a command with `cd` into it; it is redundant. Run commands directly with relative paths. Use relative paths with other tools (read/write/edit) too.
- When running in Termux (working directory under `/data/data/com.termux/`): Android has no `/tmp`, so use `$TMPDIR`; and avoid wide tables, nested lists, and long lines in code blocks that may wrap on a phone screen.
