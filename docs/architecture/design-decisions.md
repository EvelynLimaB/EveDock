# Design Decision Log

## DEC-001 — Use a 12 V internal bus

**Status:** Accepted for V0 architecture.

Reasons:

- ONU and router are expected to use 12 V.
- A common DC bus reduces unnecessary conversion stages.
- 12 V is practical for modular low-voltage distribution.
- It leaves a simple path to a dedicated 19 V laptop converter.

The final bus voltage tolerance and protection limits remain to be validated.

## DEC-002 — Keep the battery removable

**Status:** Accepted.

The prototype uses an existing Basike 20,000 mAh / 22.5 W powerbank as the initial battery source. A removable interface avoids a permanently enclosed battery and permits later source upgrades.

## DEC-003 — Separate source selection from load conversion

**Status:** Accepted.

The source/power-path layer should establish the protected internal bus first. Device-specific conversion, such as 12 V to 19 V, should happen downstream. This makes load modules replaceable and keeps the core bus architecture stable.

## DEC-004 — Treat 60 W as a design target, not a rating

**Status:** Preliminary.

The currently documented laptop measurement is 7.95 W and other loads have not yet been measured. A 60 W class target provides room for future loads, but it must not be treated as a safe continuous rating until the actual protection and thermal design is validated.

## DEC-005 — Telemetry is a later layer

**Status:** Accepted.

Power measurement and ESP32 integration are valuable, but they should not block validation of the fundamental power path. Telemetry begins after the V0 electrical path is stable.

## DEC-006 — CAD source files are authoritative

**Status:** Accepted.

STEP/parametric CAD is the source of truth for mechanical design. STL files are generated print artifacts and should not become the only representation of a part.
