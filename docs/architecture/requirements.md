# EveDock Requirements and Verification Matrix

| ID | Requirement | Verification | Evidence | Status |
|---|---|---|---|---|
| REQ-PWR-001 | The protected internal distribution bus shall have a documented nominal voltage and operating limits. | TEST-002/003 + design review | Measurements + schematic | OPEN |
| REQ-PWR-002 | Device supply ratings shall not be used as substitutes for measured continuous load. | Documentation review | Truth table + test records | PARTIAL |
| REQ-PWR-003 | Each external power input shall have an explicit protection strategy. | Design inspection | Schematic/BOM | OPEN |
| REQ-PWR-004 | Each output branch shall have a defined protection/current-limit strategy before deployment. | Design inspection + fault testing | Schematic/test report | OPEN |
| REQ-PWR-005 | The 19 V laptop rail shall remain within its defined voltage tolerance over the intended operating load. | TEST-003 + converter characterization | Voltage/current/thermal data | OPEN |
| REQ-PWR-006 | The primary and backup sources shall not create an unsafe backfeed path. | Schematic review + fault test | Power-path design + test | OPEN |
| REQ-PWR-007 | Backup switchover shall be characterized under representative network load. | TEST-004 | Oscilloscope/high-speed capture + reboot observations | OPEN |
| REQ-PWR-008 | Basike compatibility shall be established experimentally rather than assumed. | TEST-005 | PD profile, current, pass-through, cutoff and recovery data | OPEN |
| REQ-PWR-009 | The selected backup source shall be documented with its actual source limits separately from bus design targets. | Documentation review | Power budget | OPEN |
| REQ-PWR-010 | Telemetry failure shall not interrupt the fundamental power path. | Fault injection / design review | Schematic + test record | OPEN |
| REQ-MEC-001 | Mechanical revisions shall identify source CAD, revision and print parameters. | Release review | CAD metadata | PARTIAL |
| REQ-THERM-001 | Converter and protection-component temperatures shall remain within component limits under the defined continuous load. | TEST-006 | Thermal measurements | OPEN |
| REQ-DOC-001 | Every published electrical number shall have an evidence class. | Documentation review | Truth table | PARTIAL |
| REQ-DOC-002 | Hardware, firmware and documentation licensing shall be present in the repository. | Repository inspection | License files | OPEN |

## Status meanings

- **OPEN:** requirement is defined but not yet verified.
- **PARTIAL:** supporting documentation exists, but verification or repository completeness is incomplete.
- **PASS:** requirement has sufficient evidence for the current hardware revision.
- **BLOCKED:** verification depends on an unresolved design or hardware dependency.

No requirement marked OPEN or BLOCKED should be represented as a validated product capability.
