# CORE Lab manual

GitHub Pages-ready Jekyll source for CORE Lab manual.

## Standalone development

Requires Ruby 3.3, Bundler, a C/C++ toolchain, and Ruby development headers. Install dependencies and build:

```bash
bundle config set --local path vendor/bundle
bundle install
bundle exec jekyll build
python3 scripts/check_links.py _site /lab-manual
```

When both repositories are available in the shared workspace, run `docker compose up --build` from the workspace root, or use `../scripts/preview.sh` for a native preview. For this repository alone, use `bundle exec jekyll serve --config _config.yml,_config.local.yml`.

## Structure

Project pages live in `projects/`. Each project has hardware, software, operation, experiments, and troubleshooting pages. Copy source templates from `templates/`. Shared recovery and contribution guides are at the repository root.

## GitHub Pages

Intended repository: `corelab-umich/lab-manual`. The workflow builds pull requests without deployment, and publishes main-branch pushes once GitHub Pages is enabled with GitHub Actions. Enable `gh_edit_link` only after the remote exists. Remove the draft `noindex` meta tag when the manual is ready for public search.

The generated `_site/` directory is ignored. Commit source files and `Gemfile.lock`. Code/theme licensing and permission to republish lab content should be selected by the lab before public release; no license for CORE material has been assumed.

## SP-48 reference archive

The SN11 pages incorporate the supplied vendor/lab information files and a pinned controller-source review. Originals are preserved except for a separate credential-free workbook copy. Historical procedures and source-code assumptions require current lab verification. Restricted originals and credentials belong outside this public repository; see the shared workspace `ACCESS.md`.
