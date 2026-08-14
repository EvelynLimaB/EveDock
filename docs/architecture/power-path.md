# Power Path Architecture

## Design principle

EveDock separates source capability from the protected load bus. A source is not assumed to be able to provide the full bus design target merely because the bus is designed for future expansion.

## V0 conceptual architecture

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
```

This is an architectural diagram only. It is not a validated schematic.

## Basike constraint

The Basike is a removable backup candidate and must be treated as a source-specific limitation. Its USB-C interface is not the same thing as a raw 12 V battery terminal. The final implementation must establish the required USB-C/PD sink behavior and verify the negotiated profile.

The Basike is currently considered approximately a 20 W class 12 V source based on the manufacturer's published output capability. Sustained output, pass-through behavior, cutoff behavior, and recovery are not yet verified by EveDock.

## Power-mux role

A power mux or ideal-diode stage is responsible for selecting/ORing sources and preventing unsafe source-to-source backfeed. It is not itself a battery charger and does not replace USB-C PD negotiation.

A candidate such as TI TPS2121 may be evaluated for the protected low-voltage source-selection stage, subject to final current, voltage, thermal, and transient requirements.

## Electrical invariants

1. No source may be connected directly to another source without an intentional power-path element.
2. The backup path must not backfeed the primary input.
3. The primary path must not exceed the documented source or connector limits.
4. Every external source input needs a defined protection strategy.
5. The 19 V converter must be downstream of the protected 12 V bus.
6. Telemetry and control electronics must not be a single point of failure for power delivery.
7. The final source-selection circuit must be validated before use as a UPS.
