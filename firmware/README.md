# Firmware

Firmware is not required for V0.

Planned stack:

```text
ESP32 -> ESPHome -> Home Assistant
```

Telemetry should remain optional: loss of the MCU, Wi-Fi, MQTT, or Home Assistant must not interrupt the fundamental power path.
