# dotclaude Citations

This skill routes citation work to one of three sub-skills from the
dotclaude "thesis" plugin. Read [PROVENANCE.md](PROVENANCE.md) for the
upstream source and what was kept or dropped in this adaptation.

## Choose the right sub-skill

- Use **bibtex-manager** when adding references, cleaning a messy
  bibliography, resolving duplicate keys, or converting a reading list into
  a .bib. It keeps the .bib file as the single source of truth: fetch
  verified BibTeX from a DOI, arXiv id, or title via Crossref and arXiv,
  normalise citation keys, deduplicate entries, and fix fields BibTeX and
  biblatex care about. Read
  [bibtex-manager/SKILL.md](bibtex-manager/SKILL.md) first, and
  [bibtex-manager/reference/fields.md](bibtex-manager/reference/fields.md)
  when cleaning fields.
- Use **citation-verifier** to audit every citation in a chapter, paper, or
  proposal against the .bib file and the real world: each cite key must
  exist, each entry must resolve to a live DOI or arXiv record whose title,
  authors, and year match, and each claim attributed to a source must be
  supported by that source's note or text. Use before submission, or
  whenever text was drafted with AI assistance and a fabricated reference
  would be fatal. Read [citation-verifier/SKILL.md](citation-verifier/SKILL.md)
  first.
- Use **citation-graph** to expand a set of key papers into the literature
  around them by walking the citation graph with the Semantic Scholar and
  OpenAlex APIs: backward (references), forward (citing works), and
  co-citation, scored by how many seeds connect to each candidate. Use when
  a supervisor names one seminal paper, or when checking that a
  related-work chapter has not missed a line of work. Read
  [citation-graph/SKILL.md](citation-graph/SKILL.md) first.

## Work the method in Muse

- Load only the sub-skill the task needs.
- **Rate limits are a hard stop.** A 429 from any provider (Crossref,
  OpenAlex, Semantic Scholar, arXiv) ends work against that provider in
  this task: do not wait and retry, do not sleep and retry, and do not
  switch to another endpoint, tool, or subagent for the same provider.
  Report partial progress and stop. (Upstream said "wait and retry" — that
  was changed in this adaptation; see PROVENANCE.md.)
- There is no `citation-guard` hook in Muse: re-run citation-verifier
  Level 1 manually after edits instead of expecting continuous checking.
- The sibling skills `literature-search` and `paper-reader` are **not**
  installed here. Seeds, reading lists, and notes can come from anywhere:
  web search, the user's own lists, or any notes file or folder the user
  already uses.
