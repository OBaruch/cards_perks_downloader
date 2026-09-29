# Code Overview

> Every code file in this repository is **empty (0 bytes)**, exactly as committed originally. This document describes the **role each file was meant to have**, based on its name, its location, and the original README. It does not describe existing behavior, because there is none.

## Package: `cards_perks_downloader/`

| File | Size | Intended role | Evidence level |
|---|---|---|---|
| `__init__.py` | 0 B | Marks the directory as a Python package; the natural place to expose the public API | Package marker: Confirmed. Public API: Inferred |
| `downloader.py` | 0 B | Core module: coordinates connectors and exposes the "simple interface" / "extensible API" from the README; likely also the CLI's backing logic | Inferred |
| `connectors/__init__.py` | 0 B | Marks `connectors` as a sub-package; the likely place for the standard connector interface or a connector registry | Package marker: Confirmed. Interface: Inferred |
| `connectors/amex.py` | 0 B | Connector for American Express perks | Inferred (name + README) |
| `connectors/visa.py` | 0 B | Connector for Visa perks | Inferred (name + README) |
| `connectors/mastercard.py` | 0 B | Connector for Mastercard perks | Inferred (name + README) |

## Tests: `tests/`

| File | Size | Intended role |
|---|---|---|
| `test_downloader.py` | 0 B | Tests for `downloader.py` (Inferred). The test framework is Unknown. |

## Documentation placeholders

| File | Size | Intended role |
|---|---|---|
| `CONTRIBUTING.md` | 0 B | Contribution guidelines, most likely including how to submit a new connector (Inferred) |
| `docs/integration_guide.md` | 0 B | Guide for integrating a new data source as a connector (Inferred) |

These placeholders are kept empty on purpose because they are part of the original scaffold. The new documentation lives in separate files.

## Intended Component Relationships

This diagram shows the **intended** design, taken from the README and the file layout. None of these relationships exist in code.

```
             ┌───────────────────────┐
  user  ───▶ │  API / CLI (intended) │
             └──────────┬────────────┘
                        │
             ┌──────────▼────────────┐
             │     downloader.py     │  orchestration + standard output
             └──────────┬────────────┘
                        │ standard connector interface (undefined)
        ┌───────────────┼────────────────┐
        ▼               ▼                ▼
   amex.py         visa.py        mastercard.py     (+ future local-bank connectors)
        │               │                │
        ▼               ▼                ▼
   official websites (live data)
```

The project is too small, and too unimplemented, to justify a separate `architecture.md`. The diagram above records the only architecture that can be reasonably inferred.

## Dependencies

No imports exist, so no dependencies can be identified. The repository has no `requirements.txt`, `setup.py`, `setup.cfg`, or `pyproject.toml`.
