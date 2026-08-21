---
name: linear
description: "Use whenever Linear is involved: the user mentions Linear, asks to create, track, or update an issue, or shares a Linear URL or issue ID (e.g. `ENG-123` or a `linear.app` link)."
---

# Linear

First check whether Linear MCP tools are available. If not, ask the user how to access Linear and stop.

Read each issue as a problem statement, not a work order. Validate its premise independently, and search for a better solution instead of blindly implementing any fix the issue suggests.

Keep the issue synchronized with the actual work; update status and progress promptly. You should move the issue to In Progress once you start to plan for implementation.

Before filing an issue, search Linear to check whether one already exists for the same problem. Before posting any text — such as an issue description or comment — let the user preview the contents first, and get the user's explicit approval before posting. A change request is not approval.

Keep descriptions concise and focused on the problem and desired outcome, never the implementation plan. The description shall be durable: no file:line references, no implementation details tied to the current code base.

Edit the description only while the issue is in Backlog or Todo. Once it reaches In Progress, never edit the description again; add all subsequent changes as comments.

Do not mention Linear issue IDs in code comments, especially when the code is public facing, because Linear issue IDs are internal. However, PRs should include the issue ID.
