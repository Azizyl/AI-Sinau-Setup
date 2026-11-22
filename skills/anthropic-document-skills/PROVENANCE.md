# Provenance

Document skills from Anthropic's official skills repository, installed as a
Muse custom skill. No Claude-Code-only references were found in any of the
four SKILL.mds or the PDF reference docs — they are pure tooling guidance,
so they transfer as-is.

- Upstream: https://github.com/anthropics/skills
- Upstream commit: e4bb5d9 (e4bb5d960d87126ff3b3a8af1a104b7db67560ba)
- License: Apache 2.0. Each sub-skill folder carries its own LICENSE.txt.
- Installed: 2026-11-22
- Upstream clone (for reference only, not part of this skill):
  ~/workspace/research/anthropic-skills-upstream

## Included

- The four document sub-skills in full, each with its SKILL.md, scripts,
  and resources: docx, xlsx, pptx, pdf.
- docx: merge_runs, accept_changes, comment, the office/ validation harness
  (soffice.py, validate.py, validators, OOXML schemas), and comment
  templates.
- xlsx: recalc.py plus the office/ validation harness.
- pptx: add_slide, slide_text, thumbnail, clean, apply_theme.js, plus the
  office/ validation harness.
- pdf: 8 scripts (bounding-box checks, fillable-field checks, conversion to
  images, validation images, form-field extraction, form filling) plus
  REFERENCE.md and FORMS.md.
- This install's own router SKILL.md, skill.yaml, and this note.

## Excluded

- Every other skill in the upstream repo (creative, development, enterprise
  examples, etc.) — only the four document skills were installed, as Nman
  chose.
- The repo's .claude-plugin/ marketplace files, spec/, template/, and
  top-level README — not needed for the skills themselves.

## Notes

- The docx creation path is npm `docx-js`, not python-docx. The
  verify/edit/comment/validate sections are tool-agnostic and directly
  usable.
- Environment gaps on this VM (checked 2026-11-22; nothing was installed):
  `pandoc` not installed, `pypdf` not installed, `python-pptx` not
  installed. Present: node, npm, soffice (LibreOffice), python-docx,
  openpyxl, pandas. If a skill step needs a missing tool, say so and use an
  available route instead of silently skipping the step.
