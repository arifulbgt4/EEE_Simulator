# EPIC-HDL-001 - RTL FPGA and Verilator integration

## Outcome

Deliver the complete **RTL FPGA and Verilator integration** capability for release R9, including normative behavior, failure handling, validation, documentation, security, accessibility, performance, compatibility, and operations where applicable.

## Requirements and release

- Requirements: REQ-026
- Release: R9
- Entry: Gate G8 educational CPU.

## Atomic tasks

| Task | Single outcome | Depends on | Status |
|---|---|---|---|
| [PLAT-HDL-001](../platform/plat-hdl-001-define-supported-verilog-and-systemverilog-subset.md) | Define supported Verilog and SystemVerilog subset | Gate G8 educational CPU | Planned |
| [PLAT-HDL-002](../platform/plat-hdl-002-implement-hdl-editor-and-source-package-contract.md) | Implement HDL editor and source package contract | PLAT-HDL-001 | Planned |
| [PLAT-HDL-003](../platform/plat-hdl-003-implement-syntax-lint-worker.md) | Implement syntax lint worker | PLAT-HDL-002 | Planned |
| [PLAT-HDL-004](../platform/plat-hdl-004-implement-no-network-compiler-sandbox.md) | Implement no-network compiler sandbox | PLAT-HDL-003 | Planned |
| [PLAT-HDL-005](../platform/plat-hdl-005-implement-verilator-compilation-adapter.md) | Implement Verilator compilation adapter | PLAT-HDL-004 | Planned |
| [PLAT-HDL-006](../platform/plat-hdl-006-implement-generated-model-and-compiler-cache.md) | Implement generated model and compiler cache | PLAT-HDL-005 | Planned |
| [PLAT-HDL-007](../platform/plat-hdl-007-implement-simulation-wrapper-and-clock-control.md) | Implement simulation wrapper and clock control | PLAT-HDL-006 | Planned |
| [PLAT-HDL-008](../platform/plat-hdl-008-implement-testbench-lifecycle.md) | Implement testbench lifecycle | PLAT-HDL-007 | Planned |
| [PLAT-HDL-009](../platform/plat-hdl-009-implement-vcd-and-fst-waveform-capture.md) | Implement VCD and FST waveform capture | PLAT-HDL-008 | Planned |
| [PLAT-HDL-010](../platform/plat-hdl-010-implement-hierarchy-browser.md) | Implement hierarchy browser | PLAT-HDL-009 | Planned |
| [PLAT-HDL-011](../platform/plat-hdl-011-implement-reusable-ip-metadata-and-versioning.md) | Implement reusable IP metadata and versioning | PLAT-HDL-010 | Planned |
| [PLAT-HDL-012](../platform/plat-hdl-012-implement-fpga-lut-bram-dsp-and-pll-abstractions.md) | Implement FPGA LUT BRAM DSP and PLL abstractions | PLAT-HDL-011 | Planned |
| [PLAT-HDL-013](../platform/plat-hdl-013-implement-rtl-versus-event-model-differential-tests.md) | Implement RTL versus event-model differential tests | PLAT-HDL-012 | Planned |
| [PLAT-HDL-014](../platform/plat-hdl-014-validate-malicious-and-resource-heavy-hdl-limits.md) | Validate malicious and resource-heavy HDL limits | PLAT-HDL-013 | Planned |

## Exit criteria

- [ ] Every listed task is Done with linked evidence.
- [ ] Requirement, component/interface, test, and release traceability has no gap.
- [ ] Nominal and failure behavior are documented and validated.
- [ ] Security, performance, accessibility, compatibility, migration, and operational gates pass where applicable.
- [ ] Known limitations and deferred work are explicit.
