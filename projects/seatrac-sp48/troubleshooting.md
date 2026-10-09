---
title: "Troubleshooting"
nav_order: 5
permalink: /seatrac-sp48/troubleshooting/
parent: "SeaTrac SP-48"
---
# Troubleshooting

These checks are drawn from the recovered notes and reviewed source. They are diagnostic starting points; no new vessel tests were performed.

| Symptom | Checks supported by the source |
| --- | --- |
| No raw UDP packets | Check the receiver bind address, host interface, UDP mapping, configured vessel destination, and firewall. A loopback bind cannot receive externally addressed packets. |
| Raw packets but missing ROS sensor topics | Confirm the expected packet type/sink and compare [interface lengths and units]({{ '/seatrac-sp48/interface/' | relative_url }}) with the decoder. |
| Wrong location or controller domain | Review the hard-coded origin and domain configuration; the source uses a Jordan Lake origin. |
| SOC has unexpected magnitude | The measurement-packet field uses Wh derived from a 6500 Wh assumption, rather than a normalized fraction. |
| Commands still sent with `allow_command=false` | This setting selects manual values; it does not stop transmission. Follow the lab's verified stop procedure. |
| Offline test reaches the boat | The test Compose file includes a live UDP command publisher. Omit that service and inspect the destination configuration. |
| Julia packages disappear after mounting `.julia` | The mount hides the image depot. Install packages in the mounted project/depot following upstream setup guidance. |
| GPS or ADCP serial connection fails | Verify COM port, power, and baud rate: the recovered initial rates are GPS 4800 and ADCP 9600, with both configured to 19200. |
| VMDas lacks GPS data | Check NMEA1 port assignments and the NAV settings; close BBTalk before acquisition. |
| Dashboard clocks disagree indoors | Battery Tips directs synchronizing each clock to the computer using the Dashboard time controls. |
| Battery cells diverge | Compare cell-voltage history; the source identifies a difference above 0.1 V as a concern. |
| No alerts while stored | With the main battery switch off there is no logging or alerting. Review [storage checks]({{ '/seatrac-sp48/battery/' | relative_url }}). |

For a resolved issue, retain the exact symptom, build/commit, diagnosis evidence, confirmed fix, author, and verification date. Keep untested hypotheses labeled as such.
