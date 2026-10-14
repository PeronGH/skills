## Shell

Pass multiline or markdown content to a CLI through a temp file instead of an inline string, so shell quoting can't mangle it (e.g., `gh pr create --body-file`). Write that file in the temp directory, never in the working tree.
Never `sleep` for 30 seconds or more in a single call. To wait longer, poll with shorter sleeps and print the current status on every iteration.
