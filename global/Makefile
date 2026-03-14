PARTS := $(wildcard parts/*.md)

all: CLAUDE.md CODEX.md

CLAUDE.md: header-claude.md $(PARTS)
	cat $^ > $@

CODEX.md: header-codex.md $(PARTS)
	cat $^ > $@

clean:
	rm -f CLAUDE.md CODEX.md

.PHONY: all clean
