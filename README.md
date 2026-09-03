# ZeroRun

Fail-closed deterministic test-result reuse for AI coding agents and CI.

ZeroRun answers one narrow question after a code edit: can a previously passing deterministic test result be reused defensibly, or must the target execute fresh?

Reuse is eligible only inside a reviewed boundary. Changed, unknown, unsupported, or conflicting evidence fails closed and executes fresh or is quarantined.

## ZeroRun v0.4 status

**Internal technical qualification: PASS.**

ZeroRun v0.4 cleared the unchanged formal performance gates on historical merged edits across pytest and SymPy:

| Workload | Corpus | Same-runner compute efficiency | p95 reduction | Observed safety failures |
| --- | ---: | ---: | ---: | ---: |
| pytest | 10 merged patches | **8.1657×** | **78.415%** | **0** |
| SymPy | 20 merged patches | **5.4545×** | **78.309%** | **0** |

The formal gates were at least **5× same-runner compute efficiency**, at least **50% p95 reduction**, and zero observed stale-success/shadow-mismatch/cache-conflict events in the accepted evidence.

These are workload-specific **internal historical qualification results**, not universal speed guarantees or external production proof. Real-user reliability, setup friction, retention, willingness to pay, and commercial validation remain open.

See [EVIDENCE.md](EVIDENCE.md) for the claim boundary and provenance summary.

## Supported v0.4 boundary

- Linux/amd64
- immutable OCI runtime image pinned by digest
- explicit operator-reviewed source closure
- deterministic result-only targets
- read-only checkout
- no network during task execution
- declared environment included in reuse identity
- exact command/policy/runtime identity
- uncertainty executes fresh
- conflicting fresh verification quarantines a cached success

ZeroRun does **not** automatically prove that a declared source closure is complete. `closure_reviewed: true` remains an explicit review assertion.

See [docs/BOUNDARY.md](docs/BOUNDARY.md).

## Private pilot

The v0.4 runtime implementation is proprietary and distributed to approved design partners as a compiled Linux/amd64 pilot package. Pilot users do **not** need access to the private implementation repository and do not upload their source code to ZeroRun.

Typical lifecycle:

```text
agent edit
   ↓
zerorun run <task>
   ↓
MISS_EXECUTED or HIT_REUSED
   ↓
periodic zerorun run <task> --verify
```

A healthy initial cache lifecycle is:

```text
MISS_EXECUTED
HIT_REUSED
VERIFY_MATCH
```

Public installation/onboarding guidance: [docs/PILOT.md](docs/PILOT.md).

## Public vs private repositories

This repository, **`floxy-21/zerorun`**, is the public product surface. It contains:

- product explanation
- supported safety boundary
- sanitized evidence summary
- pilot onboarding guidance
- public roadmap
- security/contact guidance

The runtime implementation, benchmark harnesses, internal experiments, raw qualification receipts, and private pilot build system belong in a separate private implementation repository.

## Next milestone

The next meaningful proof is external usage:

1. onboard 2–5 real developers or teams;
2. collect at least 100 genuine external edit → test requests under the normal safety boundary;
3. record reuse, misses/bypasses, verification outcomes, p50/p95, compute savings, setup friction, and support burden;
4. preserve failures and broad/shared edits rather than selecting only favorable cases;
5. use those traces to evaluate customer economics and willingness to pay.

See [docs/ROADMAP.md](docs/ROADMAP.md).

## Links

- Website: https://zero-run.onrender.com/
- Technical evidence: https://zero-run.onrender.com/evidence
- Private pilot: https://zero-run.onrender.com/contact
- Security: [SECURITY.md](SECURITY.md)

Do not post credentials, access tokens, confidential source code, or sensitive repository details in a public issue.
