---
title: "ADCP and antenna setup"
nav_order: 8
permalink: /seatrac-sp48/adcp/
parent: "SeaTrac SP-48"
---
# ADCP and antenna setup

[ADCP + Antenna Setup]({{ '/assets/reference/seatrac-sp48/ADCP-Antenna-Setup.docx' | relative_url }}) was initially released April 15, 2023. It references configuration files and a manufacturer manual that were not supplied; recover them before attempting a complete setup.

## V200 GPS antenna

The notes first check GPS messages in TeraTerm at **4800 baud**, with the correct COM port. They then use PocketMax 4.0 to load `V200Settings` through Quick Config / File Load Config, save settings, power-cycle the GPS, and verify output at **19200 baud**.

The `V200Settings` file is missing from this archive. Do not substitute an invented configuration.

## WorkHorse ADCP serial interface

Confirm whether the ADCP is configured for RS-232 or RS-422. The notes reference the manufacturer's `WorkHorseOperationManual_Jan20.pdf` for the internal switch and end-cap procedure (pages 125 and 98). That manual and a referenced switch figure were not supplied. Opening the instrument requires the correct manufacturer instructions; this page does not provide a complete disassembly procedure. The notes record cross-pattern tightening and a final torque of **5.6 N·m (50 in·lb)**.

For serial setup, the notes use RDI Tools (June 2018), BBTalk with the WorkHorse device, and initially **9600 baud, no parity, 8 data bits, 1 stop bit**. After a break response, `cb511` sets **19200 baud**, followed by a power cycle and reconnection.

| Command | Purpose stated in the notes |
| --- | --- |
| `PS0` | System information |
| `PA` | Pre-deployment initialization/check |
| `PC1` | Beam check out of water, using the described rubbing test |
| `PT200` | Onboard tests; the notes explicitly question whether this can be performed out of water |

The unanswered `PT200` question remains unresolved; do not treat it as an approved out-of-water step.

## VMDas acquisition configuration

The notes copy the customer's `_ADCP` folder to `C:\_ADCP`, load `300 Defaults.ini`, and edit the following data options:

- ADCP and NMEA1 COM ports under Communications.
- Correct ADCP setup INI file.
- Recording Primary Path.
- Both NAV inputs set to NMEA1.
- Averaging intervals of **15 / 60 seconds** for bottom-track/calibration work and **60 / 300 seconds** for normal collection.

The `_ADCP` folder, `300 Defaults.ini`, and ADCP setup files were not supplied. Record the exact recovered files and revisions when available.

For the source's acquisition sequence, power GPS and ADCP, connect BBTalk at 19200 baud, send a break and `PA`, close BBTalk, then use VMDas File → Collect Data → Play. Confirm text in both ADCP and GPS panes; stop collection when finished.

## Calibration notes needing completion

The document discusses bottom tracking, comparing BOT Direction with NAV Made Good Degrees, and setting EA heading alignment in Transform options. It questions whether saving the INI occurs automatically. These are incomplete calibration notes, not a validated calibration recipe. Preserve a reviewed calibration record with the corresponding hardware and data.
