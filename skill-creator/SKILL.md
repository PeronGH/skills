---
name: skill-creator
description: "Use this skill when the user wants to create, edit, or improve a skill. Trigger on any mention of skills, SKILL.md, or requests to capture a workflow as reusable instructions."
---

# Skill Creator

## What a Skill Is

A skill corrects the model's defaults for a specific domain. The model has broad knowledge but generic habits. A skill tells it which habits to change.

## What a Skill Is Not

- Not a reference for things the model already knows. It can carry niche knowledge the model lacks — but that goes in bundled `references/` files, not the SKILL.md body.
- Not a tutorial. Don't teach; configure.
- Not exhaustive. If a line doesn't change behavior, it's wasted tokens.

## Writing a Skill

### Frontmatter

```yaml
---
name: skill-name
description: "When to trigger. Keep it broad — one sentence."
---
```

The description is the only trigger mechanism. Make it broad enough that it fires whenever relevant. The model tends to undertrigger — err on the side of pushy.

### Body

The model has senior-level knowledge but junior-level defaults. Every line in a skill should correct a default. Cut everything else.

- State what you want directly. Don't explain why unless the "why" changes behavior.
- Prefer imperative sentences. "Use X" not "You should consider using X".
- If a section has one sentence, it doesn't need a heading — fold it into a neighbor.
- One example is worth including only if the convention is ambiguous without it. Zero is usually fine.

### Size

Ideal skill is under 100 lines. Hard limit is 200 lines.

### Bundled Resources

A skill can include more than SKILL.md:

```
skill-name/
├── SKILL.md
├── scripts/      — deterministic/repetitive tasks
├── references/   — niche knowledge the model lacks
└── assets/       — templates, fonts, etc.
```

SKILL.md stays short. Reference files carry the bulk when needed.
