---
name: slides-creator
description: "Use this skill any time the user wants to create a slide deck, presentation, or .pptx file from scratch. Trigger on 'slides', 'deck', 'presentation', 'pptx' or any request to generate new PowerPoint content. Do NOT use for reading or editing existing .pptx files."
---

# Slides Creator

Create presentations using `@pixel/pptx` from JSR.

## Workflow

1. **Ensure Deno is installed.** If not, install it.
2. **Fetch the current README:** `curl -sL https://github.com/PeronGH/pptx/raw/refs/heads/main/README.md`
3. **Run `deno doc jsr:@pixel/pptx`** to get up-to-date type signatures. Filter for specific symbols as needed.
4. **Write a one-shot script** in a temp directory that imports directly from `jsr:@pixel/pptx`, then run it with Deno.
5. **QA visually.** Convert the .pptx to PDF with LibreOffice, then PDF to PNG with pdftoppm. Inspect every slide image. Fix and re-verify.

Steps 2–3 are mandatory every session. Do not write code from memory.
