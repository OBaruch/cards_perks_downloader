# Possible Improvements

> **None of the items below have been applied.** They are recorded separately so that the original implementation and documentation are preserved as they were committed. Anyone who picks this project up again should treat them as a starting backlog, not as a description of the current state.

## Original documentation

1. **Truncated installation section.** The original README ends inside an unclosed ```` ```bash ```` block ([`original/README.original.md`](original/README.original.md)). A future README should close it and finish the section.
2. **Present-tense claims.** The original README describes features as if they already work. A future release should label unimplemented features as planned.
3. **License copyright placeholder.** The `LICENSE` appendix still contains `Copyright [yyyy] [name of copyright owner]`. That text is part of the standard Apache boilerplate and does not need to be edited, but a `NOTICE` file or a copyright header could name the author.
4. **Empty `CONTRIBUTING.md` and `docs/integration_guide.md`.** These should eventually explain how to write and submit a connector.

## Packaging and tooling

5. **No packaging metadata.** A `pyproject.toml` would be needed before `pip install cards_perks_downloader` could work.
6. **No declared Python version or dependencies.**
7. **No test runner configured.** `tests/test_downloader.py` exists, but no framework is chosen.

## Design questions to settle before implementation

8. **Define the connector interface.** For example, an abstract base class or protocol in `connectors/__init__.py` with a single method that returns a list of perk records.
9. **Define the standardized perk schema.** For example: source, card product, country, category, title, description, validity dates, URL, retrieved-at timestamp.
10. **Choose an extraction strategy per source.** Options include public APIs, static HTML parsing, or a headless browser for JS-rendered pages. Each site's terms of service and `robots.txt` should be reviewed.
11. **Resilience.** Scrapers break when websites change. Isolate connector failures, add timeouts and retries, and keep recorded fixtures for tests.
12. **Connector discovery.** A registry or Python entry points would let third-party packages add local-bank connectors, in line with the README's "plugins" idea.
13. **CLI.** Define commands, for example: list available connectors, download perks from one or all sources, and choose the output format.

See [`sdlc/plan.md`](sdlc/plan.md) for how these could be sequenced.
