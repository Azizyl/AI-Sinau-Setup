# Provenance

Study-app generation skill, installed as a Muse custom skill.

- Upstream: https://github.com/phanthanhdieulinh/study-atlas (skill at
  skills/study-atlas/)
- Upstream commit: 5e7de8f (5e7de8f0ffe6dce051fe14277d4bf409e6fb2f03)
- License: MIT (see LICENSE; © 2026 Lucy Linh Phan)
- Installed: 2026-11-22
- Upstream clone (for reference only, not part of this skill):
  ~/workspace/research/study-atlas-upstream

Note: this is a very new project (created 2026-11-07; 2 stars, 4 commits
at install time). The skill is complete and self-contained, but it has
little adoption history yet.

## Included

- SKILL.md in full, with the adaptations below.
- scripts/ in full: extract.py, validate.py, build.py.
- assets/ in full: app.js, style.css (the course-agnostic study app).
- references/ in full: schema.md, writing-guide.md, subagent-brief.md,
  topic-mode.md.
- LICENSE (MIT, copied from the repo root).
- This install's own skill.yaml and this note.

## Excluded

- agents/openai.yaml (Codex/ChatGPT UI metadata — not applicable to Muse).
- .claude-plugin/ (Claude Code plugin and marketplace manifests).
- examples/demo-topic/ (a tiny demo course for testing the build).

## Adaptations for Muse

Upstream was written for Claude Code and OpenAI Codex side by side. The
following were reworded to Muse equivalents (no method content changed):

- The platform line now says the skill runs in Muse.
- Uploaded-file paths now point at Muse locations
  (`~/workspace/user/files/` for documents,
  `~/workspace/user/media_library/` for images) instead of
  `/mnt/user-data/uploads/` on claude.ai.
- The `<skill>` example path is now
  `~/workspace/custom-skills/study-atlas` instead of
  `~/.claude/skills/study-atlas` / `~/.agents/skills/study-atlas`.
- The pip-install failure note now refers to Muse's VM instead of the
  Codex sandbox, and records that pymupdf is not installed yet.
- The image-reading line now says to read PNGs with Muse's file-reading
  tool (the Codex branch was dropped).
- The parallelisation step now says to spawn Muse subagents (the
  "Agent/Task tool" wording was dropped); references/subagent-brief.md
  was reworded the same way.
- The HTML output location for uploaded files now says to save next to
  the user's files under `~/workspace/` instead of
  `/mnt/user-data/outputs/` on claude.ai.

## Environment

- Python 3.12.3 on this VM.
- **pymupdf is NOT installed** — the extractor (`scripts/extract.py`)
  needs it to read PDFs, so it must be installed before the skill can
  run on real materials.
- python-pptx is NOT installed (optional, only for .pptx sources);
  python-docx 1.1.0 is installed.
- Nothing was installed as part of this skill install.
