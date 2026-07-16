# Source and Evidence Policy

Status: **Normative documentation and release policy 1.0**
Applies to: requirements, ADRs, architecture contracts, model/library records, task readiness, validation, security, licensing, implementation claims, and releases

## 1. Purpose

This policy separates **where an idea entered the project** from **evidence that a technical claim is true**. A citation can preserve planning history without validating an equation, standard, model, implementation, or result.

The 44-page document *Web-based Electronics and Computer Simulation Platform* is retained as the project's original source brief. Every citation written as `[Source PDF, p. N]`, `[Source PDF, pp. N-M]`, or `[Source basis: PDF, ...]` is a **legacy origin and scope-traceability marker only**. The PDF has not been established as an authoritative, independently verified technical source. Its statements MUST be treated as unverified until corroborated under this policy.

Repository adoption can make a product requirement or ADR normative for this project. It does not make the source brief's technical assertions scientifically, legally, operationally, or experimentally correct.

## 2. Evidence classes

| Class | Examples | Permitted use | Prohibited use by itself |
|---|---|---|---|
| `source_brief_unverified` | The Source PDF and page citations | Planning history, problem framing, candidate scope, discovery leads | Technical substantiation, task readiness, validation, or release approval |
| `repository_decision` | Accepted ADR, approved requirement, release scope | Normative product intent and architecture constraints | Proof of external facts, numerical correctness, license rights, security, or physical accuracy |
| `official_primary_source` | Official standard/specification, manufacturer-controlled datasheet or model, authoritative upstream documentation/source, original research record | Establishing the declared contract or reference basis after version and applicability review | Automatic proof that this implementation conforms or that a model is accurate |
| `independent_reference` | Analytical solution, independently implemented reference, reviewed benchmark dataset, reference simulator with pinned version | Differential, numerical, or conformance comparison inside a declared envelope | Physical-correlation claims unless the reference contains applicable physical measurements |
| `physical_evidence` | Calibrated measurement with specimen, fixture, procedure, environment, raw data, uncertainty, and immutable lineage | Experimental correlation and bounded real-world accuracy claims | Claims outside the measured population, conditions, or uncertainty envelope |
| `current_project_evidence` | Current source artifact, schema validation, test log, benchmark, security assessment, license review, release record | Implementation-state, conformance, and release decisions | Broader claims than the recorded test and environment support |

A secondary or educational source MAY help discovery and explanation. It MUST NOT be the sole basis for a technical task becoming `Ready` or an artifact becoming `Released` when an applicable official/primary source or physical reference exists.

## 3. Claim-to-evidence requirements

| Claim | Minimum acceptable basis before `Ready` | Minimum evidence before `Released` |
|---|---|---|
| Equation, constant, material property, or physical mechanism | Versioned official/primary technical source, exact extraction location, dimensions, assumptions, and applicability | Implemented equation/model tests, limiting cases, uncertainty/validity record, and required independent or physical comparison |
| Standard, protocol, file format, symbol convention, or accessibility claim | Applicable official specification or standards publication with edition/version and access status | Conformance fixtures or review evidence against the pinned edition |
| Manufacturer/device/package behavior | Manufacturer-controlled datasheet, package drawing, model, or measurement record with ordering-code applicability and redistribution status | Exact revision binding, extracted-parameter review, and category-required validation |
| Software, browser, engine, API, or deployment behavior | Official upstream documentation/source for the pinned version | Current implementation and integration/test evidence in the supported environment |
| License, copyright, patent, or redistribution permission | Authoritative license text, rightsholder terms, SPDX mapping where applicable, and recorded review owner | Completed distribution/legal review and retained notices/decisions; the Source PDF is never license evidence |
| Security, authentication, isolation, or privacy property | Official protocol/security specifications, threat model, and versioned platform contracts | Current negative/abuse tests, configuration review, and required security sign-off |
| Numerical accuracy or simulator equivalence | Declared analytical or independent reference, metric, tolerance rationale, operating envelope, and uncertainty approach | Reproducible comparison results with exact revisions, settings, seeds, raw outputs, and limitations |
| Physical realism or real-world accuracy | Planned physical benchmark with specimen, equipment, calibration, environment, method, and uncertainty | Accepted physical evidence under the benchmark contract; simulator-to-simulator agreement alone is insufficient |
| Implementation, performance, browser, accessibility, or release status | Exact planned artifact/test/benchmark and acceptance criterion | Current project evidence from the declared revision and environment |
| Catalog count or market coverage | Machine-enumerated registry scope and explicit inclusion rule | Validated enumeration and release states; no extrapolation from the source brief or market size |

