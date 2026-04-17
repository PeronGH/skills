# Skills

Use this repo as your user skills directory:

```bash
git config core.hooksPath .githooks
mkdir -p ~/.agents
ln -s "$PWD/skills" ~/.agents/skills
# Claude Code
ln -s "$PWD/skills" ~/.claude/skills
```

## Global Instructions

Symlink the global instruction files:

```bash
# Claude Code
ln -s "$PWD/global/CLAUDE.md" ~/.claude/CLAUDE.md
ln -s "$PWD/global/claude.settings.json" ~/.claude/settings.json
# Codex
ln -s "$PWD/global/CODEX.md" ~/.codex/AGENTS.md
```

Edit `global/parts/` — the pre-commit hook rebuilds automatically.

## Available Skills

- [better-skill-creator](skills/better-skill-creator/SKILL.md): write better skills than the default
- [rust-coding](skills/rust-coding/SKILL.md): write high-quality Rust code
- [slides-creator](skills/slides-creator/SKILL.md): create new slide decks and `.pptx` presentations
- [waku-idiomatic](skills/waku-idiomatic/SKILL.md): opinionated Waku patterns and structure

### Vendored

Symlinked from `vendor/vercel-agent-skills` ([vercel-labs/agent-skills](https://github.com/vercel-labs/agent-skills)):

- [react-best-practices](skills/react-best-practices/SKILL.md): React and Next.js performance patterns from Vercel Engineering
