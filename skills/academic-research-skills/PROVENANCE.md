# Provenance

Adapted from the Academic Research Skills (ARS) suite for use as a Muse
custom skill. Muse has no Claude Code plugin system, so this install keeps
the skills as prompt-driven methodology plus standalone scripts.

- Upstream: https://github.com/imbad0202/academic-research-skills
- Upstream version: v3.24.4 (released 2026-11-19)
- Upstream commit: bd57330 (bd57330f63f4b089dde8fdef9bf5f009ecc89f0c)
- License: CC BY-NC 4.0, Copyright (c) 2026 Cheng-I Wu. Noncommercial use
  only. See LICENSE, NOTICE.md, CITATION.cff, and THIRD_PARTY.md.
- Installed: 2026-11-21
- Upstream repo size: 74 MB. This install: about 8.4 MB, 439 files plus the
  three files written for this adaptation (SKILL.md, skill.yaml, this note).

## Included

- The five sub-skills in full, each with its SKILL.md, agents, examples,
  references, and templates: deep-research, academic-paper,
  academic-paper-reviewer, academic-pipeline, sr-screener.
- shared/ in full: methodology files, reference protocols, JSON schemas for
  the Material Passport, evidence rows, revision patches, and review
  artifacts, plus the review criteria registry.
- scripts/: 79 Python files (78 modules plus the verification_gate package),
  selected as the scripts the five sub-skills reference plus their transitive
  local imports. This includes the arXiv, Crossref, OpenAlex, Semantic
  Scholar, and Chinese literature API clients, the claim audit and panel
  checkers, the acronym and tortured-phrase screeners, and the revision
  patch tools. sr-screener keeps its own 6 scripts under sr-screener/scripts.
- MODE_REGISTRY.md: the upstream index of all 35 modes across the five
  sub-skills.
- LICENSE, NOTICE.md, CITATION.cff, THIRD_PARTY.md.

## Excluded

- .claude-plugin/ (marketplace and plugin manifests), .claude/, .github/,
  hooks/ (Claude Code hooks), commands/ (the /ars-* slash commands),
  pi/ (Pi adapter), tools/ (release discipline tooling).
- tests/, evals/, plugin-evals/, plugin-evals-citation-check/,
  plugin-evals-citation-locale/: test suites and eval harnesses.
- scripts/ files not referenced by the five sub-skills: the remaining test
  files, repo self-checks, legacy scripts, fixtures, and the Zotero, Obsidian,
  and folder-scan adapters.
- audits/, docs/ (plugin design docs and changelog archive), top-level
  examples/ (mostly sample output PDFs), CHANGELOG.md (900 KB),
  README.md and its translations, CONTRIBUTING.md, GOVERNANCE.md,
  SECURITY.md, QUICKSTART.md.
- Top-level agents/: byte-identical mirrors of agent files already kept
  inside deep-research/agents and sr-screener/agents.
- One script referenced by the methodology does not exist upstream and so
  was not copied: scripts/plot_fig3.py, named only as an example in
  academic-paper/references/vlm_figure_verification.md.

## What does not transfer from Claude Code

- Hooks, slash commands (/ars-*), agent-team orchestration, and the
  marketplace manifest do not exist in Muse. Agent files are prompt
  references played in sequence, and slash commands map to modes inside the
  sub-skills.

## Runtime notes

- All 85 Python files (79 under scripts/, 6 under sr-screener/scripts/)
  compile cleanly with python3 -m py_compile. Nothing that needs network
  access or API keys was run.
- Help text runs cleanly for scripts/check_acronyms.py (both with
  PYTHONPATH=. and with python3 -m scripts.check_acronyms),
  scripts/arxiv_client.py, and sr-screener/scripts/prepare_records.py.
- Five scripts need Python packages that are not installed in this
  environment, so they compile but cannot run here: pdf_read_preflight.py
  and verify_submission_package.py need pypdf and defusedxml,
  inquiry_branch_ledger.py and tortured_phrase_screening.py need
  ruamel.yaml, and revision_roadmap.py needs referencing. Install them only
  if the user asks.
- No secrets were found in the copied files. A scan for API keys, passwords,
  and token patterns across the five sub-skills, shared/, and the API client
  scripts returned no matches.
