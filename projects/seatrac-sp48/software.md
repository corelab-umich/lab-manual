---
title: "Software and configuration"
nav_order: 2
permalink: /seatrac-sp48/software/
parent: "SeaTrac SP-48"
---
# Software and configuration

## Reviewed source

[seatrac-asv-controller](https://github.com/corelab-umich/seatrac-asv-controller) provides ROS 2 Humble nodes, Docker configurations, Python/Julia controllers, sensor message decoding, and UDP command encoding. This documentation reviews [commit `20fd8cc669c3`](https://github.com/corelab-umich/seatrac-asv-controller/tree/20fd8cc669c3cc4dfc5e0b90afe88c7c5c191522); it does not establish a tested hardware baseline.

| Package | Role |
| --- | --- |
| `asv_sensors` | UDP reception, sensor drivers, measurement aggregation, and command transmission |
| `asv_messages` | SeaTrac packet encoding/decoding |
| `messages` | Custom ROS message definitions |
| `asv_controller` | Python/Julia control, estimation, and map publishers |
| `asv_model` | State/model publishers |
| `asv_utils` | Networking, byte conversion, and checksum utilities |

## Obtain and build

On a host with Docker Engine and Compose available:

```bash
git clone --recurse-submodules https://github.com/corelab-umich/seatrac-asv-controller.git
cd seatrac-asv-controller
git checkout 20fd8cc669c3cc4dfc5e0b90afe88c7c5c191522
git submodule update --init --recursive
docker compose -f docker-compose.sensor-drivers.yml build
```

The Dockerfile installs ROS dependencies and Julia 1.11.1, then runs `deps/install.jl` in `/root/.julia/environments/pyjuliapkg`. A host-mounted `.julia` directory hides the image's Julia depot; the upstream README describes installing packages into that mounted environment for first use. The copied installer is `/root/julia_install/install.jl`. Confirm the container's project/depot before running it.

These commands are documented from source; a container build has not been tested here because Docker Engine access is unavailable.

## Local configuration

The repository `.env` contains example listener/boat addresses, UDP port, and logging level. Configure these for the actual host and vessel using the lab's restricted connection record. `IP_ADDRESS` is the **receiver bind address**, while `BOAT_IP` is the command destination. A loopback bind address will not receive packets addressed to an external host interface.

`UDP_PORT` is used for both reception and command transmission in the Compose configuration. Although `.env` defines `PUB_PORT`, the current command-publisher service does not use it. Verify the vessel's required port assignments instead of assuming that variable controls the transmit port.

## Receive telemetry without starting controllers

```bash
docker compose -f docker-compose.sensor-drivers.yml up --build   packet_publisher imu_sensor_driver power_level_sensor_driver   attitude_sensor_driver gps_sensor_driver wind_sensor_driver   measurement_packet_publisher rosbag_recorder
```

This Compose file does not include the command publisher. Check receipt of current packets and parsed sensor messages before using the aggregated measurement packet.

| Topic | Producer / purpose |
| --- | --- |
| `/raw_sensor_packets` | UDP receiver: raw SeaTrac packets |
| `/imu` | IMU driver: ROS IMU data |
| `/gps`, `/nav_sat_fix` | GPS driver: custom navigation data and ROS fix |
| `/wind` | Wind driver |
| `/power_level` | Battery/power driver |
| `/attitude` | Heading/attitude driver |
| `/measurement_packet` | Aggregated measurements, published at 1 Hz |
| `/asv_command` | Controller heading and requested speed in knots |
| `/q_map`, `/target_q_map`, `/w_hat` | Controller visualization images |

## Controller assumptions to review

The measurement publisher uses a fixed geographic origin near Jordan Lake, converts knots to m/s, and converts SOC percent into energy using a **6500 Wh code assumption**. Its `stateofcharge` field therefore represents Wh rather than a fraction. Review the origin, battery capacity, wind model, controller domain, and selected control strategy for each experiment.

The main Compose file starts both `asv_ergo_control` and `transect_control`, plus `command_publisher`; its parameter estimator is commented out. Select one intended controller and confirm its required estimator inputs before a hardware run.

**The test Compose file also includes `command_publisher`. Running the whole test stack is not guaranteed to isolate the physical vessel.** Select the required mock/receiver services explicitly and omit command transmission for an offline test.

## Command behavior

`control_command_publisher` subscribes to `/asv_command` and sends true-heading/RPM UDP messages to the configured boat. Speed is interpolated using the repository's knots-to-RPM table, which clamps at 0 and 1300 RPM for requests outside 0–5 knots.

**`allow_command=false` still transmits the manual heading and manual speed values. It is not an emergency stop or a transmission-disable switch.** The reviewed publisher has no stale-command timeout. A verified vessel-specific stop procedure remains required; see [Operation]({{ '/seatrac-sp48/operation/' | relative_url }}).

## Persisted data

The Compose files mount `.rosbags` for ROS bags, `.jld2` for controller records, `.images` for map images, and `.julia` for Julia packages. Preserve the code commit, configuration, timestamps, and units alongside every dataset.
