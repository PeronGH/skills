PARTS := $(wildcard parts/*.md)

all: CLAUDE.md CODEX.md

CLAUDE.md: header-claude.md $(PARTS)
	awk 'FNR==1 && NR!=1 {print ""} 1' $^ > $@

CODEX.md: header-codex.md $(PARTS)
	awk 'FNR==1 && NR!=1 {print ""} 1' $^ > $@

clean:
	rm -f CLAUDE.md CODEX.md

.PHONY: all clean
