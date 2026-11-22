# Provenance

Symbolic mathematics skill from the K-Dense-AI scientific-agent-skills
collection, installed as a Muse custom skill.

- Upstream: https://github.com/K-Dense-AI/scientific-agent-skills (skill at
  skills/sympy/)
- Upstream commit: ec59a29 (ec59a29a03d5c40f73ab40878df04860bc00e876)
- License: MIT (see LICENSE; © 2025 K-Dense Inc.)
- Installed: 2026-11-22
- Upstream clone (for reference only, not part of this skill):
  ~/workspace/research/scientific-agent-skills-upstream (sparse, blobless
  clone — only skills/sympy and skills/matplotlib were checked out)

## Included

- SKILL.md in full, with no adaptations (see below).
- references/ in full: advanced-topics.md, code-generation-printing.md,
  core-capabilities.md, core_capabilities.md, matrices-linear-algebra.md,
  physics-mechanics.md, review.md.
- LICENSE (MIT, copied from the repo root).
- This install's own skill.yaml and this note.

## Excluded

- The other 179 skills in the upstream collection — only sympy and
  matplotlib were installed, as Nman chose.

## Adaptations for Muse

None. No Claude-Code-only references (hooks, slash commands, MCP servers,
plugin manifests) were found in the skill; it transfers as-is.

## Environment

- Python 3.12.3 on this VM.
- SymPy 1.12 is installed, but the skill was reviewed against and requires
  SymPy 1.14.0 — minor gap. Most examples work on 1.12, but
  version-sensitive behaviour (e.g. newer solvers, printing) should be
  checked against the installed version before relying on it.
- NumPy/SciPy are optional extras for some examples; a C/Fortran compiler
  is only needed for compiled wrappers, not for emitting source.
- Nothing was installed as part of this skill install.
