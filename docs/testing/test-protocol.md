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

Record steady-state 12 V bus voltage/current/power and individual load measurements where practical.

**Status:** TBD

## TEST-003 — Combined load

Loads: ASUS + ONU + router.

Record total input power, 12 V bus voltage, 19 V rail voltage, converter temperature, and source current.

**Status:** TBD

## TEST-004 — Backup switchover

Procedure:

1. Run the supported network loads from the primary source.
2. Confirm stable voltage and operation.
3. Remove the primary source under controlled conditions.
4. Record transition behavior with an oscilloscope or suitable high-speed instrumentation where available.
5. Verify ONU reboot: yes/no.
6. Verify router reboot: yes/no.
7. Verify laptop reset: yes/no.
8. Restore primary source and repeat.

**Status:** TBD

A switchover test is required before the system is described as a UPS.

## TEST-005 — Powerbank compatibility

Record:

- Powerbank model
- Negotiated input profile
- Input voltage/current
- Pass-through behavior
- Whether the powerbank disconnects when load changes
- Runtime until cutoff
- Reconnection behavior

**Status:** TBD

## TEST-006 — Thermal test

Run the intended worst-case continuous load for a defined interval. Record temperatures of converters, protection devices, connectors, wiring, and enclosure surfaces.

**Status:** TBD
