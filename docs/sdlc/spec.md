# Spec: cards_perks_downloader

> **Artifact type:** Specification (the *what*). Derived from [intent.md](intent.md), the original README, and the committed file structure.
> **Downstream artifact:** [plan.md](plan.md)
> **Status:** Reconstructed. Requirements marked **Confirmed** come directly from the original material. Requirements marked **Inferred** fill gaps the original material left open and must be validated before implementation. **Nothing in this spec is implemented.**

## 1. Scope

The Python package `cards_perks_downloader`, with:

- a core module `downloader.py`,
- a sub-package `connectors/` with initial connectors `amex.py`, `visa.py`, `mastercard.py`,
- tests under `tests/`,
- contributor documentation (`CONTRIBUTING.md`, `docs/integration_guide.md`).

## 2. Functional Requirements

| ID | Requirement | Source | Evidence level |
|---|---|---|---|
| FR-1 | The library downloads perks information for credit cards from official issuer, network, and bank websites. | README | Confirmed |
| FR-2 | Each data source is implemented as a **connector** (plugin) that follows a **standard interface**. | README | Confirmed |
| FR-3 | Initial connectors: American Express, Visa, Mastercard. | README + `connectors/*.py` | Confirmed |
| FR-4 | Connectors for local banks can be added by third-party contributors. | README | Confirmed |
| FR-5 | All connectors output data in one **standardized format**. | README | Confirmed |
| FR-6 | The library exposes simple functions so other applications can call the extraction. | README | Confirmed |
| FR-7 | A **CLI** lets users download perks from the terminal. | README | Confirmed |
| FR-8 | Data is fetched live from the source at call time ("real-time"). | README | Confirmed |
| FR-9 | The core downloader can run one connector or all registered connectors and combine the results. | `downloader.py` + README "centralize" | Inferred |
| FR-10 | A failing connector does not stop the others from returning results. | Robustness of FR-9 | Inferred |

## 3. Non-Functional Requirements

| ID | Requirement | Evidence level |
|---|---|---|
| NFR-1 | Language: Python. | Confirmed |
| NFR-2 | Installable with `pip install cards_perks_downloader`. | Confirmed (intent); packaging metadata missing |
| NFR-3 | License: Apache 2.0. | Confirmed |
| NFR-4 | Adding a connector does not require changes to the core modules. | Inferred from "modular" and "plugins" |
| NFR-5 | Network access respects each site's terms of use (reasonable request rates, identifiable user agent). | Inferred |
| NFR-6 | Tests do not depend on live websites (they use recorded fixtures). | Inferred |

## 4. Interfaces (Proposed, not original)

The original material does **not** define these. The shapes below are a minimal proposal that satisfies FR-2, FR-5, and FR-6, and they need validation.

### 4.1 Connector interface

```python
class Connector:            # in connectors/__init__.py
    name: str               # e.g. "amex"
    def fetch(self) -> list["Perk"]: ...
```

### 4.2 Standardized record (`Perk`)

| Field | Type | Notes |
|---|---|---|
| `source` | str | Connector name |
| `card` | str \| None | Card product, if the perk is specific to one |
| `country` | str \| None | ISO 3166-1 alpha-2 |
| `category` | str \| None | e.g. travel, dining, insurance |
| `title` | str | |
| `description` | str \| None | |
| `valid_from` / `valid_to` | date \| None | |
| `url` | str | Official source page |
| `retrieved_at` | datetime | Supports FR-8 traceability |

### 4.3 Public API and CLI

- `downloader.download(sources: list[str] | None = None) -> list[Perk]`
- CLI: `cards-perks-downloader [--source NAME ...] [--format json|csv] [--output PATH]`

## 5. Acceptance Criteria

- **AC-1** (FR-3, FR-5): For each initial connector, `fetch()` returns a non-empty list of valid `Perk` records against a recorded fixture.
- **AC-2** (FR-9, FR-10): `download()` with one connector forced to fail still returns the other connectors' results and reports the failure.
- **AC-3** (NFR-4): A new connector defined outside the package can be registered and used without editing `downloader.py`.
- **AC-4** (FR-7): The CLI writes valid JSON for `--format json`.
- **AC-5** (NFR-2): `pip install .` succeeds from a clean environment.

## 6. Out of Scope

See the Non-Goals in [intent.md](intent.md#6-non-goals-inferred).

## 7. Traceability to the Existing Scaffold

| Scaffold file | Requirements |
|---|---|
| `cards_perks_downloader/downloader.py` | FR-6, FR-8, FR-9, FR-10, §4.3 |
| `cards_perks_downloader/connectors/__init__.py` | FR-2, FR-4, NFR-4, §4.1 |
| `cards_perks_downloader/connectors/{amex,visa,mastercard}.py` | FR-1, FR-3, FR-5 |
| `cards_perks_downloader/__init__.py` | FR-6 (public exports) |
| `tests/test_downloader.py` | AC-1 … AC-4, NFR-6 |
| `CONTRIBUTING.md`, `docs/integration_guide.md` | FR-4 |
