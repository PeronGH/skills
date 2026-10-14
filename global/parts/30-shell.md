## Shell

Pass multiline or markdown content to a CLI through a temp file instead of an inline string, so shell quoting can't mangle it (e.g., `gh pr create --body-file`). Write that file in the temp directory, never in the working tree.
Each `sleep` must be under 30 seconds. A single command may wait longer by polling in a loop, as long as it prints a status line on every iteration so progress shows at least every 30 seconds.
