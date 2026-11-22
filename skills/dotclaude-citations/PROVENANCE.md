# Provenance

Three citation skills from the dotclaude "thesis" plugin, installed as a
Muse custom skill. Muse has no Claude Code plugin system, so the skills are
kept as prompt-driven methodology; the plugin manifests and hooks were
dropped.

- Upstream: https://github.com/KhaledSaeed18/dotclaude (skills at
  skills/academic/bibtex-manager, skills/academic/citation-verifier,
  skills/academic/citation-graph)
- Upstream commit: 92aac6e (92aac6e17166c2c890a01f02ea2f5e577003b957)
- License: MIT, Copyright (c) 2026 Khaled Saeed. See LICENSE.
- Installed: 2026-11-22
- Upstream clone (for reference only, not part of this skill):
  ~/workspace/research/dotclaude-upstream

## Included

- The three sub-skills in full, each with its SKILL.md:
  bibtex-manager, citation-verifier, citation-graph.
- bibtex-manager/reference/fields.md.
- LICENSE (MIT, copied from the repo root).
- This install's own router SKILL.md, skill.yaml, and this note.

## Excluded

- The other 18 skills in the dotclaude plugin (academic-writing,
  literature-search, paper-reader, latex-toolkit, systematic-review, etc.)
  — only the three citation skills were installed, as Nman chose.
- The `registry.json` files in each skill folder (Claude Code plugin
  manifests).
- The `citation-guard` hook (Claude Code hooks do not transfer to Muse).

## Adaptations for Muse

- **429 is a hard stop, not "wait and retry".** citation-graph upstream
  said "on 429 wait and retry". That conflicts with Muse's rule (a 429 is
  a hard stop for that provider in the task, no retry), so the line was
  changed to the hard stop in citation-graph/SKILL.md. The router SKILL.md
  states the rule for all three sub-skills.
- **citation-guard hook reference removed.** citation-verifier upstream
  said "The `citation-guard` hook does Level 1 continuously on every
  edit". The hook is not installed and does not transfer, so the line now
  says to re-run Level 1 manually after edits.
- **Sibling-skill references adapted.** All three sub-skills referenced
  `literature-search` and `paper-reader`, which are not installed here.
  Those references now say seeds, reading lists, and notes can come from
  anywhere (web search, the user's own lists, any notes file or folder).
