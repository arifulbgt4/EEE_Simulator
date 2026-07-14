# Test Catalog

Status: **Normative identifier and evidence plan 1.0**

The [machine-readable test registry](test-registry.yaml) assigns one stable acceptance test to every product requirement and one stable validation test to every golden reference fixture. Atomic task test IDs are derived deterministically by the [Atomic Task Contract](../tasks/ATOMIC_TASK_CONTRACT.md).

## Coverage invariants

- `TEST-REQ-001` through `TEST-REQ-038` map one-to-one to `REQ-001` through `REQ-038`.
- `TEST-GRC-001` through `TEST-GRC-054` map one-to-one to `GRC-001` through `GRC-054` and `VAL-GRC-001` through `VAL-GRC-054`.
- Every platform, component, package, and validation card names its stable acceptance IDs.
- A test record declares expected evidence, release gate, source task or fixture, and status.
- Registry presence means `Specified`; only linked current results may change a test to `Passing`.

## Evidence contract

Each execution record contains test ID, immutable project/fixture digest, candidate and independent-reference versions, model/package/engine versions, analysis configuration, operating envelope, browser or worker environment, seed, timestamp, raw result references, comparison calculation, diagnostics, and final disposition.

Exact digital truth/event tests have no numerical tolerance. Numerical tests use the limits in [Numerical Accuracy Targets](NUMERICAL_ACCURACY_TARGETS.md) or a stricter family-specific envelope. Visual/package tests retain deterministic render configuration, semantic assertions, accessibility output, and approved reference images without treating pixel similarity as electrical evidence.

## Change control

Test IDs are never reused. Changing expected behavior requires updating the requirement or fixture, affected cards, traceability, and release checklist in the same change. A retired test remains in the registry with replacement and rationale.
