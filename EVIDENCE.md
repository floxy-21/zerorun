# Technical evidence

## Accepted internal corpus

ZeroRun's technical MVP was evaluated on 30 distinct historical merged edits
across pytest and SymPy. The comparison used direct execution and the normal
ZeroRun path under a locked internal protocol, with shadow checks for claimed
reuse.

| Measure | Direct | ZeroRun | Reported result |
| --- | ---: | ---: | ---: |
| pytest p95 | 50.40s | 27.23s | 45.96% reduction |
| SymPy p95 | 134.26s | 89.26s | 33.52% reduction |
| pytest same-runner cumulative compute | — | — | 3.062x efficiency |

Observed in this corpus:

- stale-success events: 0
- shadow mismatches: 0
- cache conflicts: 0

## Interpretation

This evidence supports an internal technical acceptance claim for these workloads
inside the reviewed launch boundary. It does not establish universal speedup,
production reliability, source-closure completeness, external adoption, or
commercial demand.

## Open gates

- A 5x result has not been established.
- 100 real external requests have not been completed.
- Design-partner repeatability and reliability remain open.
- Paying customers, retention, willingness to pay, and commercial validation
  remain open.
- The raw receipt remains private pending evidence sanitization and publication
  review.
