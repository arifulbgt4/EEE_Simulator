# EPIC-IMP-001 - Model data and firmware interchange

## Outcome

Deliver the complete **Model data and firmware interchange** capability for release R7, including normative behavior, failure handling, validation, documentation, security, accessibility, performance, compatibility, and operations where applicable.

## Requirements and release

- Requirements: REQ-024, REQ-032, REQ-042, REQ-049, REQ-056, REQ-063
- Release: R7
- Entry: Gate G6 Electronics MVP.

## Atomic tasks

| Task | Single outcome | Depends on | Status |
|---|---|---|---|
| [PLAT-IMP-001](../platform/plat-imp-001-implement-spice-model-and-subcircuit-import-policy.md) | Implement SPICE model and subcircuit import policy | Gate G6 Electronics MVP | Planned |
| [PLAT-IMP-002](../platform/plat-imp-002-implement-spice-library-include-resolution.md) | Implement SPICE library include resolution | PLAT-IMP-001 | Planned |
| [PLAT-IMP-003](../platform/plat-imp-003-implement-verilog-and-systemverilog-source-packaging.md) | Implement Verilog and SystemVerilog source packaging | PLAT-IMP-002 | Planned |
| [PLAT-IMP-004](../platform/plat-imp-004-implement-verilog-a-and-ams-supported-subset-policy.md) | Implement Verilog-A and AMS supported-subset policy | PLAT-IMP-003 | Planned |
| [PLAT-IMP-005](../platform/plat-imp-005-implement-ibis-import-contract.md) | Implement IBIS import contract | PLAT-IMP-004 | Planned |
| [PLAT-IMP-006](../platform/plat-imp-006-implement-touchstone-import-contract.md) | Implement Touchstone import contract | PLAT-IMP-005 | Planned |
| [PLAT-IMP-007](../platform/plat-imp-007-implement-csv-and-pwl-stimulus-import.md) | Implement CSV and PWL stimulus import | PLAT-IMP-006 | Planned |
| [PLAT-IMP-008](../platform/plat-imp-008-implement-vcd-and-fst-waveform-import.md) | Implement VCD and FST waveform import | PLAT-IMP-007 | Planned |
| [PLAT-IMP-009](../platform/plat-imp-009-implement-hex-elf-and-binary-firmware-import.md) | Implement HEX ELF and binary firmware import | PLAT-IMP-008 | Planned |
| [PLAT-IMP-010](../platform/plat-imp-010-implement-export-and-round-trip-rules.md) | Implement export and round-trip rules | PLAT-IMP-009 | Planned |
| [PLAT-IMP-011](../platform/plat-imp-011-implement-model-provenance-and-license-records.md) | Implement model provenance and license records | PLAT-IMP-010 | Planned |
| [PLAT-IMP-012](../platform/plat-imp-012-implement-unsupported-syntax-and-security-diagnostics.md) | Implement unsupported syntax and security diagnostics | PLAT-IMP-011 | Planned |

## Exit criteria

- [ ] Every listed task is Done with linked evidence.
- [ ] Requirement, component/interface, test, and release traceability has no gap.
- [ ] Nominal and failure behavior are documented and validated.
- [ ] Security, performance, accessibility, compatibility, migration, and operational gates pass where applicable.
- [ ] Known limitations and deferred work are explicit.
- [ ] Every import records source/hash/license/redistribution/trust/validation/executable mode/dependencies/sandbox and remains quarantined until policy permits use/publication.
- [ ] Vendor ordering codes use bounded generic-device inheritance and exact package/pin bindings instead of copied whole models.
