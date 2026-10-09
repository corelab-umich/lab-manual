---
title: "SeaTrac SP-48"
nav_order: 3
permalink: /seatrac-sp48/
has_children: true
---
# SeaTrac SP-48

The SeaTrac SP-48 autonomous surface vessel is used for CORE Lab research in control, sensing, and energy-efficient autonomous systems. These pages collect the recovered **SN11, hull serial 1011** hardware records and the lab's [ROS 2 controller repository](https://github.com/corelab-umich/seatrac-asv-controller).

The supplied wiring and interface records date to 2023. They describe a historical configuration; confirm the current vessel configuration before applying them. The software review uses commit `20fd8cc669c3cc4dfc5e0b90afe88c7c5c191522`. Physical operating procedures and container startup have not been validated on the vessel.

## Documentation

- [Hardware, wiring, and power budgets]({{ '/seatrac-sp48/hardware/' | relative_url }})
- [Controller installation, configuration, and ROS topics]({{ '/seatrac-sp48/software/' | relative_url }})
- [Operation and telemetry checks]({{ '/seatrac-sp48/operation/' | relative_url }})
- [Battery maintenance and storage]({{ '/seatrac-sp48/battery/' | relative_url }})
- [ADCP and V200 antenna setup]({{ '/seatrac-sp48/adcp/' | relative_url }})
- [SeaTrac UDP interface]({{ '/seatrac-sp48/interface/' | relative_url }})
- [Experiment records and data preservation]({{ '/seatrac-sp48/experiments/' | relative_url }})
- [Troubleshooting]({{ '/seatrac-sp48/troubleshooting/' | relative_url }})

## Download the recovered information files

| File | What it contains |
| --- | --- |
| [ADCP + Antenna Setup]({{ '/assets/reference/seatrac-sp48/ADCP-Antenna-Setup.docx' | relative_url }}) | V200 configuration, ADCP serial setup, VMDas collection, and unfinished calibration notes. |
| [Battery Tips]({{ '/assets/reference/seatrac-sp48/Battery-Tips.docx' | relative_url }}) | Storage intervals, charge methods, BMS history, and alert settings. |
| [Boat Wiring]({{ '/assets/reference/seatrac-sp48/Boat-Wiring.pdf' | relative_url }}) | Three sheets covering power, propulsion/navigation, and communications. |
| [SeaTrac Interface Rev4]({{ '/assets/reference/seatrac-sp48/SeaTrac-Interface-Rev4.docx' | relative_url }}) | UDP framing, status messages, commands, and camera/AIS interfaces. |
| [SN11 System Info — credential-free copy]({{ '/assets/reference/seatrac-sp48/SN11-System-Info-redacted.xlsx' | relative_url }}) | Equipment inventory, power budgets, enclosure allocation, and expansion-board configuration. Passwords, account/connection details, and device identifiers are removed. |
| [SN11 Wiring]({{ '/assets/reference/seatrac-sp48/SN11-Wiring.pdf' | relative_url }}) | Two sheets covering the main cabinet and payload enclosures. |

[Reference dates, limitations, and missing files]({{ '/seatrac-sp48/references/' | relative_url }}) identify what still needs recovery. Sensitive originals belong in the lab's restricted storage, outside this public repository.
