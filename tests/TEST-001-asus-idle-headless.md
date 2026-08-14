# TEST-001 — ASUS idle headless

**Status:** PASS (measurement captured; power-path integration not tested)

## Setup

- Device: ASUS M1502IA-EJ211
- OS: Linux
- Display: off
- Network: active
- Services: project/home-server services as configured during measurement
- Battery SOC: 99%
- Date: 2026-08-14
- Method: `upower`

## Result

- Measured power: **7.95 W**
- Battery design energy: 42.067 Wh
- Reported full energy: 35.621 Wh

## Interpretation

This is a baseline operating-point measurement. It is not a maximum-power test and must not be used alone to size the 19 V converter or the complete EveDock source.

## Follow-up

- [ ] Measure with display on.
- [ ] Measure under CPU/network load.
- [ ] Measure input power through the planned 19 V converter.
- [ ] Record converter efficiency.
- [ ] Repeat using the EveDock 19 V rail.
