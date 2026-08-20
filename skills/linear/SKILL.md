---
name: linear
description: "Manage Linear work only when the user explicitly invokes Linear, requests a Linear action, or provides a Linear issue ID; never trigger merely because work could be tracked."
---

# Linear Workflow

## Check Access First

Before any other Linear step, check whether Linear MCP tools are available. If they are unavailable, stop and ask the user how they want you to access Linear. Do not substitute another tracker or imply that a Linear action succeeded.

Treat Linear as shared state. Inspect before mutating, keep it synchronized with reality, and follow the workspace's existing conventions instead of inventing new ones.

## Establish Context

1. Search for existing or duplicate issues before creating one.
2. Read the full issue, comments, relations, and project context before acting on it.
3. Resolve teams, statuses, labels, projects, cycles, templates, and people from live Linear data. Use names when tools accept them; do not copy opaque IDs between workspaces.
4. Infer routing from the request and surrounding context. Ask before mutating only when an unresolved choice would materially change the result.
5. Do not modify Linear when the user is only asking for analysis, a recommendation, or a draft.

## Write Good Issues

- Describe one concrete problem with a clear outcome. Use a short, directly scannable title in plain language.
- Make the description a concise problem statement, not an implementation plan. Capture the current behavior or context, who or what is affected, the impact, evidence, constraints, and desired outcome when known.
- Keep proposed solutions, technical designs, file-level change lists, and implementation checklists out of the description. Put them in comments or linked documents.
- Include only the context needed to understand the problem. Link to deeper specifications, discussions, code, designs, or customer conversations.
- For externally reported bugs and requests, preserve the reporter's own words when useful and describe the problem without prescribing an unverified solution.
- Record observed behavior, reproduction details, and expected behavior for bugs when known. Express acceptance conditions as observable outcomes rather than implementation steps.
- Scope work so one issue represents one independently completable outcome. Use sub-issues when one issue is too large but the work is too small for a project; use a project when several issues share a coordinated deliverable.
- Assign one accountable owner when ownership is known.
- Apply an existing issue template when it matches the work. Do not force every issue into the same description structure.

## Set Properties Deliberately

- Use the owning team and its workflow. Never assume status names are identical across teams.
- Set optional properties only when they communicate real information. Do not invent a priority, estimate, label, project, cycle, or due date merely to fill fields.
- Reserve Urgent for genuinely urgent work because it notifies the assignee.
- Use explicit blocked, blocking, related, parent, and duplicate relations instead of encoding relationships only in prose.
- Do not create or rename workspace configuration such as teams, statuses, labels, or projects unless the user explicitly requests it.

## Keep Work Current

- Move status when the real state of work changes. Mark an issue Done only when its outcome is complete; use the workspace's canceled or duplicate outcomes when appropriate.
- Edit the description only while the issue has never left a Backlog or Unstarted workflow category, such as Todo. Use that editing window to sharpen the problem statement.
- Once the issue has entered a Started category, never edit its description, even if it later moves backward. Add corrections, scope changes, discoveries, decisions, blockers, handoffs, and progress as comments.
- If issue history is unavailable and it is unclear whether work has started, preserve the description and use a comment.
- Link accessible implementation or review artifacts to the issue. Prefer the issue's suggested branch name and configured Git integration when available.
- Update relations, ownership, project, cycle, and priority when reality changes rather than allowing metadata to drift.

After a mutation, report the issue identifier and URL, what changed, and any unresolved decision or blocker.
