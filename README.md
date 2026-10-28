# Crescent docs

The documentation site for Crescent, built with [Zensical](https://zensical.org).

## Work on it

```sh
python -m venv .venv
.venv\Scripts\activate          # Windows; source .venv/bin/activate elsewhere
pip install zensical
zensical serve                  # http://localhost:8000, rebuilds as you edit
```

Pages are Markdown in `docs/`. The navigation is in `zensical.toml`.

## The API reference

`docs/reference/` and the Reference part of the navigation in `zensical.toml` are generated from
Crescent itself, so they always match the API. Don't edit them by hand; they are rewritten whenever
the API changes.

## Publish

Pushing to `main` builds the site and publishes it to GitHub Pages (`.github/workflows/docs.yml`).
In the repository's settings, set **Pages → Source** to **GitHub Actions** once.

The site is at **<https://mitosisx.github.io/crescent-docs/>** (`site_url` in `zensical.toml`; the
workflow prints the same address when it finishes). The run is under the repository's **Actions**
tab, so if a page is missing that is where the build said why.
