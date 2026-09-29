# cards_perks_downloader

> **Status: early-stage scaffold.** The repository contains the planned package structure. All source, test, and guide files are empty placeholders. None of the features described below were implemented.

## Project Overview

`cards_perks_downloader` was planned as a Python library that downloads the perks (benefits, promotions, rewards) offered by credit card issuers and banks and puts them into one standardized format for lookup and analysis.

The original README describes the intended product. The committed files contain only the structure planned for it: a core `downloader` module, a `connectors` sub-package with one module per card network (American Express, Visa, Mastercard), a test module, and placeholder docs.

## Project Context

| Item | Value | Evidence level |
|---|---|---|
| Project origin | **Personal Project** (open-source library idea) | Inferred |
| Author | Baruch Lopez | Confirmed (git history) |
| Date | March 12–13, 2025 | Confirmed (git history) |
| Stage | Initial scaffold / starting point | Confirmed (last commit is `starting point`, all code files are 0 bytes) |
| License | Apache License 2.0 | Confirmed (`LICENSE`) |
| Academic context | Nothing points to one (no course, assignment, or university references) | Unknown |

For the full reasoning, see [docs/project-context.md](docs/project-context.md).

## Problem Statement

*(From the original README; intent only, not implemented.)*

Card issuers and banks publish their perks on separate websites, each in its own format. That makes it hard to look up and compare benefits in one place. The project aimed to extract this data directly from official websites and combine it into a standardized format.

## Objective

Provide an extensible library in which each data source (issuer, network, or local bank) plugs in as a **connector** that follows a standard interface. The goal was to let contributors from different countries add connectors for their local institutions.

## Repository Structure

```
cards_perks_downloader/
├── README.md                      # This file (added during the repository restructure)
├── AGENTS.md                      # Working rules for AI coding agents / contributors
├── LICENSE                        # Apache 2.0 (original)
├── CONTRIBUTING.md                # Original, empty placeholder
├── .gitignore                     # Original Python .gitignore
├── cards_perks_downloader/        # Original Python package (empty placeholders)
│   ├── __init__.py
│   ├── downloader.py              # Planned core / public API
│   └── connectors/                # Planned per-source connectors
│       ├── __init__.py
│       ├── amex.py
│       ├── mastercard.py
│       └── visa.py
├── tests/
│   └── test_downloader.py         # Original, empty placeholder
└── docs/
    ├── integration_guide.md       # Original, empty placeholder
    ├── project-context.md         # Origin, evidence, and history
    ├── code-overview.md           # File-by-file description of the scaffold
    ├── possible-improvements.md   # Observations (not applied)
    ├── sdlc/                      # Intent → Spec → Plan artifacts
    │   ├── intent.md
    │   ├── spec.md
    │   └── plan.md
    └── original/
        └── README.original.md     # The original README, preserved verbatim
```

The Python package keeps its original location and layout, so any future implementation can build directly on the scaffold.

## Original Implementation

This repository preserves the original implementation of the project. The source code has intentionally not been refactored or modernized in order to retain the historical context and original development approach.

The source code represents the original implementation developed as a personal project. At the time of the last original commit, the implementation consisted only of empty module files that set out the planned architecture.

## Technologies

| Technology | Evidence level | Notes |
|---|---|---|
| Python | Confirmed | `.py` modules, Python package layout, Python `.gitignore` |
| pip / PyPI distribution | Intended | Mentioned in the original README; there is no packaging metadata (`setup.py` / `pyproject.toml`) |
| Web scraping / HTTP clients | Intended | Implied by "extracts data directly from official websites"; no library is named or imported |
| CLI | Intended | Mentioned in the original README; no entry point exists |

No third-party dependencies can be identified.

## How It Works

**Intended design (from the original README; not implemented):**

1. A caller uses a simple API in `downloader.py` (or a CLI) to request perks data.
2. The downloader delegates to one or more **connectors** (`connectors/amex.py`, `visa.py`, `mastercard.py`, …), each of which knows how to pull perks from one official website.
3. Every connector returns data in a **standardized format**, so results from different sources can be combined and compared.
4. New sources are added by writing a new connector that follows the shared interface.

The standard interface, the data schema, and the output format were never defined in the repository.

## Inputs and Outputs

- **Inputs (intended):** live data from official issuer, network, and bank websites.
- **Outputs (intended):** perks data in a standardized format, available through the API or the CLI.
- **Actual:** the repository contains no data, sample inputs, or generated outputs.

## Running the Project

There is nothing to run yet. The package modules are empty, and the repository has no dependency list, entry point, or test content.

The original README shows `pip install cards_perks_downloader`. The repository has no packaging metadata, and nothing here shows that a package with this name was ever published, so that command should not be treated as a working installation method for this code.

## Documentation

- [Project context](docs/project-context.md): origin, evidence, timeline, and open questions
- [Code overview](docs/code-overview.md): what each file is (and isn't)
- [Possible improvements](docs/possible-improvements.md): observations, not applied
- AI-native SDLC artifacts:
  - [Intent](docs/sdlc/intent.md): why the project exists
  - [Spec](docs/sdlc/spec.md): what it should do, derived from existing material
  - [Plan](docs/sdlc/plan.md): how the scaffold maps to the intended work
- [Original README](docs/original/README.original.md): preserved verbatim
- [AGENTS.md](AGENTS.md): rules for anyone (human or AI agent) changing this repository

## Historical Note

This repository was later reorganized and documented to improve readability and preserve the historical context of the original project. The original source code remains unchanged. The only file moved is the original `README.md`, which now lives unaltered at [`docs/original/README.original.md`](docs/original/README.original.md).

## License

Apache License 2.0. See [LICENSE](LICENSE).
