## Shell

Pass multiline or markdown content to a CLI through a temp file instead of an inline string, so shell quoting can't mangle it (e.g., `gh pr create --body-file`). Write that file in the temp directory, never in the working tree.
Never wait blind. When waiting on something (CI, a deploy, a background process), prefer streaming or event-driven commands (e.g., `gh event listen`, `logs -f`) so changes arrive immediately. Only fall back to polling when no stream is available: check actual state at least every 30 seconds and print diagnostic state (e.g., job status, last log line), not just a heartbeat. Either way, exit as soon as it succeeds, fails, or stops making progress.
