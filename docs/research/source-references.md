# EveDock Research References

This file records external technical references used to shape the current architecture. External specifications are not treated as EveDock measurements.

## Basike BA-POW079

The manufacturer's published product information identifies a 20,000 mAh class powerbank with approximately 74 Wh nominal stored energy and USB-C output capability in the 12 V / 1.67 A class.

Use in EveDock:

- establish the backup source as approximately a 20 W class source at 12 V;
- do not treat the powerbank as a 60 W internal-bus source;
- require EveDock testing for sustained output and pass-through behavior.

Source: https://basikebrasil.com.br/products/ba-pow-079

## Texas Instruments TPS2121

TPS2121 is a candidate power-mux component for low-voltage source selection. Its datasheet/product information describes a 2.8 V to 22 V operating range and up to 4.5 A output capability under specified conditions.

Use in EveDock:

- candidate for the protected source-selection layer;
- not a substitute for a battery charger or USB-C PD sink;
- final selection remains dependent on current, thermal, transient and protection requirements.

Source: https://www.ti.com/product/TPS2121

## Texas Instruments TPS25730

TPS25730 is a USB Type-C and USB Power Delivery sink controller intended for USB-C/PD power-path applications.

Use in EveDock:

- establishes that USB-C PD negotiation should be treated as an explicit subsystem;
- candidate architecture reference for a future USB-C PD sink implementation;
- not a selected EveDock component yet.

Source: https://www.ti.com/product/TPS25730

## Texas Instruments INA226

INA226 is a high-side current/power monitor suitable for the low-voltage telemetry layer and supports bus-voltage/current/power measurement over I2C.

Use in EveDock:

- candidate for power telemetry;
- telemetry remains electrically independent from the fundamental power path.

Source: https://www.ti.com/product/INA226

## ESPHome INA226 support

ESPHome provides an INA226 sensor component for exposing voltage/current/power telemetry.

Use in EveDock:

- supports the planned ESP32 + ESPHome + Home Assistant telemetry stack.

Source: https://esphome.io/components/sensor/ina226/

## CERN OHL v2

CERN publishes three variants of the CERN Open Hardware Licence v2, including CERN-OHL-S-2.0 for strongly reciprocal hardware licensing.

Source: https://ohwr.org/licences/

## Apache License 2.0

Apache publishes the current Apache License 2.0 and guidance for applying it to software distributions.

Source: https://www.apache.org/licenses/LICENSE-2.0.html

## CC BY-SA 4.0

Creative Commons publishes the CC BY-SA 4.0 legal code and canonical URL.

Source: https://creativecommons.org/licenses/by-sa/4.0/legalcode

## Reference projects

`nithinmathewjoji/12v-ups-for-wifi-routers-` is a useful reference for simple 12 V UPS topology. Its published design uses a 12 V lead-acid battery, relay switching, and a 220 VAC transformer/rectifier arrangement. It is a reference project, not an EveDock design baseline.

Source: https://github.com/nithinmathewjoji/12v-ups-for-wifi-routers-
