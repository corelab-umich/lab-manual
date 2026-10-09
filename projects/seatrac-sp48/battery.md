---
title: "Battery maintenance and storage"
nav_order: 7
permalink: /seatrac-sp48/battery/
parent: "SeaTrac SP-48"
---
# Battery maintenance and storage

This page summarizes [Battery Tips]({{ '/assets/reference/seatrac-sp48/Battery-Tips.docx' | relative_url }}). Confirm the installed battery and charger configuration before use; the values below are taken from the supplied notes.

## Cell voltage and storage

The notes give **2.7 V per cell** as a damage boundary and **3.1 V per cell** as a practical empty level. They identify a cell-to-cell difference above **0.1 V** as possible imbalance or damage. Do not use the damage boundary as a normal operating target.

A fully charged boat left on its trailer with the system on can lose roughly half its charge in two weeks; the notes recommend checking every two weeks. With the main battery switch off, charge can last months; the notes recommend checking every three months by powering on and connecting the Dashboard. Switch-off storage has no logging or alerts.

## Charging arrangements in the notes

| Method | Recorded guidance |
| --- | --- |
| Solar panels | Modest sunlight can maintain charge against small trailer loads. |
| Red external fast charger | Approximately 10% charge per hour; the notes describe leaving this charger connected. Confirm the actual charger's operating instructions. |
| Small supply at solar input | Remove one panel and use its MC4 solar-input connection with a supply set to **20 V and no more than 5 A**. This is a solar-input arrangement, not a direct battery connection. |

![MC4 polarity reference from Battery Tips]({{ '/assets/images/seatrac-sp48/mc4-polarity.jpeg' | relative_url }})

Check the actual polarity markings and wiring before connecting the supply; the photograph is a reference for the documented connection.

## Dashboard checks

1. Connect and use the Check button.
2. Under Data Reports Timing, the source's trailer settings are RF **0.05 minutes (3 seconds)** and Cell1 **15 minutes** to the server.
3. Indoors, GPS-derived clocks can drift. Use the time controls at the bottom left to set each clock from the computer.
4. Open Window → BMS, show the last seven days of history, and examine the full interval for cell-voltage trends and imbalance.

## Alert configuration

The source uses Data Alerts Get/Set controls for boat settings and separate server recipient settings. It calls for BMS fault alerts, low SOC at **40%**, and no-network-communications at **1800 seconds**. RF, Cell1, LAN, and PC are enabled in the described configuration; SBD depends on mission traffic requirements.

Lab members must supply and maintain their own approved alert recipients in restricted configuration. This documentation does not configure or send alerts.
