# Academic Research Skills

This skill routes academic research and writing work to one of five sub-skills adapted from the Academic Research Skills (ARS) suite v3.24.4. Read [PROVENANCE.md](PROVENANCE.md) for the upstream source and what was kept or dropped in this adaptation, and read [MODE_REGISTRY.md](MODE_REGISTRY.md) for the full list of 35 modes across the five sub-skills.

## Choose the right sub-skill

- Use deep-research when the user needs rigorous research on a topic, a literature review, a systematic review with PRISMA reporting, a meta-analysis, a fact check of claims, or Socratic help to shape a research question. Read [deep-research/SKILL.md](deep-research/SKILL.md) first and follow its mode selection guide.

- Use academic-paper when the user needs to plan, draft, revise, or format an academic paper, check citations, write an abstract, or respond to reviewer comments. Read [academic-paper/SKILL.md](academic-paper/SKILL.md) first and follow its mode selection guide.

- Use academic-paper-reviewer when the user wants a simulated multi-perspective peer review of a manuscript, a re-review of revisions, a methodology-focused review, or reviewer calibration. Read [academic-paper-reviewer/SKILL.md](academic-paper-reviewer/SKILL.md) first.

- Use academic-pipeline when the user wants the full research to publication workflow in one run, from research question to final manuscript with integrity checks and review stages. Read [academic-pipeline/SKILL.md](academic-pipeline/SKILL.md) first. It orchestrates the other sub-skills and does no substantive work itself.

- Use sr-screener when the user needs protocol-driven screening of studies for a systematic, scoping, or rapid review, with dual-reviewer title and abstract screening, full-text screening, conflict adjudication, or PRISMA 2020 flow counts. Read [sr-screener/SKILL.md](sr-screener/SKILL.md) first.

- When the request spans more than one sub-skill, start with academic-pipeline and let it sequence the work, or run the sub-skills in order and hand artifacts forward as each sub-skill describes.

- Load only the sub-skill the task needs, and load its references files only when the task reaches the step that needs them.

## Work the method in Muse

- Treat each agent file in the sub-skill agents folders as a prompt reference that defines one role and its checks, and play the roles in sequence in one conversation instead of dispatching separate agents.

- Treat the slash commands the sub-skills mention as mode names only, and run the matching mode from the sub-skill directly.

- Resolve every shared and scripts path in the sub-skills relative to this skill folder, so shared means the shared folder here and scripts means the scripts folder here.

- Run helper scripts from this skill folder with the skill folder on the Python path, for example with `cd ~/workspace/custom-skills/academic-research-skills && PYTHONPATH=. python3 scripts/check_acronyms.py --help`, or with `python3 -m scripts.check_acronyms --help` from the same folder, because the scripts import each other as a package.

- Run the sr-screener scripts directly from their own folder, for example with `python3 sr-screener/scripts/prepare_records.py --help`, because they import only their local srlib module.

- Keep the Material Passport, run ledger, and other artifacts the pipeline describes as files in the user project folder, not in this skill folder.

- Never copy or move the user manuscript or data into this skill folder.

## What does not transfer from Claude Code

- Hooks do not run in Muse, so the guardrails that hooks enforced become checks the agent performs explicitly at each step, such as confirming the research question before searching and confirming the outline before drafting.

- Slash commands do not exist in Muse, so invoke a mode by reading the sub-skill and following its mode instead of typing a command.

- Agent teams do not run as parallel subagents in Muse, so play the roles in sequence and record each role output in the conversation or in the project files.

- The marketplace manifest, plugin metadata, eval harness, tests, and release tooling from upstream are not installed here.

## Human oversight and limits

- Keep the human in the loop at every checkpoint the sub-skills define, and ask the user to confirm the research question, the outline, the screening criteria, and each stage transition before moving on.

- Never present ARS output as submission ready, and tell the user the manuscript still needs their own review plus their institution or journal checks.

- Remember that ARS checks the manuscript and the reported process, including citation existence, claim to source alignment, reported methodology, figure and table fidelity, and reporting guideline coverage, and that these checks have explicit coverage limits.

- Never claim that ARS verified the underlying empirical work, because it cannot establish that reported procedures were performed, that raw data are authentic or complete, that analyses reproduce, or that an intervention occurred as described. A study built on fabricated data can pass every ARS gate when the fabrication is consistently reported, cited, and packaged, so the user and their institution keep responsibility for the empirical work.

- Record experiment provenance only from what the user declares, and never infer from the manuscript whether the user ran experiments.

- Treat the simulated review panel as author-facing feedback only, with no publication authority.

## Language and menulis-cep4t

- Use this skill for research methodology, review method, and screening method whatever language the user writes in, because the method applies across languages.

- Use menulis-cep4t for Indonesian writing mechanics, including EYD V spelling, KBBI word choice, campus presets, and Typst or Pandoc builds, and use this skill for the research and review method around the manuscript.

- When a manuscript is in Indonesian, apply the ARS method to its structure, claims, and citations, apply menulis-cep4t to its language, and say which skill governs each part when the two overlap.

## Available connectors

- [Google Drive](/opt/hatch/connectors/google_drive/CONNECTOR.md) for finding drafts and source files the user saved in Drive.

- [Google Docs](/opt/hatch/connectors/google_docs/CONNECTOR.md) for reading drafts the user saved as Docs.

- Use `muse.connector_search` to find other connectors and `muse.skill_search` to find related skills.

- If nothing here fits, look on the web for a maintained API or MCP server and set it up with [Custom Connectors and MCPs](/opt/muse/skills/custom-connector-setup/SKILL.md), or build a custom connector.

## Websites

- [OpenAlex](https://openalex.org/) for searching scholarly works and checking citation metadata. Carry the DOI or title into the browser task and verify the work, authors, and year match.

- [Crossref](https://www.crossref.org/) for verifying DOI metadata. Carry the DOI into the browser task and verify the title, authors, and venue match.

- [arXiv](https://arxiv.org/) for finding preprints. Carry the title or arXiv identifier into the browser task and verify the paper matches before citing it.

- [Semantic Scholar](https://www.semanticscholar.org/) for searching papers and citation contexts. Carry the title or DOI into the browser task and verify the paper matches.

## Alternatives for better results

- Start with the Socratic or plan mode when the user is unsure what to research, because a sharp question saves more time than a broad search.

- Run a quick mode first for a fast brief, then run the full mode only when the brief shows the topic is worth the deeper pass.

- Use sr-screener for the screening step of a systematic review instead of screening inside deep-research, because the screener keeps decisions traceable and produces PRISMA counts.

## What was verified and what was not

- All 85 Python scripts in scripts and in sr-screener scripts compile cleanly with `python3 -m py_compile`, and the sr-screener scripts need only the standard library plus openpyxl, which is installed.

- The help text of check_acronyms, arxiv_client, and prepare_records runs cleanly with the invocation shown above, with no network use.

- The API clients for arXiv, Crossref, OpenAlex, Semantic Scholar, and Chinese literature were not run, because they need network access, and they were compile checked only.

- Five scripts need Python packages that are not installed here, so they compile but cannot run until the user installs the packages. The scripts are pdf_read_preflight and verify_submission_package, which need pypdf and defusedxml, inquiry_branch_ledger and tortured_phrase_screening, which need ruamel.yaml, and revision_roadmap, which needs referencing. Do not install these packages without the user asking.

- The method files were copied from upstream without running the eval harness, so the methodology is untested in Muse and the first real run should be checked against the sub-skill steps.
