# Project Context

This document rebuilds the context of `cards_perks_downloader` from the material in the repository. Each statement is labeled:

- **Confirmed**: backed directly by files or git history.
- **Inferred**: reasonably deduced, but not stated anywhere.
- **Unknown**: the repository does not provide enough information to determine it.

## Sources Analyzed

| Source | Content | Useful context |
|---|---|---|
| `README.md` (now [`original/README.original.md`](original/README.original.md)) | 1,141 bytes: description, three features, start of an installation section | **Main source.** Defines purpose, features, and intended design |
| `LICENSE` | Apache License 2.0, copyright placeholder not filled in | Intended as open source |
| `.gitignore` | Standard GitHub Python template | Language: Python |
| `cards_perks_downloader/**/*.py` | 6 files, **all 0 bytes** | Planned module structure |
| `tests/test_downloader.py` | 0 bytes | Tests were planned |
| `CONTRIBUTING.md` | 0 bytes | Outside contributions were planned |
| `docs/integration_guide.md` | 0 bytes | A connector integration guide was planned |
| Git history | 3 commits, March 12–13, 2025 | Timeline and author |

The repository contains no PDF, Word, PowerPoint, image, diagram, notebook, dataset, or configuration files.

## Classification

**Project origin: Personal Project** (*Inferred*)

Evidence:

- The repository is on the author's personal GitHub account, and the only author is Baruch Lopez (*Confirmed*).
- The README is written as a public, community-oriented open-source library ("contributors from different countries to add specific connectors"), with an Apache 2.0 license and a `CONTRIBUTING.md` placeholder (*Confirmed*).
- Nothing refers to a university, course, assignment, employer, or client (*Confirmed absence*).

The project is best described as an **early-stage personal open-source project that stopped at the scaffold stage** (*Inferred*). It could also count as a proof of concept, but no concept was actually tested in code.

## Timeline (from git history)

| Date (UTC−6) | Commit | Change |
|---|---|---|
| 2025-03-12 23:58 | `Initial commit` | GitHub-generated repository with `README.md` (one-line description), `LICENSE`, and `.gitignore` |
| 2025-03-12 23:58 | `Update README.md` | README expanded with Features and Installation sections |
| 2025-03-13 00:10 | `starting point` | Empty package, connectors, tests, and docs files added |

No further commits followed. (*Confirmed*)

## Purpose and Objective

From the original README (*Confirmed as intent*):

- Download and centralize information on perks offered by credit card issuers and banks worldwide.
- Extract the data directly from official websites. The README names American Express, Visa, MasterCard, and local banks.
- Consolidate the data into a standardized format for lookup and analysis.
- Provide:
  - **Modular connectors** (plugins) that follow a standard interface.
  - **Real-time data** fetched from official sources.
  - A **simple, extensible API** and a **CLI**.
- Distribution via `pip install cards_perks_downloader`.

## Scope

| Aspect | In the original intent | Implemented |
|---|---|---|
| Connector: American Express | Yes (`amex.py`) | No (empty) |
| Connector: Visa | Yes (`visa.py`) | No (empty) |
| Connector: Mastercard | Yes (`mastercard.py`) | No (empty) |
| Connectors for local banks | Yes (README) | No file |
| Core downloader / API | Yes (`downloader.py`) | No (empty) |
| CLI | Yes (README) | No |
| Standardized data format | Yes (README) | Not defined |
| Tests | Yes (`test_downloader.py`) | No (empty) |
| Contributor & integration docs | Yes (placeholders) | No (empty) |
| Packaging for PyPI | Yes (README) | No metadata |

## Contradictions and Gaps

1. **The README describes working features, but the code is empty.** The README is written in the present tense ("offers straightforward functions", "extracts data directly"), but no functionality exists. The README should be read as a statement of intent.
2. **The installation section is cut off.** The original README ends inside an unclosed ```` ```bash ```` code block after `pip install cards_perks_downloader`. The rest of the section (if it was ever written) is missing.
3. **The PyPI claim is unverified.** The repository has no packaging metadata, and nothing here shows that the package was published.
4. **"Worldwide" vs. local banks.** The README aims for global coverage through community connectors, but no local bank or country is named.

## Unknown

- Target countries or banks beyond the three card networks. *The original repository does not provide enough information to determine this.*
- The standard connector interface (method names, signatures, return types).
- The schema of the "standardized format" (fields, file format such as JSON or CSV, etc.).
- The scraping approach (HTML parsing, public APIs, headless browsers) and libraries.
- The intended CLI commands and options.
- The target Python version.
- Why development stopped after the initial scaffold.
