# Security Policy

## Supported versions

The project is currently documentation-only and has no released runtime. Security support begins with the first tagged implementation release. Until then, report vulnerabilities in documentation, proposed protocols, model handling, or supply-chain decisions using the private process below.

After releases begin, this table will be updated for each supported release line:

| Version | Supported |
|---|---|
| Unreleased documentation foundation | Design review only |

## Reporting a vulnerability

Do not open a public issue or discussion for a suspected vulnerability.

Send a private report through the repository owner's published security contact or the hosting provider's private security-advisory feature. Include:

- affected document, component, endpoint, format, engine, or release;
- a clear description and realistic impact;
- reproduction steps or a minimal malicious input, if safe to share;
- required privileges and deployment assumptions;
- suggested mitigations, if known;
- whether public disclosure is already planned.

Do not include live credentials, personal data, or third-party secrets. Do not test against systems or data you do not own or have explicit permission to assess.

Maintainers should acknowledge a complete report within 5 business days, provide a triage decision within 10 business days, and coordinate remediation and disclosure timing with the reporter. These are response targets, not guarantees.

## Security boundaries

The planned platform treats all user-authored projects, imported SPICE models, HDL, firmware, datasets, archives, and external-engine inputs as untrusted. The security architecture must enforce:

- no outbound network access for untrusted simulation jobs by default;
- container or equivalent process isolation for external engines;
- read-only runtime filesystems plus isolated, bounded scratch space;
- CPU, memory, wall-time, output-size, and job-count limits;
- archive path traversal, decompression-bomb, parser-depth, and schema validation defenses;
- explicit authorization for private projects, versions, comments, and shared results;
- secret isolation from browser bundles, project archives, logs, and worker inputs;
- cancellation and cleanup that terminate child processes and discard temporary data;
- provenance and signature or checksum support for trusted model sources;
- audit events for privileged operations without recording sensitive model content.

Large results, malformed circuits, non-convergent models, and unbounded waveform retention are recognized resource-exhaustion risks in the source study. [Source PDF, pp. 12, 25-26, 36, 39-40]

Detailed controls are specified in [Security, Privacy, and Sandboxing](docs/architecture/SECURITY_PRIVACY_AND_SANDBOXING.md), [Local, Cloud, and Worker Architecture](docs/architecture/LOCAL_CLOUD_AND_WORKER_ARCHITECTURE.md), and [ADR-0008](docs/decisions/ADR-0008.md).

## Safe harbor

Good-faith research that follows this policy, avoids privacy violations and service disruption, and gives maintainers reasonable time to remediate will be treated as authorized project security research to the extent the maintainers can grant that authorization.
