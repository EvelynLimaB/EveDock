# EveDock Power Budget

## Purpose

This document separates measured load, engineering estimates, source capability, and future design targets. It is the authoritative starting point for sizing the power path.

## Current load inventory

| Load | Rail | Idle / baseline | Typical | Peak | Evidence | Status |
|---|---|---:|---:|---:|---|---|
| ASUS M1502IA-EJ211 | 19 V | 7.95 W measured | TBD | TBD | TEST-001 | Measured baseline only |
| ONU | 12 V | TBD | 4–6 W estimated | TBD | User-provided supply label + estimate | Needs measurement |
| Router | 12 V | TBD | 3–4 W estimated | TBD | User-provided supply label + estimate | Needs measurement |
| Echo Dot 4 | TBD | TBD | 1.5–3 W estimated | TBD | Engineering estimate | Needs measurement |

## Important distinction

A device power-supply rating is a source capability, not the device's continuous consumption. Final source and protection sizing must use measured load data plus defined transient margin.

## Source capability

### Primary source

- Model: TBD
- Nominal output: TBD
- Continuous power capability: TBD
- Protection: TBD
- Status: PENDING

### Basike backup source

- Model: Basike BA-POW079 / 20,000 mAh class
- Nominal stored energy: approximately 74 Wh per manufacturer specification
- USB-C output capability: up to 12 V / 1.67 A class per manufacturer specification
- Practical output class: approximately 20 W at 12 V
- Status: SPECIFICATION-BASED; sustained system behavior and pass-through behavior remain to be tested

The Basike must not be treated as a 60 W source. It is a removable low-power backup candidate.

## Design targets

The previous generic 60 W bus target is retained only as a future architecture target, not as a current rating.

The project will use these separate quantities:

- **Continuous bus target:** TBD after measured load budget.
- **Peak bus target:** TBD after transient measurements.
- **Primary source capability:** TBD after load characterization.
- **Backup source capability:** source-specific; Basike is currently a ~20 W class candidate.

## Calculation rules

For a downstream converter with efficiency η:

`P_input = P_output / η`

Example only: 7.95 W at the laptop load and 90% converter efficiency would require approximately 8.83 W at the 12 V side of the converter. This is a calculation example, not a measured EveDock efficiency value.

The total bus budget must include:

1. measured steady-state loads;
2. converter losses;
3. startup/transient demand;
4. wiring and connector losses;
5. protection-device losses;
6. thermal margin;
7. source-specific limitations.

## Acceptance gate

No bus power rating will be declared final until TEST-002, TEST-003, TEST-004, and TEST-005 provide measured evidence sufficient to determine steady-state load, peak demand, switchover behavior, and backup-source capability.
