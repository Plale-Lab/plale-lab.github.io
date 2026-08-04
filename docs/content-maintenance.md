# PlaleLab content maintenance

The website keeps frequently edited content in YAML so project and news updates do not require layout changes.

## Projects

Edit `_data/projects.yml`. Each featured project should include:

- a short stage label aligned with the research chain;
- a concise summary and one evidence statement;
- at least two real resource links, such as documentation, source code, a dataset, results, or a paper.

The homepage renders the entries in file order.

## News

Edit `_data/news.yml`. News is curated rather than generated from the publication list. Use it for selected publications, artifact releases, collaborations, talks, and lab milestones. Set `featured: true` to include an item in the homepage signal list; the News archive includes every entry.

## Team

Edit `_data/team_members.yml` and place portraits in `images/`. Profile destinations may include email, website, Google Scholar, GitHub, and ORCID. Missing destinations are omitted automatically.

## Publications

Edit `assets/ref.bib`. Jekyll Scholar renders the bibliography and the browser-side filter uses the final citation text, so titles, authors, and years are searchable without an extra index.

## Brand assets

Approved artwork lives in `images/brand/`. Keep the existing filenames when replacing an asset so the header, hero, footer, social metadata, and favicon references remain stable.

## Local production build and preview

From the repository root, install the Ruby dependencies and run Jekyll directly:

```shell
bundle install
bundle exec jekyll serve
```

Then open `http://127.0.0.1:4000/`.

If Ruby is unavailable locally, Docker can provide the same Ruby 3.2 environment used by GitHub Actions. The following PowerShell fallback writes the production build to `_site` and serves it on port 4100:

```powershell
$siteRoot = (Get-Location).Path
$siteOut = Join-Path $siteRoot '_site'
docker run --rm -v "${siteRoot}:/src:ro" -v "${siteOut}:/output" -v plalelab-bundle:/tmp/bundle ruby:3.2-bookworm bash -lc "cp -a /src /work && cd /work && gem install bundler -v 2.5.23 --no-document >/dev/null && export BUNDLE_PATH=/tmp/bundle && (bundle check >/dev/null || bundle install >/dev/null) && JEKYLL_ENV=production bundle exec jekyll build --destination /output"
npx http-server _site -a 127.0.0.1 -p 4100 -c-1
```

Then open `http://127.0.0.1:4100/`.
