---
title: "Experiments"
nav_order: 4
permalink: /seatrac-sp48/experiments/
parent: "SeaTrac SP-48"
---
# Experiments

## Record each run

No historical experiment datasets were supplied with these information files. For every new run, preserve:

- Objective, operator, date/time and time zone, location, weather, and water conditions.
- SN11 build revision, payload configuration, battery state, and ADCP/GPS calibration.
- Controller commit, selected controller, local parameter file, origin/domain, and capacity assumptions.
- ROS bags from `.rosbags`, controller `.jld2` records, map `.images`, and VMDas recording folder.
- Startup/stop procedure version, communications interruptions, deviations, and observations.
- Raw data separately from processed outputs, with analysis code and units.

The recorder configuration splits bags at 1800 seconds and uses file-level zstd compression. Confirm the mounted output directory and available disk space before collection. VMDas uses its configured Primary Path, which must be recorded separately.

## Experiment index

| Date | Experiment ID | Build | Code commit | Data location |
| --- | --- | --- | --- | --- |
| No records migrated yet | — | — | — | — |

[Use the experiment template]({{ '/templates/#experiment-record' | relative_url }}). Keep credentials out of records shared publicly. Restricted datasets and connection records belong in lab-member storage; the public index may describe their purpose without exposing sensitive files.
