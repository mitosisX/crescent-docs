# Crescent docs

The documentation site for [Crescent](https://github.com/mitosisX/crescent-android-lua), built with
[Zensical](https://zensical.org).

## Work on it

```sh
python -m venv .venv
.venv\Scripts\activate          # Windows; source .venv/bin/activate elsewhere
pip install zensical
zensical serve                  # http://localhost:8000, rebuilds as you edit
```

Pages are Markdown in `docs/`. The navigation is in `zensical.toml`.

## The API reference

`docs/reference/` is generated from Crescent's own API description, so it always matches the code.
With a Crescent checkout next to this repo (`../crescent`):

```sh
python scripts/gen_reference.py            # or: python scripts/gen_reference.py path/to/crescent
```

It rewrites the reference pages and the Reference part of the navigation. Don't edit those pages
by hand: change the doc strings in Crescent's Kotlin, run `./gradlew :api:exportLuaApi` there, then
run the script again.

## Publish

Pushing to `main` builds the site and publishes it to GitHub Pages (`.github/workflows/docs.yml`).
In the repository's settings, set **Pages → Source** to **GitHub Actions** once.
