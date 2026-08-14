# EveDock Acceptance Criteria

These criteria define when a subsystem can move from experimental to validated for the current hardware revision.

## Power distribution

PASS requires:

- nominal bus voltage is defined;
- voltage remains within the selected component/load limits during the defined continuous load;
- measured current is below source, wiring, connector, and protection limits;
- no abnormal heating is observed;
- no source backfeed occurs.

## 12 V loads

PASS requires ONU and router to operate continuously for the defined test interval without reboot, dropout, excessive voltage deviation, or thermal fault.

## 19 V laptop rail

PASS requires:

- regulated output within the defined laptop input tolerance;
- successful laptop operation at idle and representative load;
- startup behavior characterized;
- converter efficiency measured;
- converter temperature documented.

## Backup source

PASS requires the exact backup source model and negotiated USB-C profile to be recorded, plus:

- sustained output test;
- pass-through behavior test;
- low-battery/cutoff behavior;
- recovery/reconnect behavior;
- source transition test with representative load.

A source that passes energy-runtime testing but fails seamless source transition is not a validated UPS source.

## Switchover

PASS requires:

- primary-to-backup transition captured with suitable instrumentation;
- no unacceptable bus collapse or overshoot;
- ONU state unchanged;
- router state unchanged;
- laptop does not reset when the laptop rail is within its tested operating conditions.

## Thermal

PASS requires every power converter, protection component, connector, and relevant enclosure location to remain within the manufacturer's limits with documented margin during the defined continuous-load test.

## Telemetry

PASS requires voltage/current/power readings to be plausible and reproducible, while disconnecting the telemetry MCU or network must not interrupt power delivery.

## Release rule

A subsystem may be described as **validated for the tested configuration** only when the corresponding requirement rows are PASS and the test records identify the exact hardware revision and measurement conditions.
