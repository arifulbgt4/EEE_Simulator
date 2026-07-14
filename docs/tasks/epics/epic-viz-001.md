# EPIC-VIZ-001 - Visualization and virtual instruments

## Outcome

Deliver the complete **Visualization and virtual instruments** capability for release R2, including normative behavior, failure handling, validation, documentation, security, accessibility, performance, compatibility, and operations where applicable.

## Requirements and release

- Requirements: REQ-007, REQ-021, REQ-034, REQ-037
- Release: R2
- Entry: Gate G1 editor foundation.

## Atomic tasks

| Task | Single outcome | Depends on | Status |
|---|---|---|---|
| [PLAT-VIZ-001](../platform/plat-viz-001-define-probe-and-measurement-contract.md) | Define probe and measurement contract | Gate G1 editor foundation | Planned |
| [PLAT-VIZ-002](../platform/plat-viz-002-implement-scalar-voltage-current-and-power-indicators.md) | Implement scalar voltage current and power indicators | PLAT-VIZ-001 | Planned |
| [PLAT-VIZ-003](../platform/plat-viz-003-implement-multichannel-waveform-viewer.md) | Implement multichannel waveform viewer | PLAT-VIZ-002 | Planned |
| [PLAT-VIZ-004](../platform/plat-viz-004-implement-cursors-measurements-and-annotations.md) | Implement cursors measurements and annotations | PLAT-VIZ-003 | Planned |
| [PLAT-VIZ-005](../platform/plat-viz-005-implement-oscilloscope-instrument-behavior.md) | Implement oscilloscope instrument behavior | PLAT-VIZ-004 | Planned |
| [PLAT-VIZ-006](../platform/plat-viz-006-implement-multimeter-instrument-behavior.md) | Implement multimeter instrument behavior | PLAT-VIZ-005 | Planned |
| [PLAT-VIZ-007](../platform/plat-viz-007-implement-function-and-pulse-generator-controls.md) | Implement function and pulse generator controls | PLAT-VIZ-006 | Planned |
| [PLAT-VIZ-008](../platform/plat-viz-008-implement-logic-analyzer-and-timing-diagram.md) | Implement logic analyzer and timing diagram | PLAT-VIZ-007 | Planned |
| [PLAT-VIZ-009](../platform/plat-viz-009-implement-spectrum-fft-and-bode-views.md) | Implement spectrum FFT and Bode views | PLAT-VIZ-008 | Planned |
| [PLAT-VIZ-010](../platform/plat-viz-010-implement-heat-map-visualization.md) | Implement heat-map visualization | PLAT-VIZ-009 | Planned |
| [PLAT-VIZ-011](../platform/plat-viz-011-implement-educational-current-direction-animation.md) | Implement educational current-direction animation | PLAT-VIZ-010 | Planned |
| [PLAT-VIZ-012](../platform/plat-viz-012-implement-realistic-physical-component-appearance-renderer.md) | Implement realistic physical component appearance renderer | PLAT-VIZ-011 | Planned |
| [PLAT-VIZ-013](../platform/plat-viz-013-implement-ic-package-body-pins-orientation-mark-and-label-renderer.md) | Implement IC package body pins orientation mark and label renderer | PLAT-VIZ-012 | Planned |
| [PLAT-VIZ-014](../platform/plat-viz-014-implement-component-limit-and-failure-overlays.md) | Implement component limit and failure overlays | PLAT-VIZ-013 | Planned |
| [PLAT-VIZ-015](../platform/plat-viz-015-implement-accessible-waveform-summaries.md) | Implement accessible waveform summaries | PLAT-VIZ-014 | Planned |
| [PLAT-VIZ-016](../platform/plat-viz-016-validate-instrument-input-loading-models.md) | Validate instrument input-loading models | PLAT-VIZ-015 | Planned |

## Exit criteria

- [ ] Every listed task is Done with linked evidence.
- [ ] Requirement, component/interface, test, and release traceability has no gap.
- [ ] Nominal and failure behavior are documented and validated.
- [ ] Security, performance, accessibility, compatibility, migration, and operational gates pass where applicable.
- [ ] Known limitations and deferred work are explicit.
