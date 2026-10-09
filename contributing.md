---
title: "Contributing"
nav_order: 6
permalink: /contributing/
---
# Contributing

## Add or update a page

1. Edit the appropriate Markdown file under `projects/` or copy a template from `templates/`.
2. Include a title, unique permalink, parent project, and navigation order in the YAML front matter.
3. Add the applicable build/software revision, author, status, and review record in the content.
4. Use `relative_url` for internal links so the manual works beneath `/lab-manual/`.
5. Build and inspect the local preview. The build script checks internal links and anchors.
6. Once remotes exist, submit changes on a branch and request review from a project maintainer.

## Review checklist

- Can another student reproduce the described setup from the stated starting point?
- Are commands and expected outputs recorded with version context?
- Are asset and dataset locations stable and accessible to the lab?
- Are draft steps and unresolved assumptions clearly marked?
- Has the operating procedure been reviewed for this exact platform configuration?

## Files and ownership

Use descriptive filenames and dated experiment IDs. Keep large datasets and CAD exports in approved shared storage, with stable links in the [asset register]({{ '/assets-register/' | relative_url }}). A new drawing or firmware change should create a new revision record.

## Review status

A draft becomes reviewed only after a named reviewer records the date, applicable revisions, and evidence. `last_modified_date` is an edit timestamp, not a verification date. Keep historical pages and label them archived when superseded.
