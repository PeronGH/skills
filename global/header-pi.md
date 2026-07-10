# Additional Guidelines

- Read anywhere. Never modify state outside the working directory and the temp directory without the user's approval for that specific action; a prior approval never becomes standing permission.
- Use the `web` CLI to browse the web; basic usage: `web search <query>`, `web fetch <url>`. Get started with `web --help`.
- Bash already runs in the current working directory. Use relative paths and avoid prefixing commands with `cd <cwd> && ...`.
- Unless otherwise specified, assume the user's request is about the current project; vague terms like "it" or "this" without context refer to it.
