---
title: "Information files and provenance"
nav_order: 6
permalink: /seatrac-sp48/references/
parent: "SeaTrac SP-48"
---
# Information files and provenance

## Source archive

The six supplied files came from the lab's SN11 information folder. The five DOCX/PDF downloads are unchanged copies. The workbook is a separate credential-free copy; its original remains untouched in restricted local storage.

| Download | Recorded scope/date |
| --- | --- |
| [ADCP + Antenna Setup.docx]({{ '/assets/reference/seatrac-sp48/ADCP-Antenna-Setup.docx' | relative_url }}) | Initial release April 15, 2023 |
| [Battery Tips.docx]({{ '/assets/reference/seatrac-sp48/Battery-Tips.docx' | relative_url }}) | Battery/storage/Dashboard guidance; revision date unspecified |
| [Boat Wiring.pdf]({{ '/assets/reference/seatrac-sp48/Boat-Wiring.pdf' | relative_url }}) | 1097-SCH revision 4, January 13, 2023, three sheets |
| [SeaTrac Interface Rev4.docx]({{ '/assets/reference/seatrac-sp48/SeaTrac-Interface-Rev4.docx' | relative_url }}) | Internal Version 24, February 15, 2023 |
| [SN11 System Info — credential-free.xlsx]({{ '/assets/reference/seatrac-sp48/SN11-System-Info-redacted.xlsx' | relative_url }}) | Five sheets: System Info, Power Summary, Main Enclosure, Expansion Board, Wire Data |
| [SN11 Wiring.pdf]({{ '/assets/reference/seatrac-sp48/SN11-Wiring.pdf' | relative_url }}) | 1097-SCH revision 4, April 25, 2023, two sheets |

Controller documentation is based on [commit `20fd8cc669c3`](https://github.com/corelab-umich/seatrac-asv-controller/tree/20fd8cc669c3cc4dfc5e0b90afe88c7c5c191522), inspected October 9, 2026. Source documents were read as reference material; their procedures were not executed.

## Missing or unresolved information

- Current as-built configuration, firmware, and complete launch/abort/recovery/shutdown procedure.
- `V200Settings`, the `_ADCP` directory, `300 Defaults.ini`, ADCP setup INI files, and the manufacturer WorkHorse manual.
- Completed ADCP calibration procedure and the unanswered out-of-water test question.
- Conflicting ADCP power estimates and unresolved cable/winch-charger wiring notes.
- Camera protocol offsets and duplicate PTZ function identifiers.
- Validated container installation, controller selection, and current geographic/power model parameters.

## Public and restricted material

General setup guidance and reviewed, credential-free files may be published here. Passwords, access tokens, sensitive connection records, and restricted experiment data must be stored in a separate private repository or authenticated service. Hiding a navigation link or adding a browser password prompt does not protect a statically published file.

Authentication must protect the sensitive pages **and their downloads** before delivery. Do not place restricted material in this public repository's Git history, build artifacts, or search index. Hosting and lab-member access will be configured separately; no protected remote service has been created yet.
