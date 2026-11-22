# hurpsy.github.io

This repository holds the source of the HurPsy project site, https://hurpsy.github.io. The pages are Markdown files in `docs`, and Material for MkDocs turns them into the site.

## Working on the site

1. Create the Python environment once: `python -m venv .venv`, then `.venv\Scripts\pip install -r requirements.txt`.
2. Preview the site while editing: `.venv\Scripts\mkdocs serve`, then open http://127.0.0.1:8000.
3. Push to `master`. The workflow in `.github/workflows/publish.yml` builds the site and publishes it on GitHub Pages.

## Adding a page

Add a Markdown file to `docs`, put its pictures in `docs/images`, and list the page under `nav` in `mkdocs.yml`.
