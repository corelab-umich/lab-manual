---
title: "SeaTrac UDP interface"
nav_order: 9
permalink: /seatrac-sp48/interface/
parent: "SeaTrac SP-48"
---
# SeaTrac UDP interface

This is a reading guide to [SeaTrac Interface Rev4]({{ '/assets/reference/seatrac-sp48/SeaTrac-Interface-Rev4.docx' | relative_url }}) and the [controller source](https://github.com/corelab-umich/seatrac-asv-controller/tree/20fd8cc669c3cc4dfc5e0b90afe88c7c5c191522). The filename says Rev4; the document's internal history lists Version 24 dated February 15, 2023. Confirm the applicable vendor revision for current firmware.

## Packet framing

Multi-byte values are little-endian. Floats/doubles use IEEE formats. BYTE is 1 byte, WORD and signed short are 2 bytes, float is 4, and double is 8. Strings use a WORD length followed by bytes, with no trailing NUL.

| Byte position (1-based) | Field |
| --- | --- |
| 1–2 | Header `0x00 0xFF` |
| 3–4 | WORD data length |
| 5 | Message relay |
| 6 | Message type |
| 7 onward | Message-specific data |
| Final two bytes | Checksum |

Total packet length is **data length + 8**. The source uses message types 7/8 for status request/reply, 9/10 for request/reply, and 11 for commands. The repository checksum implementation is in `asv_utils/src/utils/utils.cpp`; inspect that implementation when maintaining the encoder.

## Status messages and scaling

| Sink ID | Status | Full packet length / units |
| --- | --- | --- |
| 64 | Power | 47 bytes; currents ×0.002 A, pack voltage ×0.001 V, SOC ×0.002% |
| 76 / 79 | Attitude / backup | 35 bytes; heading, pitch, roll ×0.01 degrees |
| 77 / 80 | GPS / backup | 45 bytes; lat/lon doubles in radians, speed ×0.002 knots, heading ×0.01 degrees |
| 86 | IMU | 59 bytes; roll/pitch ×0.01 degrees, rates ×0.02 degrees/s, acceleration ×0.01 m/s², heave ×0.001 m |
| 78 | Wind | 25 bytes; apparent speed ×0.002 knots, angle ×0.01 degrees, temperature ×0.01 °C, pressure ×0.01 bar |
| 82 | Propulsion | 35 bytes; propulsion mode and motor/rudder status |
| 83 | Mission | Variable length; mission state and mission data |

The power document defines pack current as load minus charger current, so charging can yield a negative value. Distinguish wire-format units from the converted ROS fields and aggregated measurement units.

## Commands used or described

Commands use message type 11. The described board relay is 8.

| Sink / function | Command payload | Full length |
| --- | --- | --- |
| Mission 83 / 5 | Mission state integer | 15 bytes |
| Propulsion 82 / 1 | Rudder angle float (degrees, starboard positive), RPM float | 19 bytes |
| Propulsion 82 / 2 | True heading float (degrees), RPM float | 19 bytes |
| Mission 83 / 7 | Latitude/longitude doubles (radians), speed float (knots) | 31 bytes |

The reviewed ROS command encoder sends **propulsion 82 / function 2**, using true heading and RPM. It does not send speed in knots directly; the command publisher converts requested knots to RPM.

The vendor table spans 0 RPM / 0 knots through 1300 RPM / 5 knots. Treat it as the documented conversion reference, not a newly calibrated speed model.

## Additional interfaces and limitations

The document also describes AIS target data and camera setup, frame transfer, and PTZ commands. Some camera byte offsets are inconsistent, and PTZ function 8 is listed twice for different operations. Resolve these with the vendor before implementing those commands.

The interface document includes a historical Silvus network example and refers to an RFI spreadsheet for addressing. This does not establish the SN11 network configuration. Use the actual vessel's restricted connection record.

Refer to [Operation]({{ '/seatrac-sp48/operation/' | relative_url }}) for the missing lab review and stop-procedure requirements; protocol fields alone do not define a safe mission sequence.
