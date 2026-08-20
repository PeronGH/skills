---
name: linear
description: "Use whenever Linear is involved: the user mentions Linear, asks to create, track, or update an issue, or shares a Linear URL or issue ID (e.g. `ENG-123` or a `linear.app` link)."
---

# Linear

First check whether Linear MCP tools are available. If not, ask the user how to access Linear and stop.

Keep the issue synchronized with the actual work; update status and progress promptly.

Keep descriptions concise and focused on the problem and desired outcome, never the implementation plan. The description shall be durable: no file:line references, no implementation details tied to the current code base.

Edit the description only while the issue is in Backlog or Todo. Once it reaches In Progress, never edit the description again; add all subsequent changes as comments.

Do not mention Linear issue IDs in code comments, especially when the code is public facing, because Linear issue IDs are internal. However, PRs should include the issue ID.
