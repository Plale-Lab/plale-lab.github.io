# CLAUDE.md

This repo is part of the Plale Lab workspace (`plale_lab/`). See `../CLAUDE.md` for cross-project context and the Karpathy Guidelines that apply lab-wide — this file covers only what's specific to `academic-website-template`.

**This is the Plale Lab's site** (PI Beth Plale), not her personal page — treat content and framing accordingly.

## Stack

Jekyll 4.3.3 (Ruby/Bundler). Plugins: `jekyll-scholar`, `jekyll-sitemap` (plus `sass-embedded`, `kramdown-parser-gfm`, `webrick`).

```bash
bundle install
bundle exec jekyll serve   # http://localhost:4000
npm install && npm run build   # only needed if editing assets/js/site.js — esbuild bundles+minifies to assets/js/site.min.js (prebuilt JS is committed)
```

`_config.yml` also sets `lab_name: "Plale Lab"`, `accent_color: "#2E9C93"`, and `nav_pages` currently enables `research` (a dropdown with 5 sub-page children), `team`, `publications`, `news`, and `contact` (talks/teaching/blogs are commented out). `nav_pages` entries can carry a `children:` list (each `{name, url}`) to render as a Bootstrap dropdown in `_includes/header.html` instead of a flat link — see the `research` entry for the pattern.

## Content

- `_data/` — `alumni.yml`, `media.yml`, `news.yml`, `team_members.yml` (no `awards.yml`/`grants.yml`, despite what you might expect). There's also `great_mathematicians_and_physicists.csv`, which is leftover template sample data, not lab content. `alumni.yml`/`media.yml` start empty (documented schema comment, conditionally rendered only if non-empty) until real data is added.
- `_pages/` — `404.md`, `blogs.md`, `contact.md`, `home.md`, `news.md`, `publications.md`, `talks.md`, `teaching.md`, `team.md`, plus `research/*.md` (one page per research area, linked from Home's research cards and the nav's Research dropdown). `team.md` renders `site.data.team_members` (cards) and `site.data.alumni` (table), each conditionally rendered only if non-empty. `news.md` renders `site.data.news` (date/headline/optional category+body). Headers inside raw HTML `<div>` blocks must use literal `<h3>`/`<h4>` tags, not `###`/`####` markdown syntax — kramdown doesn't parse markdown inside HTML block elements, and an `<a>` should never wrap block-level content (kramdown mis-parses it) — use the "stretched link" pattern instead (an inline `<a>` with `position: absolute; inset: 0` via CSS), see `.research-card-link`/`.research-more` in `_sass/layouts/_research.scss`.
- Publications are generated from `assets/ref.bib` via Jekyll Scholar — **do not hand-edit the publications page.** Scholar config: bibliography `citesty` style, `bibliography_template: bibtemplate`, sorted by year/month descending, `details_dir: bibliography`. `_pages/publications.md` (layout `gridlay`) splits entries into "Preprints" (`{% bibliography --query @unpublished %}`) and "Publications" (`{% bibliography --query !@unpublished %}`) sections, plus a client-side JS filter box and an "In the media" sidebar (`site.data.media`, hidden until non-empty).
- `logos/` — 6 Plale Lab PNG brand assets (icon, logo-primary-transparent, logo-black, logo-white, logo-white-background, logo-reverse-dark). Use these, not generic placeholders.

## Deploy

`.github/workflows/deploy.yml` ("Build and Deploy") triggers on push to branch **`source`** (not `main`) or manual dispatch. Sets up Ruby 3.2, runs `bundle exec jekyll build`, uploads via `actions/upload-pages-artifact@v5`, deploys via `actions/deploy-pages@v5`.
