# `<CMP-ID>` - `<family/variant, fidelity, concern>`

## Metadata

| Field | Value |
|---|---|
| Status | Planned |
| Family | `<stable-family-id>` |
| Variant | `<stable-variant-id or shared>` |
| Fidelity | F0-F5 |
| Concern | CAT, SYM, MODEL, THERMAL, FAILURE, IMPORT, VALIDATION, or DOCS |
| Release | `<R#>` |
| Depends on | `<task IDs>` |

## Exact prerequisites

- Exact task and gate IDs only.

## Public contracts

- Exact named entities and contract documents.

## Single outcome

Describe one component/model variant, one fidelity tier, and one concern. Do not combine independent model, symbol, import, validation, or documentation work.

## Normative inputs

- Family specification and registry row.
- Pin/domain and parameter contracts.
- Equations, reference model/data, operating envelope, and license/provenance.
- Linked golden fixture and numerical tolerance.

## Equations and reference data

- Exact equations, event rules, reference IDs/data, limits, and provenance.

## Allowed files

- Exact documentation paths; exact source/test paths are mandatory before `Ready`.

## Deliverables

- Exact model/symbol/metadata/test/documentation artifact owned by this concern.

## Documentation updates

- Exact registry, coverage, traceability, test, risk, and release records.

## Edge and failure cases

- Invalid or extreme parameters.
- Unsupported analyses or fidelity requests.
- Temperature, parasitic, breakdown, saturation, state, or timing behavior where applicable.
- Structured diagnostic requirements.

## Acceptance test IDs

- `TEST-<TASK-ID>-NOMINAL`
- `TEST-<TASK-ID>-BOUNDARY`
- `TEST-<TASK-ID>-FAILURE`

## Acceptance

- [ ] Registry and family specification agree.
- [ ] Applicable golden/reference assertions pass.
- [ ] Unsupported behavior is explicit, not silently approximated.
- [ ] Provenance, license, limitations, and accuracy envelope are visible.
- [ ] Coverage and traceability state advances only to the evidence-supported state.

