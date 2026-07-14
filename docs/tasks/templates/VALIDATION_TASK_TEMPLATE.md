# `<VAL-ID>` - Validate `<target>`

## Metadata

| Field | Value |
|---|---|
| Status | Planned |
| Target | `<family, engine, interface, or workflow>` |
| Requirement | `<REQ-ID>` |
| Golden fixture | `<GRC-ID>` |
| Fidelity/analysis | `<F# and analysis>` |
| Depends on | `<task IDs>` |

## Exact prerequisites

- `PLAT-QA-001`, predecessor gate, and exact target task IDs.

## Public contracts

- Exact result, diagnostic, provenance, model, and package contracts.

## Allowed files

- Exact validation documentation and evidence paths; implementation files are forbidden.

## Reference

State the independent analytical, reference-engine, manufacturer, standards, or published dataset. Record version, settings, operating envelope, and license.

## Test vectors

List nominal, boundary, invalid, temperature, tolerance, failure, and regression vectors.

## Acceptance calculation

State exact expected values/features and `atol`/`rtol` or exact digital/event rules.

## Acceptance test ID

- `TEST-GRC-<NNN>`

## Documentation updates

- Exact fixture, registry, coverage, traceability, and release records.

## Evidence

- Machine-readable results.
- Human-readable comparison and diagnostics.
- Environment, engine/model versions, seed, and timestamp.

## Definition of Done

- [ ] Reference is independent and reproducible.
- [ ] Nominal and edge vectors pass.
- [ ] Failure results are structured and actionable.
- [ ] Coverage, task, and release evidence links are updated.

