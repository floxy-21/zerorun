# Supported launch boundary

ZeroRun's current claim is intentionally narrow.

## Reuse identity

A prior pass is eligible for reuse only when all required identity inputs match:

- explicit operator-reviewed source closure and content identity
- immutable OCI runtime image digest
- exact command and target configuration
- execution policy
- declared environment values
- Linux/amd64 platform identity

## Execution boundary

- Linux/amd64 only
- read-only checkout
- no network during task execution
- deterministic result-only launch targets
- captured streams suppressed and no output artifacts published
- unsupported, missing, changed, or uncertain identity executes fresh
- conflicting fresh verification evidence is quarantined

## Nonclaims

ZeroRun does not automatically infer or prove source-closure completeness. It is
not arbitrary-command memoization, broad build caching, or a guarantee that every
repository will achieve the measured internal results.
