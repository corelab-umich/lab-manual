---
title: "Hardware and build records"
nav_order: 1
permalink: /seatrac-sp48/hardware/
parent: "SeaTrac SP-48"
---
# Hardware and build records

## Recorded SN11 configuration

| Component | Recorded equipment / role |
| --- | --- |
| Platform | SeaTrac SP-48, customer SN11, hull serial 1011 |
| Main power | Six solar panels, two solar chargers, three battery packs, main battery switch, and external charger connection |
| Payload computer | Windows OnLogic computer; exact model is unspecified in the inventory |
| Router | Peplink/Pepwave MAX BR1 Pro |
| Camera | Axis F44A camera system |
| Satellite link | SkyLink 6100 |
| Navigation | V200 antenna/GPS; wind and water-speed sensors; AIS |
| Water measurements | WorkHorse ADCP |

The public system inventory removes passwords, account/connection details, and device identifiers. Lab members obtain the original connection record from restricted storage; its settings still require confirmation against the current vessel.

## Power routing

The records distinguish 12 V, 24 V, and nominal 38 V battery rails. On the expansion board, V1 and V2 select 12 V inputs, and V3 selects the battery rail. SENS1 supplies the V200 from V1; SENS3 supplies the ADCP from V3. The computer receives **regulated 12 V** from PowerRegOut1, whose input is a battery feed. The battery-feed voltage is not the computer's direct input rating.

Spare outputs and unconfigured `#N/A` entries should remain labeled unconfigured until their as-built wiring is confirmed.

## Power budget discrepancies

| Workbook section | Typical power | Busy power |
| --- | --- | --- |
| Power Summary: base vessel | 14.7 W | 19 W |
| Power Summary: payload | 30.2 W | 77.8 W |
| Power Summary: total | 44.9 W | 96.8 W |
| Main Enclosure: listed payload total | 32.2 W | 142.8 W |

The ADCP is listed as **2 / 5 W** in Power Summary and **4 / 70 W** in Main Enclosure. Resolve this discrepancy before sizing payload power or estimating runtime. These figures are recorded estimates, not newly measured consumption.

## Wiring drawings

[Boat Wiring]({{ '/assets/reference/seatrac-sp48/Boat-Wiring.pdf' | relative_url }}) is drawing 1097-SCH revision 4, dated January 13, 2023, with power, motor/navigation, and communications sheets. [SN11 Wiring]({{ '/assets/reference/seatrac-sp48/SN11-Wiring.pdf' | relative_url }}) is revision 4 dated April 25, 2023, with main-cabinet and enclosure sheets.

[![SN11 payload enclosure wiring]({{ '/assets/images/seatrac-sp48/sn11-enclosures.png' | relative_url }})]({{ '/assets/images/seatrac-sp48/sn11-enclosures.png' | relative_url }})

The enclosure drawing places the computer/expansion board in the port payload enclosure and router/video equipment in the starboard enclosure. Open the image or PDF to inspect connector details. The drawings include unresolved cable labels and a note that 12 V #3 “somehow connects” to two wireless winch chargers. That connection is unresolved, not a confirmed circuit.

Record new measurements and changes against a dated build revision rather than replacing the historical drawings.
