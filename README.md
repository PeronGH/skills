# Skills

Use this repo as your user skills directory:

```bash
git config core.hooksPath .githooks
mkdir -p ~/.agents
ln -s "$PWD" ~/.agents/skills
# Claude Code
ln -s "$PWD" ~/.claude/skills
```

## Global Instructions

Symlink the global instruction files:

```bash
# Claude Code
ln -s "$PWD/global/CLAUDE.md" ~/.claude/CLAUDE.md
# Codex
mkdir -p ~/.codex
ln -s "$PWD/global/CODEX.md" ~/.codex/AGENTS.md
```

Edit `global/parts/` — the pre-commit hook rebuilds automatically.

## Available Skills

- [better-skill-creator](better-skill-creator/SKILL.md): write better skills than the default
- [rust-coding](rust-coding/SKILL.md): write high-quality Rust code
- [slides-creator](slides-creator/SKILL.md): create new slide decks and `.pptx` presentations
- [waku-idiomatic](waku-idiomatic/SKILL.md): opinionated Waku patterns and structure
