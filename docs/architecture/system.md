# System Architecture

## Design intent

EveDock distributes low-voltage DC power from a primary source or removable backup source. The protected internal architecture targets a 12 V distribution bus and a regulated 19 V rail for the ASUS M1502IA-EJ211.

## Block diagram

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
          |                  BACKUP SOURCE
          |                      |
          |               Basike USB-C output
          |                      |
          |                      v
          |                USB-C PD SINK
          |                      |
          |                input protection
          |                      |
          +----------> BACKUP POWER PATH
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

                         [future telemetry]
                              |
                            INA226
                              |
                             ESP32
                              |
                           ESPHome
                              |
                        Home Assistant
```

This is an architectural target. It is not a validated schematic.

## Electrical invariants

1. No unverified battery/source combination is connected directly to a load.
2. A source must not be connected directly to another source without an intentional power-path/ORing stage.
3. Each externally accessible input and output needs an explicit protection strategy before deployment.
4. The 19 V rail must be regulated and independently validated under load.
5. Source switchover must be tested with representative loads before the system is described as UPS-capable.
6. Measured consumption, source capability, and future design targets are tracked separately.
7. Telemetry must not be a single point of failure for power delivery.

## Design targets

| Parameter | Target | Evidence |
|---|---:|---|
| Internal distribution bus | 12 V nominal | Architecture decision |
| Laptop rail | 19 V regulated | Required by target device |
| Continuous bus capacity | TBD | Power-budget gate |
| Peak bus capacity | TBD | Transient characterization |
| Primary source capability | TBD | Source characterization |
| Basike backup source | ~20 W class | Manufacturer output specification; EveDock test pending |
| Telemetry | V/I/P/SOC where available | Future |
| Battery | Removable | User-owned Basike backup candidate |

The previous 60 W figure is retained only as a future architecture target. It is not a current validated rating for the EveDock bus or the Basike backup source.
