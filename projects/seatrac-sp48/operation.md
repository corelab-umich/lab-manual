---
title: "Operation"
nav_order: 3
permalink: /seatrac-sp48/operation/
parent: "SeaTrac SP-48"
---
# Operation

## Scope and review status

The recovered documents support battery maintenance, ADCP/GPS setup, and packet interpretation. They do not supply a complete, verified launch, autonomous mission, emergency-stop, recovery, and shutdown procedure. A trained lab operator must complete and review those vessel-specific steps before this page serves as an operating procedure.

## Preparation records

1. Identify the vessel, current payload/wiring revision, battery condition, and operator.
2. Compare the as-built system with [Hardware]({{ '/seatrac-sp48/hardware/' | relative_url }}); resolve the ADCP power-budget discrepancy and unresolved wiring notes.
3. Check [battery storage and BMS history]({{ '/seatrac-sp48/battery/' | relative_url }}) and confirm the correct charging arrangement.
4. Recover the current network connection details from restricted lab storage; do not commit credentials.
5. Record the controller commit, selected control strategy, geographic origin, battery-capacity assumption, and mission limits.

## Telemetry verification

Start the receiver-only stack described in [Software]({{ '/seatrac-sp48/software/' | relative_url }}). Check fresh raw packets, GPS fix, heading, wind, and battery messages. Compare displayed values with the SeaTrac Dashboard and retain a short ROS bag. Resolve unit or timestamp disagreements before passing measurements to a controller.

For ADCP data acquisition, follow the documented [V200/ADCP setup]({{ '/seatrac-sp48/adcp/' | relative_url }}) and verify that VMDas receives both ADCP data and GPS messages. The original notes contain incomplete calibration steps.

## Before transmitting commands

Document and demonstrate the vessel's physical stop control, the mission-state transitions, the behavior on communications loss, and recovery from the intended mode. The repository's `allow_command=false` parameter continues to send manual commands, and the test stack includes a command publisher. Neither is a verified emergency-stop procedure.

## Required lab review

| Item | Status |
| --- | --- |
| Current build and network configuration | Historical records recovered; current setup needs confirmation |
| Battery/ADCP setup | Source notes transcribed; physical validation pending |
| Controller installation and simulation | Source reviewed; container execution unverified |
| Launch, abort, recovery, and shutdown | Complete lab procedure still needed |

Use the [operating-procedure template]({{ '/templates/#operating-procedure' | relative_url }}) to record reviewer, date, tested configuration, expected observations, and evidence.
