# System Architecture

## Design intent

EveDock distributes low-voltage DC power from a primary source or removable powerbank. The internal architecture targets a 12 V distribution bus and a regulated 19 V rail for the ASUS M1502IA-EJ211.

## Block diagram

```text
             +-------------------+
             | Primary DC source |
             +---------+---------+
                       |
                       v
                 +-----------+
                 | Protection|
                 +-----+-----+
                       |
                       v
                 +-----------+       +------------------+
                 | Power-path|<------| Removable battery|
                 | / source  |       | / powerbank      |
                 | selection |       +------------------+
                 +-----+-----+
                       |
                       v
                    12 V BUS
              +--------+--------+----------------+
              |        |        |                |
             ONU    Router     Echo        12 -> 19 V
                                             converter
                                                 |
                                               ASUS

                         [future]
                              |
                         current/voltage
                           telemetry
                              |
                            ESP32
                              |
                           ESPHome
                              |
                       Home Assistant
```

## Electrical invariants

1. No unverified battery/source combination is connected directly to a load.
2. Each externally accessible output must have an appropriate protection strategy before the design is considered deployment-ready.
3. The 19 V rail must be regulated and independently validated under load.
4. Source switchover must be tested with real loads before it is described as UPS-capable.
5. Measured consumption and source ratings are tracked separately.

## Design targets

| Parameter | Target | Evidence |
|---|---:|---|
| Internal distribution bus | 12 V nominal | Architecture decision |
| Laptop rail | 19 V regulated | Required by target device |
| Nominal bus design capacity | 60 W class | Preliminary design target |
| Telemetry | V/I/P/SOC where available | Future |
| Battery | Removable | User-owned Basike powerbank |

The 60 W value is a design target, not a validated rating. Final limits depend on the selected protection, connectors, wiring, converter thermal performance, and source capabilities.