If the preferred official source is paywalled or inaccessible, the task MUST record that limitation and remain blocked unless an authorized reviewer approves a legally accessible, technically equivalent primary basis. An agent MUST NOT invent, paraphrase from memory, or infer inaccessible standard text.

## 4. Citation and provenance rules

1. Legacy `[Source PDF]` citations MAY remain so planning lineage is not lost, but they MUST be interpreted only through this policy.
2. A new technical assertion MUST cite the exact official/primary source or evidence record that supports it; adding a Source PDF page is optional origin metadata and never substitutes for that citation.
3. Each technical source record MUST include source type, title/owner, edition or version, publication or revision date when available, exact section/page/table/parameter location, stable locator, retrieval date for mutable web material, content digest when retained, license/redistribution status, applicability, and reviewer state.
4. Repository decisions and engineering approximations MUST be labeled as such. They MUST state assumptions, limitations, and the validation needed before release.
5. Conflicting sources MUST remain visible. The selected interpretation requires an owner, rationale, affected scope, and review record; evidence MUST NOT be silently discarded.
6. A generated citation, plausible URL, model name, database record, or unsupported quotation is not evidence until its identity and content are verified.
7. Source artifacts, extracted facts, model-calibration data, and holdout validation data MUST have separate immutable identities. Calibration evidence MUST NOT be presented as independent validation.

## 5. Task readiness rule

For every applicable technical claim, a task cannot become `Ready` until its card names:

- the exact official/primary source or approved physical/reference artifact;
- the source version and exact location used;
- the facts, equations, parameters, or constraints to be extracted;
- applicability, assumptions, units/dimensions, license/redistribution status, and known conflicts;
- the acceptance evidence that will be produced; and
- the reviewer or review class required by the task contract.

A task that cites only the Source PDF for an equation, standard, accuracy target, dependency behavior, license, security property, implementation fact, or release criterion MUST remain `Planned` or `Blocked`; it cannot be promoted to `Ready`. A documentation-governance task with no external technical claim MAY mark this rule `not_applicable`, but it MUST give a concrete rationale.

Discovery tasks MAY be created specifically to locate and review missing primary sources. They produce a source inventory and decision record, not implementation or release permission.

## 6. Validation and release rule

An item cannot become `Validated` or `Released` until:

1. every applicable technical claim resolves to an approved official/primary source or physical evidence record;
2. current implementation/test evidence demonstrates the claim against that reference;
3. exact model, dependency, engine, project, fixture, and evidence revisions are retained;
4. validity, uncertainty, limitations, contradictory results, unsupported conditions, and license restrictions are visible;
5. calibration and holdout/independent validation data remain separated;
6. the relevant reviewer signs off under the task and release contract; and
7. no pass decision depends solely on the Source PDF, a repository assertion, visual plausibility, or a previously claimed status.

Absence of primary or physical evidence does not make a model false. It makes the affected technical claim **unverified** and release-blocking at any gate that requires that claim.

## 7. Migration of existing citations

Existing Source PDF citations do not need to be deleted or renumbered. They remain useful for historical traceability, but all readers, agents, task generators, reviewers, and release automation MUST classify them as `source_brief_unverified`.

During normal work on an affected requirement or task:

1. preserve the legacy page marker;
2. add exact official/primary technical sources or physical evidence records;
3. record unresolved source gaps and conflicts;
4. keep the task below `Ready`, or the artifact below `Validated`/`Released`, until the applicable evidence is accepted; and
5. update requirement, model, test, traceability, and release records together.

This is a progressive evidence migration, not permission to bulk-assert that legacy citations have been technically confirmed.
