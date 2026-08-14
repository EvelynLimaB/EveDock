# EveDock

Modular DC power dock / UPS architecture for home networking, a laptop, and smart-home loads.

> Open-source hardware project focused on a protected 12 V distribution bus, a regulated 19 V laptop rail, removable backup sources, automatic source selection, and optional telemetry.

**Status:** Prototype V0  
**Hardware revision:** 0.1  
**Electrical revision:** 0.1  
**Firmware:** N/A

## What it does

EveDock is intended to keep selected low-voltage loads operating from a primary DC source and a removable backup source during an outage. The design is modular, repairable, documented, and intended to evolve from a bench prototype into a custom PCB and 3D-printed enclosure.

## Current architecture

```text
PRIMARY DC SOURCE
     |
     +--> input protection / fuse
     |
     v
+-------------------+
| PRIMARY POWER     |
| PATH              |
+---------+---------+
          |
          |              BACKUP SOURCE
          |                  |
          |           Basike USB-C output
          |                  |
          |                  v
          |            USB-C PD SINK
          |                  |
          |            input protection
          |                  |
          +---------> BACKUP POWER PATH
                           |
                           v
                    +-------------+
                    | POWER MUX / |
                    | SOURCE ORING|
                    +------+------+
                           |
                           v
                        12 V BUS
                     /     |      \
                   ONU   Router    Echo
                           |
                        12 -> 19 V
                        regulated
                           |
                          ASUS

                    [telemetry, future]
                         INA226
                           |
                          ESP32
                           |
                        ESPHome
                           |
                     Home Assistant
```

This is an architectural target, not a validated schematic.

## Critical source constraint

The removable Basike powerbank is a **backup-source candidate**, not a 60 W power source. Its published USB-C output is approximately 12 V / 1.67 A class, or about 20 W at 12 V. Sustained output, pass-through behavior, cutoff behavior, and source-transition behavior are not yet validated by EveDock.

The 60 W figure remains a future architecture target only. Final continuous and peak bus ratings will be derived from measured load and transient data.

## Supported loads

| Load | Nominal rail | Status |
|---|---:|---|
| ONU | 12 V | Pending measurement |
| Router | 12 V | Pending measurement |
| Echo Dot 4 | TBD | Pending measurement |
| ASUS M1502IA-EJ211 | 19 V | 7.95 W measured baseline |

## Evidence policy

Every electrical value in this repository is classified as:

- **CONFIRMED** — directly measured or explicitly provided by a reliable primary source.
- **CONFIRMED + RESEARCH** — confirmed by the project owner and cross-checked against documentation.
- **ESTIMATED** — engineering estimate; not suitable as a final design limit.
- **PENDING** — required measurement or verification has not been completed.

Never convert a device's power-supply rating into its actual continuous consumption without measurement.

## Engineering gates

The project will not declare a final bus rating until the measured power budget and source behavior have been characterized. In particular, the following remain open:

- 12 V load measurements for ONU and router.
- 19 V converter efficiency, startup, peak-load, and thermal characterization.
- Basike USB-C profile, sustained output, pass-through, cutoff, and recovery behavior.
- Primary-to-backup switchover behavior under representative load.
- Numerical fuse, connector, wire, and thermal limits.

See `docs/architecture/requirements.md`, `docs/architecture/power-budget.md`, and `docs/testing/acceptance-criteria.md`.

## Safety

This project handles DC power and potentially high fault currents from battery sources. Use appropriate fusing, wire gauge, connectors, insulation, current limits, reverse-polarity protection, and thermal management. Do not bypass protection during normal operation. The prototype must be validated before unattended use.

The repository does not yet constitute a certified power supply, UPS, or safety-certified product.

## Quick build status

V0 is a bench prototype. No custom PCB is required yet. The immediate objective is to validate the 12 V distribution, measure every load, validate the 19 V conversion path, characterize the removable backup source, and test source switchover before integration into a permanent enclosure.

## Repository structure

```text
EveDock/
├── electronics/
│   ├── power-path/
│   ├── protection/
│   ├── 12v-bus/
│   ├── 12v-to-19v/
│   └── telemetry/
├── mechanical/
│   ├── enclosure/
│   ├── battery-dock/
│   └── cable-management/
├── firmware/
│   ├── esp32/
│   └── home-assistant/
├── docs/
│   ├── architecture/
│   ├── electrical/
│   ├── testing/
│   ├── safety/
│   ├── legal/
│   └── build-log/
├── bom/
├── cad/
├── pcb/
├── tests/
├── LICENSE
├── CONTRIBUTING.md
├── CODE_OF_CONDUCT.md
└── CHANGELOG.md
```

## Roadmap

- **V0:** 12 V bench proof of concept
- **V0.1:** 19 V laptop rail
- **V0.2:** removable Basike characterization/integration
- **V0.3:** autonomy characterization
- **V1:** validated automatic power path
- **V1.1:** per-output protection
- **V1.2:** INA226/INA219 telemetry + ESP32
- **V2:** ESPHome/Home Assistant integration
- **V2.1:** custom PCB
- **V3:** ABS/ASA enclosure and battery dock
- **V4:** larger battery / LiFePO4-compatible architecture

## Cost tracking

**Confirmed new purchases for the project:** R$ 0.00

Existing equipment is not counted as new project spending. Hypothetical components remain unpurchased until selected and acquired. See `bom/bom-brasil.csv` for procurement state.

## License

- Hardware: CERN Open Hardware Licence Version 2 - Strongly Reciprocal (CERN-OHL-S-2.0)
- Firmware/software: Apache License 2.0
- Documentation: CC BY-SA 4.0

See `LICENSE` and `docs/legal/` for scope and canonical license sources.
