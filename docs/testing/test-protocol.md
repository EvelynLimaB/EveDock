# Test Protocol

## General recording format

Every test should record:

- Test ID
- Date/time
- Hardware revision
- Source configuration
- Load configuration
- Voltage
- Current
- Power
- Instrument/method
- Ambient conditions when relevant
- Pass/fail result
- Notes and anomalies

## TEST-001 — ASUS idle headless

Baseline documented in `tests/TEST-001-asus-idle-headless.md`.

## TEST-002 — Internet-only load

Loads: ONU + router.

Record:

- individual device voltage/current/power where practical;
- 12 V bus voltage/current/power;
- startup current if measurable;
- steady-state current;
- test duration and ambient conditions.

**Status:** TBD

## TEST-003 — Combined load

Loads: ASUS + ONU + router, with Echo when integrated.

Record:

- total source input power;
- 12 V bus voltage/current/power;
- 19 V rail voltage/current/power;
- converter efficiency;
- converter and connector temperatures;
- startup and representative CPU/network load behavior.

A single 7.95 W idle ASUS measurement is not sufficient to size the converter.

**Status:** TBD

## TEST-004 — Backup switchover

Procedure:

1. Run the supported network loads from the primary source.
2. Confirm stable voltage and operation.
3. Confirm the backup source is in the intended negotiated/active state.
4. Remove the primary source under controlled conditions.
5. Capture 12 V bus behavior with suitable instrumentation.
6. Where possible, capture source-A and source-B states simultaneously.
7. Record transition time, minimum voltage, overshoot, undershoot, and load resets.
8. Verify ONU reboot: yes/no.
9. Verify router reboot: yes/no.
10. Verify laptop reset: yes/no when the laptop rail is included.
11. Restore the primary source and repeat.

**Status:** TBD

A switchover result is required before the system is described as UPS-capable.

## TEST-005 — Backup powerbank characterization

This is a gate for treating the Basike as an EveDock backup source.

Record:

- exact powerbank model;
- negotiated USB-C PD profile;
- output voltage/current;
- sustained output power over a defined interval;
- pass-through behavior while the powerbank is charging;
- whether the powerbank disconnects when load changes;
- cutoff voltage/behavior;
- recovery/reconnection behavior;
- runtime at representative loads;
- thermal behavior.

**Status:** TBD

A passing energy-runtime result without passing switchover/pass-through behavior does not establish UPS compatibility.

## TEST-006 — Thermal test

Run the intended worst-case continuous load for a defined interval. Record temperatures of converters, protection devices, connectors, wiring, and enclosure surfaces.

Compare measured temperatures with the selected component limits and document margin.

**Status:** TBD

## TEST-007 — Laptop peak characterization

Run representative CPU, storage, display, and network workloads. Record 19 V rail peak current/power, input power to the converter, converter efficiency, and transient behavior.

**Status:** TBD
