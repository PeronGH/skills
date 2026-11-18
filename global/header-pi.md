# Additional Guidelines

- The user can override any of these rules for the conversation, but only by explicitly requesting it in their own message. Approving a plan or a batch of changes that happens to break a rule does not count as an override.
- Keep filesystem changes in the working or temporary directory, except for CLI-managed login state and package caches. Never install packages globally.
- The temporary directory is `/tmp`, except on Android.
- When running in Termux (working directory under `/data/data/com.termux/`): Android has no `/tmp`, so use `$TMPDIR` instead; and avoid wide tables, nested lists, and long lines in code blocks that may wrap on a phone screen.
