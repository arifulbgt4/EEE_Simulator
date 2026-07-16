# Contributing

Thank you for helping build an open, rigorous electronics and computer simulation platform.

All contributions follow Applied Physics First: preserve the traceable path from governing principle and dimensions through equations, algorithms, model dependencies, immutable library revisions, and validation evidence. A feature claim is incomplete when its physical validity, uncertainty, provenance, or limitation is unknown.

## Before contributing

Read, in order:

1. [docs/START_HERE.md](docs/START_HERE.md)
2. [docs/SOURCE_AND_EVIDENCE_POLICY.md](docs/SOURCE_AND_EVIDENCE_POLICY.md)
3. [AGENTS.md](AGENTS.md)
4. [docs/PRODUCT_REQUIREMENTS.md](docs/PRODUCT_REQUIREMENTS.md)
5. The relevant [accepted ADRs](docs/decisions)
6. The selected task, its dependencies, and its release gate

The project deliberately moves from realistic electronics to digital logic, educational CPUs, small computers, and finally architecture-level systems. This ordering is a repository decision whose planning origin is traced to the unverified source brief; the PDF is not feasibility evidence and must not be used to claim that any stage works. The adopted gates must not be bypassed by a contribution. [Source PDF, pp. 32-44]

## Choose an atomic task

Choose one `Ready` entry from [docs/tasks/TASK_INDEX.md](docs/tasks/TASK_INDEX.md). A component task is limited to one component or variant, one fidelity tier, and one concern. A platform task is limited to the subsystem and concern named in its card.

Do not begin work when:

- a dependency is not complete;
- the task has no acceptance criteria;
- the proposed change conflicts with an accepted ADR;
- required model provenance or licensing is unknown;
- the same task is already assigned.

Resolve documentation ambiguity before implementation. A changed architectural decision requires a new ADR that supersedes the old one; do not rewrite history.

## Contribution expectations

- Keep changes focused and reviewable.
- Preserve stable public IDs and file-format compatibility.
- Add tests for expected behavior, limits, and failure modes.
- Keep requirements, task status, catalog coverage, validation evidence, and traceability synchronized.
- Record numerical tolerances and the reference used to establish them.
- Use the applicable official/primary technical source or physical evidence for equations, standards, accuracy, licensing, security, implementation, and release claims; a Source PDF citation alone is never sufficient.
- Declare imported model provenance, version, license, supported analyses, and known limitations.
- Use immutable revision IDs and content hashes for published model, device, package, binding, board, system, project, and evidence references.
- Keep database content declarative; executable kernels require an allowlisted capability and the documented sandbox boundary.
- Resolve library definitions through the Library Service contract rather than adding engine-to-storage dependencies.
- Treat generated or vendor-supplied models as untrusted input.
- Use English for repository documentation, source identifiers, and public interfaces.

The source brief records proposals for validated models, reference-circuit comparisons, convergence diagnostics, selective probing, streaming results, and deterministic cross-engine synchronization. These are adopted planning inputs, not confirmed technical facts. Contributions in those areas must establish the safeguards with official/primary references and current project evidence. [Source PDF, pp. 29-31, 39-40]

## Documentation changes

Documentation-only contributions should:

- use relative links;
- preserve source-derived page citations as unverified origin metadata and follow the [Source and Evidence Policy](docs/SOURCE_AND_EVIDENCE_POLICY.md);
- distinguish normative requirements from explanation;
- avoid claiming every manufacturer SKU is built in;
- keep the 162-family and 502-variant baseline internally consistent;
- report only actually enumerated model records; do not convert market aspirations into registry counts;
- update the traceability matrix when requirements, tasks, tests, or gates change.

## Review checklist

A reviewer should be able to answer yes to all applicable questions:

- Is the task `Ready`, scoped, and dependency-complete?
- Does the change satisfy the named requirement and no unrelated requirement?
- Are public contracts and compatibility effects documented?
- Are normal, boundary, invalid-input, resource-limit, and cancellation paths covered?
- Are deterministic seeds and engine versions recorded where relevant?
- Are accuracy claims backed by a declared reference?
- Is every technical reference authoritative for the claim, with Source PDF citations treated only as unverified planning lineage?
- Are security and license boundaries preserved?
- Are docs, task status, coverage, tests, and traceability consistent?

## Reporting security issues

Do not open a public issue for a suspected vulnerability. Follow [SECURITY.md](SECURITY.md).

## Community standards

Participation is governed by [CODE_OF_CONDUCT.md](CODE_OF_CONDUCT.md). By contributing, you agree that your contribution is provided under the repository's [Apache-2.0 license](LICENSE) unless a clearly identified file states otherwise.
