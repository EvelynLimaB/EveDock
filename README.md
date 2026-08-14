# EveDock

Modular DC power dock / UPS for home networking, a laptop, and smart-home loads.

> Open-source hardware project focused on a removable powerbank, a 12 V DC bus, a regulated 19 V laptop rail, automatic source selection, protection, and optional telemetry.

**Status:** Prototype V0  
**Hardware revision:** 0.1  
**Electrical revision:** 0.1  
**Firmware:** N/A

## What it does

EveDock is intended to keep selected low-voltage loads operating from a primary DC supply and a removable battery/powerbank during an outage. The design is modular, repairable, documented, and designed to evolve from a bench prototype into a custom PCB and 3D-printed enclosure.

## Current architecture

```text
                 PRIMARY DC PSU
                      |
                      v
                 +----------+
                 | POWER    |
  REMOVABLE ---->| PATH /   |----> 12 V BUS ----> ONU
  POWERBANK      | SOURCE   |----> 12 V BUS ----> Router
                 | SELECT   |----> Echo rail
                 +----------+
                      |
                      +----> 12 V -> 19 V ----> ASUS M1502IA-EJ211

                         [future]
                              |
                         INA226/INA219
                              |
                            ESP32
                              |
                         Home Assistant
```

This is an architectural target, not a claim that the power-path circuit is already validated.

## Supported loads

| Load | Nominal rail | Status |
|---|---:|---|
| ONU | 12 V | Pending measurement |
| Router | 12 V | Pending measurement |
| Echo Dot 4 | TBD | Pending measurement |
| ASUS M1502IA-EJ211 | 19 V | 7.95 W measured in documented test |

## Evidence policy

Every electrical value in this repository is tagged as one of:

- **CONFIRMED** — directly measured or explicitly provided by a reliable primary source.
- **CONFIRMED + RESEARCH** — confirmed by the project owner and cross-checked against documentation.
- **ESTIMATED** — engineering estimate; not suitable as a final design limit.
- **PENDING** — required measurement or verification has not been completed.

Never convert a device's power-supply rating into its actual continuous consumption without measurement.

## Safety

This project handles DC power and potentially high fault currents from battery sources. Use appropriate fusing, wire gauge, connectors, insulation, current limits, and thermal management. Do not bypass protection during normal operation. The prototype must be validated before unattended use.

The repository does not yet constitute a certified power supply, UPS, or safety-certified product.

## Quick build status

V0 is a bench prototype. No custom PCB is required yet. The immediate goal is to validate the 12 V distribution, measure every load, validate the 19 V conversion path, and test source switchover before integrating telemetry or a permanent enclosure.

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
- **V0.2:** removable Basike powerbank integration
- **V0.3:** autonomy characterization
- **V1:** automatic power mux
- **V1.1:** per-output protection
- **V1.2:** INA226/INA219 telemetry + ESP32
- **V2:** ESPHome/Home Assistant integration
- **V2.1:** custom PCB
- **V3:** ABS/ASA enclosure and battery dock
- **V4:** larger battery / LiFePO4-compatible architecture

## Cost tracking

**Confirmed purchases for the project:** R$ 0.00

The prototype currently uses equipment already owned. Hypothetical components are not counted as purchases until acquired. See `bom/bom-brasil.csv` for the tracked procurement state.

## License

- Hardware: CERN Open Hardware Licence Version 2 - Strongly Reciprocal (CERN-OHL-S-2.0)
- Firmware/software: Apache License 2.0
- Documentation: CC BY-SA 4.0
