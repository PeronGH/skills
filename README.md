# Skills

Use this repo as your user skills directory:

```bash
mkdir -p ~/.agents
ln -s "$PWD" ~/.agents/skills
# Claude Code
ln -s "$PWD" ~/.claude/skills
```

## Global Instructions

Copy or symlink the global files into each tool's config directory:

```bash
# Claude Code
ln -s "$PWD/global/CLAUDE.md" ~/.claude/CLAUDE.md
# Codex
mkdir -p ~/.codex
ln -s "$PWD/global/AGENTS.md" ~/.codex/AGENTS.md
```

## Available Skills

- [better-skill-creator](better-skill-creator/SKILL.md): write better skills than the default
- [coding-quality](coding-quality/SKILL.md): base coding and git workflow rules
- [rust-coding](rust-coding/SKILL.md): write high-quality Rust code
- [slides-creator](slides-creator/SKILL.md): create new slide decks and `.pptx` presentations
- [waku-idiomatic](waku-idiomatic/SKILL.md): opinionated Waku patterns and structure
