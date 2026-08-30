# ZeroRun

Fail-closed deterministic test reuse for AI coding agents and CI.

ZeroRun is designed for one narrow decision after a code edit: may a previously
passing deterministic test result be reused, or must the target execute fresh?
Reuse is eligible only when the reviewed source closure, pinned runtime, command,
policy, declared environment, and Linux/amd64 platform identity match. Changed,
unknown, unsupported, or conflicting evidence fails closed.

## Current evidence

The internal technical MVP passed on 30 historical merged edits across pytest and
SymPy:

- pytest p95 reduction: **45.96%** (50.40s direct to 27.23s ZeroRun)
- SymPy p95 reduction: **33.52%** (134.26s direct to 89.26s ZeroRun)
- pytest same-runner compute efficiency: **3.062x**
- observed stale-success events: **0**
- observed shadow mismatches: **0**
- observed cache conflicts: **0**

These are workload-specific internal results, not universal guarantees. The 5x
target, 100 real external requests, design-partner proof, paying customers, and
commercial validation remain open. See [EVIDENCE.md](EVIDENCE.md).

## Supported launch boundary

- Linux/amd64
- immutable OCI runtime image pinned by digest
- explicit operator-reviewed source closure
- deterministic result-only launch targets
- commands suppress captured streams and publish no output artifacts
- read-only checkout and no network during execution
- declared environment included in the reuse identity
- uncertainty executes fresh; conflicting verification is quarantined

ZeroRun does not infer or prove that a source closure is complete. The current
MVP requires an explicit reviewed closure. See [docs/BOUNDARY.md](docs/BOUNDARY.md).

## Try a real workload

ZeroRun is recruiting a small number of design partners with expensive,
deterministic Linux/amd64 test partitions and frequent agent-driven edits.

- [Read the technical evidence](https://zero-run.onrender.com/evidence)
- [Request a private pilot](https://zero-run.onrender.com/contact)
- [Open a workload-fit issue](https://github.com/floxy-21/zerorun/issues/new?template=workload-fit.yml)

Do not post credentials, access tokens, confidential source code, or sensitive
repository details in a public issue.

## Publication scope

This repository is the curated public product surface. It contains the product
boundary, measured claim scope, public roadmap, and feedback channel. The runtime
implementation, internal working history, experiments, and raw receipts remain
private pending source, secrets, license/IP, and evidence review.

Website: [zero-run.onrender.com](https://zero-run.onrender.com/)
