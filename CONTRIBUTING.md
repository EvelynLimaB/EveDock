# Contributing to EveDock

EveDock is an open-source hardware project. Contributions should preserve traceability between requirements, measurements, design decisions, and released artifacts.

## Before changing electrical design

- Check the architecture and design-decision log.
- Distinguish measured values from estimates.
- Record assumptions and safety implications.
- Do not silently replace a component with a part having different electrical limits.

## Measurements

New measurements should include date, conditions, method/instrument, units, and hardware revision. Update the relevant truth table and test record.

## CAD

Commit editable/source CAD where practical. Exported STL files should be treated as build artifacts and associated with a revision.

## Commits

Prefer focused commits using messages such as:

- `feat: add 12V distribution prototype`
- `test: measure router idle power`
- `docs: document power-path decision`
- `fix: correct battery carrier clearance`

## Safety

Do not submit a design as validated merely because it works on a bench. High-current battery paths, fusing, thermal limits, connector ratings, insulation, and fault behavior must be explicitly considered.
