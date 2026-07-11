# Numerical Accuracy Targets

## Scope

These are default acceptance limits for declared operating envelopes. A family specification may require a tighter limit. A looser limit requires an accepted ADR with evidence and a visible user-facing accuracy classification.

## Global numeric policy

- Use IEEE-754 binary64 for solver state unless an accepted engine adapter documents otherwise.
- Store all physical quantities internally in SI base units.
- Use absolute and relative tolerances together: `pass = |actual - expected| <= atol + rtol * |expected|`.
- Never compare only rounded display values.
- Record solver method, tolerances, minimum/maximum timestep, iteration limits, initial conditions, and reference temperature.
- Numerical warnings are part of the result contract and cannot be hidden by the UI.

## Default targets

| Capability | Default acceptance |
|---|---|
| F1 scalar analytical result | `rtol <= 1e-6`; fixture-specific `atol` |
| Kirchhoff current residual | `<= 1e-9 A + 1e-6 * largest incident current` |
| Kirchhoff voltage residual | `<= 1e-9 V + 1e-6 * largest loop voltage` |
| Energy/power balance | Relative residual `<= 1e-5` for ideal closed systems |
| F2 digital truth/state | Exact logical state |
| Digital event time | Exact integer tick; default tick is 1 ps |
| F3 DC model | Within 1% of declared reference inside validation envelope |
| F3 transient amplitude/feature | Within 2% of declared reference |
| F3 AC magnitude | Within 2% and no more than 0.2 dB unless family is stricter |
| F3 AC phase | Within 2 degrees |
| F4 steady-state temperature | Within 5% or 2 degrees C, whichever is larger |
| F4 dynamic thermal time constant | Within 5% |
| Monte Carlo deterministic replay | Bit-identical sample parameters and pass/fail counts for same engine/version/seed |
| Cross-engine logical outcomes | Exact pass/fail and state sequence |

## Convergence contract

A nonlinear run may return only one of these terminal states:

- `completed`: all requested points met acceptance checks.
- `completed_with_warnings`: results are usable but include declared accuracy or interpolation warnings.
- `non_converged`: iteration or continuation strategy failed at a stated point.
- `timestep_underflow`: the required step fell below the configured minimum.
- `numerical_failure`: NaN, infinity, overflow, singular factorization after recovery, or internal invariant failure.
- `cancelled`, `timed_out`, or `resource_exhausted`.

The engine must report the failing simulated time/frequency/parameter point, last accepted state, attempted recovery strategies, and actionable diagnostics.

## Required nonlinear recovery order

1. Reuse the last accepted solution as the initial guess.
2. Apply bounded Newton damping/line search.
3. Reduce timestep or sweep increment.
4. Apply source stepping.
5. Apply conductance stepping.
6. Stop at configured limits and return a structured failure; never silently fabricate a point.

## Waveform comparison

- Align reference and candidate on physical time, not array index.
- Preserve discontinuities and event boundaries before resampling.
- Compare scalar features (rise time, settling, overshoot, frequency, duty cycle, RMS) and a normalized waveform error.
- Decimation used for display must not affect validation data.

## Accuracy profiles shown to users

| Profile | Allowed models | Intended use |
|---|---|---|
| Fast | F0-F2 and reduced F3 | Editing, education, large digital designs |
| Balanced | F1-F3 | Default electronics work |
| Accurate | Validated F3 plus applicable F4 | Engineering analysis |
| Research | F3-F5 with explicit engine configuration | Reproducible experiments; no blanket accuracy claim |

The profile name is not evidence by itself. Each result must list the actual model and engine versions used.

