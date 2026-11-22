# Anthropic Document Skills

This skill routes document work to one of four sub-skills from Anthropic's
official skills repository. Read [PROVENANCE.md](PROVENANCE.md) for the
upstream source, what was kept, and the environment gaps on this VM.

## Choose the right sub-skill

- Use **docx** when the user wants to create, read, edit, or manipulate Word
  documents (.docx) or Word templates (.dotx): professional formatting,
  tables of contents, headings, page numbers, letterheads, images,
  find-and-replace, tracked changes, or comments. Read
  [docx/SKILL.md](docx/SKILL.md) first.
- Use **xlsx** when a spreadsheet file is the primary input or output:
  open, read, edit, or fix .xlsx, .xlsm, .xltx, .csv, or .tsv files
  (columns, formulas, formatting, charts, messy-data cleanup), create a
  spreadsheet from scratch, or convert between tabular formats. Read
  [xlsx/SKILL.md](xlsx/SKILL.md) first.
- Use **pptx** when a .pptx or .potx file is involved in any way: creating
  slide decks, reading or extracting text from presentations, editing
  existing decks, combining or splitting slide files, templates, layouts,
  speaker notes, or comments. Read [pptx/SKILL.md](pptx/SKILL.md) first.
- Use **pdf** when the user wants to do anything with PDF files: reading or
  extracting text/tables, merging or splitting, rotating pages, watermarks,
  creating new PDFs, filling forms, encrypting/decrypting, extracting
  images, or OCR on scanned PDFs. Read [pdf/SKILL.md](pdf/SKILL.md) first,
  and [pdf/REFERENCE.md](pdf/REFERENCE.md) / [pdf/FORMS.md](pdf/FORMS.md)
  when the task reaches the step that needs them.

## Work the method in Muse

- Load only the sub-skill the task needs, and load its scripts only when the
  task reaches the step that needs them.
- Resolve every scripts path in the sub-skills relative to that sub-skill's
  folder, and run helper scripts from that folder, for example with
  `cd ~/workspace/custom-skills/anthropic-document-skills/docx && python3 scripts/merge_runs.py --help`.
- The docx creation path is npm `docx-js`, not python-docx — see
  [docx/SKILL.md](docx/SKILL.md). The verify/edit/comment/validate sections
  are tool-agnostic and directly usable.
- Several tools the sub-skills assume are not installed on this VM (pandoc,
  pypdf, python-pptx — see PROVENANCE.md). If a step needs one of them, say
  so and use an available route (e.g. LibreOffice via `soffice`, or
  python-docx / openpyxl, which are installed) instead of silently skipping
  the step.
