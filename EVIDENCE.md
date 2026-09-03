# ZeroRun v0.4 technical evidence

## Qualification status

**Internal technical qualification: PASS.**

Qualified runtime candidate:

```text
0b3f1e7f3a3feb1b7e41f32704a3b558a3455e58
```

The formal v0.4 gate required both supported historical workloads to achieve:

- at least **5× same-runner compute efficiency**;
- at least **50% p95 reduction**;
- zero observed stale-success/shadow-mismatch/cache-conflict events in accepted evidence;
- the frozen historical patch corpora and strict gate math unchanged.

## Final results

| Workload | Historical merged patches | Direct total | ZeroRun total | Same-runner efficiency | p95 reduction |
| --- | ---: | ---: | ---: | ---: | ---: |
| pytest | 10 | 528.286 s | 64.696 s | **8.165714×** | **78.415%** |
| SymPy | 20 | 3,788.204 s | 694.509 s | **5.454509×** | **78.309%** |

Observed in the accepted evidence:

- stale-success events: **0**;
- shadow mismatches: **0**;
- cache conflicts: **0**;
- accepted direct failures: **0**;
- accepted ZeroRun request failures: **0**.

## pytest receipt

The final pytest qualification used 10 distinct historical merged pytest patches on the exact qualified candidate and passed the strict 5× / 50% gate.

Headline result:

- compute efficiency: **8.165714×**;
- p95 reduction: **78.415%**;
- direct total: **528,286.082 ms**;
- ZeroRun total: **64,695.641 ms**;
- safety/correctness observations: **0** stale successes, shadow mismatches, and cache conflicts.

## SymPy receipt

The final SymPy evidence is provenance-locked to the same qualified runtime candidate and the same 20-patch corpus.

Eighteen case rows come from the completed full 20-case qualification execution. Two exact-source-pair cases, PRs **20250** and **20590**, use separately qualified reviewed-equivalence evidence after the broad file-level harness conservatively invalidated all four partitions. Those two reviewed decisions were bound to immutable pre-merge/merge source pairs, required the expected hit/miss pattern, and shadow-executed every claimed hit. The final aggregation replaced only those two rows, retained the other 18 unchanged rows, verified provenance, and then ran the original aggregate and strict performance gate unchanged.

Headline result:

- compute efficiency: **5.454509×**;
- p95 reduction: **78.309%**;
- direct total: **3,788,203.578 ms**;
- ZeroRun total: **694,508.656 ms**;
- post-edit hits: **60**;
- shadow mismatches: **0**;
- cache conflicts: **0**;
- direct failures: **0**;
- ZeroRun failures: **0**.

This provenance detail matters: the final receipt does not claim that an unchanged broad SymPy closure magically achieved the result, and it does not hide the two reviewed exact-source-pair promotions.

## Interpretation

This evidence supports the following narrow statement:

> ZeroRun v0.4 passed its internal historical technical qualification on the accepted pytest and SymPy workloads, exceeding the 5× same-runner compute-efficiency and 50% p95-reduction gates with zero observed stale-success, shadow-mismatch, or cache-conflict events in the accepted evidence.

It does **not** establish:

- universal speedup;
- correctness for arbitrary commands or repositories;
- automatic proof of source-closure completeness;
- external production reliability;
- customer demand, retention, or willingness to pay;
- a guaranteed reduction in a customer's total CI bill.

## Evidence publication boundary

The public repository contains this sanitized summary rather than the private runtime source, benchmark harnesses, raw workflow artifacts, or internal experimental history. Raw receipts and implementation details are retained in the private implementation repository.

## Next evidence

The next gate is external usage, not another synthetic internal benchmark target:

- 2–5 real developers or teams;
- at least 100 genuine external edit → test requests;
- normal caches and normal failures preserved;
- reuse/miss/bypass and verification outcomes recorded;
- p50/p95 and compute/time savings measured;
- installation/support burden recorded;
- customer willingness-to-pay evaluated separately from technical correctness.
