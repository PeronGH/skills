---
name: linear
description: "Manage Linear work from intake through completion. Use when searching, reading, creating, triaging, updating, or discussing Linear issues, projects, cycles, or issue IDs."
---

# Linear Workflow

Treat Linear as shared state. Inspect before mutating, keep it synchronized with reality, and follow the workspace's existing conventions instead of inventing new ones.

## Establish Context

1. Search for existing or duplicate issues before creating one.
2. Read the full issue, comments, relations, and project context before acting on it.
3. Resolve teams, statuses, labels, projects, cycles, templates, and people from live Linear data. Use names when tools accept them; do not copy opaque IDs between workspaces.
4. Infer routing from the request and surrounding context. Ask before mutating only when an unresolved choice would materially change the result.
5. Do not modify Linear when the user is only asking for analysis, a recommendation, or a draft.

## Write Good Issues

- Describe one concrete task or problem with a clear outcome. Use a short, directly scannable title in plain language.
- Keep the description concise and include only the context needed to perform the work. Link to deeper specifications, discussions, code, designs, or customer conversations.
- For externally reported bugs and requests, preserve the reporter's own words when useful and describe the problem without prescribing an unverified solution.
- Record observed behavior, reproduction details, impact, evidence, and expected behavior for bugs when known. Record the goal, constraints, and acceptance conditions for implementation work when they add useful clarity.
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
- Keep the description as the current definition of the task. Use comments for chronological progress, discoveries, decisions, blockers, handoffs, and changes that collaborators need to notice.
- Preserve material accepted context when editing. Read existing discussion and description history before rewriting established scope.
- Link accessible implementation or review artifacts to the issue. Prefer the issue's suggested branch name and configured Git integration when available.
- Update relations, ownership, project, cycle, and priority when reality changes rather than allowing metadata to drift.

After a mutation, report the issue identifier and URL, what changed, and any unresolved decision or blocker.
