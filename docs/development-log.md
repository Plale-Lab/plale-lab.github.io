# PlaleLab Website Development Log

> Branch: `feat/plalelab-site-v1`  
> Baseline: `source@9647725`  
> Started: 2026-07-31  
> Plan: `D:\github\icicle\website development plan v1.md`  
> Visual source: `D:\github\icicle\global art documentation v1.md`

## Working theses

### Visual thesis

PlaleLab is presented as a warm scientific editorial surface crossed by a precise, traceable systems path: calm paper-like space, strong Ink Green typography, and small Teal/Lime evidence signals connect infrastructure to accountability.

### Content plan

1. Hero: brand, the lab's research chain, one concise promise, and direct GitHub/Projects actions.
2. Support: named projects with concrete destinations and visible evidence.
3. Detail: curated News showing selected research, interaction, and lab milestones.
4. Deeper routes: Team, Publications, and News archive.
5. Final context: concise lab contact and institutional information.

### Interaction thesis

1. A restrained hero entrance establishes hierarchy without delaying access.
2. A trace line and checkpoint sequence reveals the research chain as an explanatory device.
3. Project rows and evidence links use small border, underline, and translation changes to sharpen affordance; no autoplay or ornamental looping motion.

## Log entries

### 2026-07-31 — Phase 0: repository baseline

**Status:** complete

**Actions**

- Cloned `https://github.com/Plale-Lab/plale-lab.github.io` into `D:\github\plale-lab.github.io`.
- Confirmed default working branch `source` at commit `9647725`.
- Created feature branch `feat/plalelab-site-v1`.
- Confirmed clean worktree before edits.
- Read and adopted `awesome-design-md`, `frontend-skill`, and the in-app browser testing instructions.
- Selected warm editorial restraint as the structural reference; PlaleLab assets and tokens remain authoritative.

**Environment**

- Node.js: `v24.14.0`.
- npm: `11.9.0`.
- Docker client/server: `29.6.1`.
- System Ruby/Bundler: unavailable.
- Build strategy: use a Ruby 3.2 Docker environment matching GitHub Actions rather than modifying the system installation.

**Decisions**

- Preserve the existing Jekyll architecture.
- Do not add a CMS or backend in v1.
- Do not treat the current generic research-card grid as the final homepage composition.
- Do not copy another product's brand; only reuse warm editorial spacing, quiet borders, and restrained elevation principles.

**Outcome**

- The Dockerized baseline build passed in Ruby 3.2.
- An initial bundle-path scoping error was corrected by exporting `BUNDLE_PATH` inside the container command before `bundle check` and `bundle install`.
- The baseline route and content audit established the existing Jekyll structure as a safe implementation base.

### 2026-07-31 — Phase 1: content and brand system

**Status:** complete

**Actions**

- Copied the approved primary, reverse, black, white, icon, and social artwork from `C:\Users\izayo\Downloads\PlaleLab-delivery` into `images/brand/`.
- Replaced the favicon with the approved small PlaleLab mark.
- Added structured project data in `_data/projects.yml`; every featured project has at least two concrete destinations.
- Reworked `_data/news.yml` as a curated research, evidence-release, and lab-milestone stream.
- Added Beth Plale's ORCID to the team data.
- Set the site tokens to Ink Green, Teal, Evidence Lime, warm paper, and their dark-theme counterparts.

**Decisions**

- Use the research chain `Infrastructure → Data → Metadata → Evidence → Accountability` as the main explanatory graphic.
- Keep GitHub and inspectable artifacts prominent instead of using generic “learn more” cards.
- Preserve a curated News archive rather than automatically presenting recent publications as news.

### 2026-07-31 — Phase 2: interface implementation

**Status:** complete

**Actions**

- Rebuilt the homepage as a full-width editorial hero, a trace-path panel, a flat project evidence ledger, and a compact News signal list.
- Reworked the header, mobile navigation, footer, Team directory, Publications page, News archive, and 404 page.
- Added a skip link, visible focus states, reduced-motion behavior, semantic regions, named resource navigation, and descriptive profile links.
- Corrected internal URLs to use Jekyll's `relative_url` filter.
- Corrected page heading hierarchy to one `h1` per page with logical `h2` descendants.
- Added an accessible label to the publication search input.

**Implementation notes**

- Kramdown initially escaped the News archive's nested HTML. Wrapping the include in a `markdown=\"0\"` boundary fixed the rendered output.
- A `100vw` full-bleed hero exposed a scrollbar-width edge case on mobile. Clipping horizontal overflow at the root removed the false overflow while preserving the full-width composition.
- The site now uses a small custom navigation handler, so the global Bootstrap JavaScript payload is no longer required.
- MathJax is loaded only by pages that opt in with `mathjax: true`.
- Fonts and icon styles are preloaded asynchronously with `noscript` fallbacks.

### 2026-07-31 — Phase 3: build and interaction verification

**Status:** complete

**Builds**

- `npm run build`: pass; minified `assets/js/site.min.js` generated successfully.
- Ruby 3.2 Docker/Jekyll production build: pass.
- `git diff --check`: pass.

**Browser checks**

- Desktop homepage checked at 1440 × 900 in light and dark themes.
- Mobile homepage checked at 390 × 844 with zero horizontal overflow.
- Mobile navigation opens, reports `aria-expanded=true`, and closes when a navigation link is selected.
- Theme toggle persists the selected theme and updates its accessible label.
- Team exposes Beth Plale's email, website, Scholar, and ORCID links.
- Publications contains eight rendered entries; filtering for `Patra` returns two visible entries and clearing restores the list.
- News archive renders four semantic articles with no escaped code blocks.

### 2026-07-31 — Phase 4: QA and performance

**Status:** complete

| Check | Result | Evidence |
|---|---|---|
| Generated internal links/assets | Pass | 165 final-build references checked, 0 broken |
| Key project/news destinations | Pass | GitHub, Read the Docs, IEEE, Zenodo, and DOI redirects resolved; ACM returned its expected bot-protection 403 after DOI resolution |
| axe-core — Home | Pass | 0 violations, 36 passes |
| axe-core — Team | Pass | 0 violations, 33 passes |
| axe-core — Publications | Pass | 0 violations, 38 passes |
| axe-core — News | Pass | 0 violations, 33 passes |
| Lighthouse desktop, initial | Pass | Performance 93, Accessibility 100, Best Practices 100, SEO 100 |
| Lighthouse desktop, optimized | Pass | Performance 99, Accessibility 100, Best Practices 100, SEO 100; LCP 1.0 s |
| Lighthouse mobile, optimized | Pass | Performance 86, Accessibility 100, Best Practices 100, SEO 100 |
| Mobile Core Web Vitals lab values | Pass | LCP 3.8 s, CLS 0; local throttled Lighthouse run |
| Local preview | Running | `http://127.0.0.1:4100/`, process 24236 |

## Verification record

| Check | Result | Evidence |
|---|---|---|
| Repository cloned | Pass | Local Git branch and remote inspected |
| Baseline SHA recorded | Pass | `9647725` |
| Feature branch created | Pass | `feat/plalelab-site-v1` |
| Native Ruby available | No | `ruby` and `bundle` commands not found |
| Docker fallback available | Pass | Docker client/server `29.6.1` |
