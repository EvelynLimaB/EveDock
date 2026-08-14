# Mechanical Print Specification

## Source-of-truth policy

STEP or parametric CAD is authoritative. STL is generated for printing.

## Required metadata for every released print

- Revision
- Part name
- CAD source
- Printer
- Material
- Nozzle diameter
- Layer height
- Walls/perimeters
- Infill
- Supports
- Print orientation
- Estimated print time
- Printed mass
- Fit notes

## Planned structure

```text
mechanical/
├── enclosure/
│   ├── v0/
│   ├── v1/
│   └── README.md
├── battery-dock/
│   ├── v0/
│   └── README.md
└── cable-management/
```

## Material strategy

ABS/ASA is a planned enclosure material because the project may expose the enclosure to converter heat. Material selection must still be validated against actual measured temperatures, printer capability, dimensional stability, and the intended installation environment.

## V0

No released geometry yet. The first mechanical prototype should prioritize fit, serviceability, cable routing, connector access, ventilation, and safe separation of power components over appearance.
