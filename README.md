# CORE Lab manual

Local GitHub Pages-ready Jekyll source. No remote is configured and nothing has been published.

## Standalone development

Requires Ruby 3.3, Bundler, a C/C++ toolchain, and Ruby development headers. Install dependencies and build:

```bash
bundle config set --local path vendor/bundle
bundle install
bundle exec jekyll build
python3 scripts/check_links.py _site /lab-manual
```

For the linked local preview, use `../scripts/preview.sh` from the workspace. For this repository alone, use `bundle exec jekyll serve --config _config.yml,_config.local.yml`.

## Structure

Project pages live in `projects/`. Each project has hardware, software, operation, experiments, and troubleshooting pages. Copy source templates from `templates/`. Shared recovery and contribution guides are at the repository root.

## Future GitHub Pages

Intended repository: `corelab-umich/lab-manual`. The existing workflow builds pull requests without deployment, and publishes main-branch pushes once GitHub Pages is enabled with GitHub Actions. Confirm repository naming and audience before creating the remote. Enable `gh_edit_link` only after the remote exists. Remove the draft `noindex` meta tag when the manual is ready for public search.

The generated `_site/` directory is ignored. Commit source files and `Gemfile.lock`. Code/theme licensing and permission to republish lab content should be selected by the lab before public release; no license for CORE material has been assumed.
