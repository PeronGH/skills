## Shell

Pass multiline or markdown content to a CLI through a temp file instead of an inline string, so shell quoting can't mangle it (e.g., `gh pr create --body-file`). Write that file in the temp directory, never in the working tree.
