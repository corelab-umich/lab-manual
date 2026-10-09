---
title: "Migration and recovery"
nav_order: 7
permalink: /recovery/
---
# Migration and recovery

## Recover an older build

1. Identify its former owner and request notes, source files, schematics, configuration backups, and example datasets through the lab's usual channels.
2. Copy originals into approved shared storage without overwriting them.
3. Record original filename, source person/machine, date recovered, and known build/software versions.
4. Add a short Markdown summary linking to those originals. Mark uncertain facts and missing files.
5. Reproduce the configuration when practical, then have a maintainer review the resulting instructions.

## Recovery register

| Project/build | Former owner | Material sought | Shared location | Status | New maintainer |
| --- | --- | --- | --- | --- | --- |
| SeaTrac SP-48 | To identify | Builds, setup, experiment notes | To assign | Not started | To assign |
| Energy-Harvesting Kite | To identify | Build variants, rigs, controls, data | To assign | Not started | To assign |
| Saildrone | To identify | Platform identity, setup, missions | To assign | Not started | To assign |

## Handle conflicting notes

Retain both sources and describe the conflict. Record which configuration was tested; do not silently merge incompatible procedures. An old laptop's working folder should be linked to a known code commit where possible.

## Handoff before leaving the lab

Use the [student handoff template]({{ '/templates/#student-handoff' | relative_url }}), assign a successor, and confirm that another student can access all linked material. Update the project maintainer field and recovery register.
