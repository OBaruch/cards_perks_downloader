# Intent: cards_perks_downloader

> **Artifact type:** Intent (the *why*). Written after the fact from existing material: the original README, the file scaffold, and git history.
> **Downstream artifacts:** [spec.md](spec.md) → [plan.md](plan.md)
> **Status:** Reconstructed. The project never moved past the scaffold stage.

## 1. Problem

Credit card issuers, card networks, and banks each publish their perks (discounts, travel benefits, insurance, rewards, promotions) on their own websites, in their own formats. Anyone who wants to know which perks are available, or to compare them across cards, has to visit and read many sites by hand. *(Confirmed: original README)*

## 2. Desired Outcome

One Python library that:

- **downloads** perks data directly from official sources,
- **normalizes** it into a single standardized format, and
- **makes it available** to other programs (API) and to people (CLI),

so perks can be looked up and analyzed in one place. *(Confirmed: original README)*

## 3. Who Benefits

| Audience | Need | Evidence level |
|---|---|---|
| Developers building finance and comparison apps | A programmatic way to get normalized perks data | Inferred ("integrating data extraction into other applications") |
| Terminal users | Quick downloads without writing code | Confirmed (README mentions a CLI) |
| Open-source contributors worldwide | A clear way to add connectors for their local banks | Confirmed (README: "contributors from different countries") |

## 4. Guiding Principles

1. **Modularity.** Each data source is an independent connector behind a standard interface. *(Confirmed)*
2. **Freshness.** Data is extracted from official websites so it is as current as possible. *(Confirmed)*
3. **Simplicity and extensibility.** The public API stays small and new sources are easy to add. *(Confirmed)*
4. **Community-driven coverage.** Global coverage comes from contributed connectors, not from a central team. *(Inferred)*

## 5. Success Signals (Inferred)

- A user can get the perks of at least one source (e.g., American Express) in the standardized format with one function call or one CLI command.
- A contributor can add a new connector without changing the core downloader.
- Results from different connectors share one schema and can be merged.

## 6. Non-Goals (Inferred)

- Being an official product of, or endorsed by, any issuer or network.
- Handling cardholder accounts, credentials, or personal financial data. The perks described are public information.
- Recommending cards or giving financial advice.

## 7. Open Questions

- Which countries and banks come first after Amex, Visa, and Mastercard? *(Unknown)*
- What is the canonical output format: Python objects, JSON, CSV, or several? *(Unknown)*
- How are websites' terms of service and scraping restrictions handled? *(Unknown)*
