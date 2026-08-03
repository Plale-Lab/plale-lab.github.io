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

### 2026-08-03 — Phase 5: stakeholder feedback round 1

**Status:** complete

**Scope**

| Feedback item | Implementation | Status |
|---|---|---|
| ICICLE leadership card | Add a fifth featured project with Institute, Services Board, and Training Catalog links | Implemented |
| “We're active!” card | Add a sixth featured project connecting CENTRA, FAIR Digital Objects, and the DONA board | Implemented |
| ICICLE release visibility | Add a featured news item with an official Component Catalog image and source attribution | Implemented |
| Beth Plale profile | Replace placeholder, add LinkedIn | Implemented |
| Isuru Gamage profile | Normalize display name; add title, biography, Scholar, LinkedIn, GitHub, and photo | Implemented |
| William Qiu profile | Replace placeholder photo | Implemented |
| Prior affiliates | Add four LinkedIn-linked entries in a dedicated data set and Team section | Implemented |
| Preview deployment | Rebuild static output and publish to `williamQ96.github.io` | Published |

**Media decisions**

- Inspected all three supplied portraits at their original resolution.
- Tested identity-preserving square crops through the image editing workflow. The generated variants were rejected because they altered source details or baked circular masks into the bitmap.
- Rejected generated portrait variants and made deterministic square crops from the supplied originals with Sharp. The final 640 × 640 WebP files preserve the source pixels while reducing the three portraits to 45 KB, 19 KB, and 16 KB.
- The Services Board redirects anonymous visitors to a login screen. A login screenshot was rejected.
- Used the publicly posted ICICLE Component Catalog image from the official Software and Cyberinfrastructure page instead; the news item credits and links to the official source. The optimized WebP is 38 KB.

**Implementation notes**

- Six featured entries retain the existing two-column project ledger, producing three balanced rows on desktop and one column on mobile.
- News data now accepts optional image, alt text, caption, and source fields without affecting text-only entries.
- Team data now accepts LinkedIn, biography, and per-photo focal position fields.
- Isuru's full submitted biography is available in an accessible disclosure so the directory remains compact by default.
- Prior affiliates are separate from Alumni because no dates or current positions were supplied; no metadata was invented.

**Local verification**

| Check | Result | Evidence |
|---|---|---|
| JavaScript production build | Pass | `npm run build` completed and regenerated the minified site script |
| Jekyll production build | Pass | Ruby 3.2 Docker build completed without errors |
| Patch hygiene | Pass | `git diff --check` returned no errors |
| Generated internal links/assets | Pass | 168 references checked across 340 generated files, 0 broken |
| axe-core — Home | Pass | 0 violations after the entrance animation settled |
| axe-core — Team | Pass | 0 violations |
| axe-core — News | Pass | 0 violations |
| Lighthouse — Home desktop | Pass | Performance 100, Accessibility 100, Best Practices 100, SEO 100 |
| Lighthouse — Home mobile | Pass | Performance 92, Accessibility 100, Best Practices 100, SEO 100; LCP 2.9 s, CLS 0.045 |
| Lighthouse — Team desktop | Pass | Performance 99, Accessibility 100, Best Practices 100, SEO 100; LCP 0.9 s, CLS 0 |
| Responsive browser audit | Pass | Home and Team checked at 1440 × 900 and 390 × 844; 0 horizontal overflow |
| Team interactions | Pass | Biography disclosure opens correctly; profile images and all six LinkedIn destinations render |

**Publication record**

| Item | Result |
|---|---|
| Preview repository | `williamQ96/williamQ96.github.io` |
| Deployment commit | `0555a6383a077a1fe08c6bd3d77fd47405ea9a09` |
| GitHub Pages workflow | [Run 30860075852](https://github.com/williamQ96/williamQ96.github.io/actions/runs/30860075852) completed successfully |
| Live URL | [https://williamq96.github.io/](https://williamq96.github.io/) |
| Live homepage audit | Pass — six project entries, three news entries, ICICLE image loaded at 900 px natural width, 0 horizontal overflow |
| Live Team audit | Pass — six current members, four prior affiliates, six LinkedIn links, three 640 × 640 portraits, 0 horizontal overflow |
