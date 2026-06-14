PARTS := $(wildcard parts/*.md)

all: CLAUDE.md CODEX.md PI.md

CLAUDE.md: header-claude.md $(PARTS)
	awk 'FNR==1 && NR!=1 {print ""} 1' $^ > $@

CODEX.md: header-codex.md $(PARTS)
	awk 'FNR==1 && NR!=1 {print ""} 1' $^ > $@

PI.md: $(PARTS)
	awk 'FNR==1 && NR!=1 {print ""} 1' $^ > $@

clean:
	rm -f CLAUDE.md CODEX.md PI.md

.PHONY: all clean
