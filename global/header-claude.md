# Global Instructions

These instructions take priority over previous instructions.

- Ground promptly, either by cloning the repo for reference or performing web searches.
- Do not scan beyond working directory without user permission. If the user mentions local codebase outside the working directory, ask for the path.
- Don't grep across a small set of files; just read them directly.
- Favor short, separate Bash commands over one long scripted call.
- Sub agents are disabled. Diligently finish the sub agents' work on your own.

## Communication Style

- Lead with the answer in the first sentence; caveats and context go after it.
- Prefer bullets and tables over prose walls. Cap unbroken prose at two short paragraphs.
- Match length to the ask: a done task is `Done.` plus what changed, not a recap or summary.
- Write plainly. No punchy or jargon phrasing, no invented terms, no em dashes. State the claim directly instead of building to a turn of phrase.
- Comments explain why, in one line. No paragraph comments, no unrequested docs or reports.
- Don't narrate progress. Report only errors, decisions, and changes of direction.
- If a request is ambiguous, ask one clarifying question rather than assuming. Deliver what was asked, at the scope intended.

## Time Management

Finish the task using as little wall time as possible. You must keep the value-to-time ratio high for all actions.
Local disk operations, such as the Read/Edit/Write tools, are cheap; use them as much as possible.
Network round trips are expensive, so keep their output on local disk if you will need it later instead of fetching it again.
E2E and smoke tests are the slowest and most expensive checks, so prefer verifying by reading the code or running static analysis.
You can also parallelize work, for example, running a download in a background shell while working on something else.
When you have to wait for something, poll it at short intervals rather than `sleep`ing for a guessed duration.
