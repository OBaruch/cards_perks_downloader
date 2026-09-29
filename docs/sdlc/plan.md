# Plan: cards_perks_downloader

> **Artifact type:** Plan (the *how*). Derived from [spec.md](spec.md) and the existing scaffold.
> **Status:** No phase has been started. This plan records how the original scaffold maps onto the intended work. It is not a record of completed work.

## 0. Current State (Baseline)

| Item | State |
|---|---|
| Package structure (`cards_perks_downloader/`, `connectors/`) | Present, all files empty |
| Tests (`tests/test_downloader.py`) | Present, empty |
| Contributor docs (`CONTRIBUTING.md`, `docs/integration_guide.md`) | Present, empty |
| Packaging metadata | Absent |
| Repository documentation | Added during the repository restructure (README, `docs/`, this SDLC set) |

**Preservation rule:** the original empty files are the historical baseline. Future implementation work must go in separate, clearly labeled changes (see [AGENTS.md](../../AGENTS.md)).

## 1. Phases

Each phase is a small, reviewable change that ends with passing tests.

### Phase 1: Foundations
- Add packaging metadata (`pyproject.toml`) and declare the Python version. → NFR-2, AC-5
- Choose a test runner and add a smoke test to `tests/`. → NFR-6
- **Done when:** `pip install .` works and the test suite runs.

### Phase 2: Contracts
- Define the `Perk` record and the `Connector` interface in `connectors/__init__.py`. → FR-2, FR-5, §4.1–4.2
- Add a connector registry (built-ins plus externally registered connectors). → FR-4, NFR-4, AC-3
- **Done when:** a dummy connector can be registered and returns validated `Perk` objects.

### Phase 3: Core downloader
- Implement `download()` in `downloader.py`: select connectors, run them, merge the results, isolate failures. → FR-6, FR-8, FR-9, FR-10, AC-2
- Export the public API from `cards_perks_downloader/__init__.py`.
- **Done when:** AC-2 and AC-3 pass using dummy connectors.

### Phase 4: Initial connectors
- For each of `amex.py`, `visa.py`, `mastercard.py`, one at a time:
  1. Identify the official perks page(s) and review the terms of use and `robots.txt`. → NFR-5
  2. Record fixtures.
  3. Implement `fetch()` → `list[Perk]`.
  4. Test against the fixtures. → AC-1
- **Done when:** AC-1 passes for all three.

### Phase 5: CLI
- Add a console entry point that wraps `download()` with source selection and JSON/CSV output. → FR-7, AC-4

### Phase 6: Contributor enablement
- Write `CONTRIBUTING.md` and `docs/integration_guide.md` (how to write, test, and submit a connector). → FR-4
- Update the README so it describes the implemented features.

## 2. Task Breakdown for Agentic Execution

Each task is sized so that one agent or one contributor can complete and verify it in one change.

| # | Task | Files | Verifies | Depends on |
|---|---|---|---|---|
| T1 | Packaging metadata | `pyproject.toml` (new) | AC-5 | none |
| T2 | Test runner and smoke test | `tests/` | NFR-6 | T1 |
| T3 | `Perk` and `Connector` contracts | `connectors/__init__.py` | FR-2, FR-5 | T2 |
| T4 | Connector registry | `connectors/__init__.py` | AC-3 | T3 |
| T5 | `download()` orchestration | `downloader.py`, `__init__.py` | AC-2 | T4 |
| T6 | Amex connector | `connectors/amex.py`, fixtures | AC-1 | T5 |
| T7 | Visa connector | `connectors/visa.py`, fixtures | AC-1 | T5 |
| T8 | Mastercard connector | `connectors/mastercard.py`, fixtures | AC-1 | T5 |
| T9 | CLI | `downloader.py` or new `cli.py` | AC-4 | T5 |
| T10 | Contributor docs | `CONTRIBUTING.md`, `docs/integration_guide.md` | FR-4 | T4 |

T6–T8 can run in parallel.

## 3. Risks

| Risk | Mitigation |
|---|---|
| Source websites change layout or block scraping | Fixture-based tests, per-connector isolation, clear error reporting |
| Terms of service forbid automated access | Review before each connector; prefer official feeds or APIs where they exist |
| Perks vary by country and card product | `country` and `card` fields in `Perk`; one connector per region where needed |
| Schema churn as connectors are added | Settle the `Perk` schema in Phase 2, before any real connector exists |

## 4. Open Decisions

Carried over from [spec.md](spec.md) and [intent.md](intent.md#7-open-questions): output format(s), scraping libraries, Python version, and the first set of local banks.
