# Agent notes for haoran1828.github.io

Personal homepage built on the al-folio v1.x starter. All layouts, includes, Sass and feature JS
live in the `al_*` gems pinned in `Gemfile`; this repo holds only config and content.

## Rules

1. **`baseurl:` in `_config.yml` stays empty.** This is a GitHub _user_ site served at the domain
   root. Setting it to `/al-folio` (the upstream demo's value) breaks every asset and link.
2. **`Gemfile` and the `plugins:` list in `_config.yml` must agree.** A plugin in only one of them
   is inert. Removing gems also requires regenerating `Gemfile.lock` with a working Ruby 3.3, or
   the CI `bundle install` fails in deployment mode.
3. **No `%` comments in `_bibliography/papers.bib`.** jekyll-scholar's parser rejects them and the
   build aborts. Keep examples in `_bibliography/EXAMPLE.bib`, which is not parsed.
4. **Do not create `_layouts/`, `_includes/`, `_sass/` here** unless deliberately overriding a gem
   file; prefer `_config.yml` flags and content edits.
5. **A feature renders only if its gem is loaded, its flag is on, and the page opts in.** Otherwise
   the tag emits nothing, with no warning.

## Content map

- `_pages/about.md` — home page (bio, photo caption, which blocks appear).
- `_news/` — one file per news item; shown on the home page.
- `_posts/` — blog; `published: false` keeps a draft out of the build.
- `_bibliography/papers.bib` — publications; `selected = {true}` marks home-page entries and
  `selected_papers` in `about.md` toggles the block.
- `_data/socials.yml` — social icons, in file order.

## Deploy and verify

Push to `main`; `.github/workflows/deploy.yml` builds and force-pushes `gh-pages`. Check with
`gh run list --workflow deploy.yml --limit 3` and `curl -fsS https://haoran1828.github.io/`.
No local Ruby is installed on the maintainer's machine, so builds are verified in CI.
