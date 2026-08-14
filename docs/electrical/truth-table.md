# Hardware Truth Table

Values are intentionally separated into measured, specified, estimated, and pending data.

| Item | Model | Source | Consumption measured | Consumption estimated | Confidence | Notes |
|---|---|---|---:|---:|---|---|
| ASUS | M1502IA-EJ211 | User measurement / Linux | 7.95 W | — | High | Headless Linux test; see TEST-001 |
| ONU | Leste | User-provided label | TBD | 4–6 W | Medium | 12 V / 1 A supply rating is not consumption |
| Router | Leste | User-provided label | TBD | 3–4 W | Medium | 12 V / 0.5 A supply rating is not consumption |
| Echo | Echo Dot 4 | Device identification | TBD | 1.5–3 W | Medium | Measure at intended power interface |
| Powerbank | Basike 20,000 mAh / 22.5 W | Device specification | TBD | — | High | Battery/source characterization pending |

## Measurement record: ASUS

- Device: ASUS M1502IA-EJ211
- Measured power: 7.95 W
- Condition: Linux headless, battery discharge
- Date: 2026-08-14
- Method: `upower`
- Battery design energy: 42.067 Wh
- Reported full energy: 35.621 Wh
- SOC: 99%

These values describe the observed test condition and must not be generalized into a worst-case power requirement.

## Rules

- A manufacturer adapter rating is a source capability, not a measured load.
- Estimated values remain estimates until measured.
- Every new measurement should include date, operating condition, method, instrument, and units.
- If a value changes, preserve the previous result in the test log rather than silently overwriting history.
