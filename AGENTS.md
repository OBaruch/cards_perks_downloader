# AGENTS.md

Guidance for anyone, human contributor or AI coding agent, who changes this repository.

## Project in one paragraph

`cards_perks_downloader` is a planned Python library for downloading and standardizing credit card perks from official issuer and network websites through pluggable connectors. The repository is a **scaffold**: every module under `cards_perks_downloader/` and `tests/` is an empty file. See [README.md](README.md) and [docs/project-context.md](docs/project-context.md).

## Source of truth

Work flows through the AI-native SDLC artifacts, in this order:

1. [docs/sdlc/intent.md](docs/sdlc/intent.md): why
2. [docs/sdlc/spec.md](docs/sdlc/spec.md): what (requirement IDs FR-*, NFR-*, AC-*)
3. [docs/sdlc/plan.md](docs/sdlc/plan.md): how (tasks T1–T10)

Every change should name the task (`T#`) and requirements it addresses. If a change goes beyond the spec, update the spec first.

## Preservation rules

- The original files are a **historical baseline**. Do not edit, reformat, or delete these as part of documentation or maintenance work:
  - `cards_perks_downloader/**/*.py`
  - `tests/test_downloader.py`
  - `CONTRIBUTING.md`, `docs/integration_guide.md`
  - `LICENSE`, `.gitignore`
  - `docs/original/README.original.md`
- Implementation work (plan phases 1–6) goes in separate, clearly labeled changes. Do not mix it with documentation-only changes.
- Label claims in documentation as **Confirmed**, **Inferred**, or **Unknown**. Never present an inference as fact.
- Do not add infrastructure (CI, containers, linters, and so on) unless a plan task calls for it.

## Commands

The repository has no build, test, or run commands yet. Plan task T1/T2 will define them. Do not invent them.
