# haoran1828.github.io

Personal academic homepage of Haoran Sun, built with [Jekyll](https://jekyllrb.com/) and the
[al-folio](https://github.com/alshedivat/al-folio) starter (v1.x, theme shipped as gems).

Live site: <https://haoran1828.github.io>

## Where things live

| What                         | File                                             |
| ---------------------------- | ------------------------------------------------ |
| Site title, footer, flags    | `_config.yml`                                    |
| Home page bio and photo      | `_pages/about.md`, `assets/img/prof_pic.jpg`     |
| Social icons                 | `_data/socials.yml`                              |
| News items on the home page  | `_news/*.md` (one file per item)                 |
| Blog posts                   | `_posts/YYYY-MM-DD-title.md`                     |
| Publications                 | `_bibliography/papers.bib` (format: `EXAMPLE.bib`) |

## Deploy

Every push to `main` runs `.github/workflows/deploy.yml`, which builds the site and pushes it to the
`gh-pages` branch. GitHub Pages serves that branch. There is no build step to run locally.

Two things that silently break the site: `baseurl` in `_config.yml` must stay empty (this is a user
site, not a project site), and `papers.bib` must not contain `%` comment lines (the BibTeX parser
rejects them).

## Local preview (optional)

```bash
brew install rbenv ruby-build imagemagick
rbenv install 3.3.5 && rbenv local 3.3.5
gem install bundler && bundle install
bundle exec jekyll serve   # http://localhost:4000/
```
