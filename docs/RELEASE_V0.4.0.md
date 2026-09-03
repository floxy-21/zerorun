# ZeroRun v0.4.0

ZeroRun v0.4.0 is the first release to close the project's internal 5× / 50% technical qualification target on both accepted historical workloads while preserving the narrow fail-closed launch boundary.

## Internal qualification

| Workload | Corpus | Same-runner compute efficiency | p95 reduction | Observed stale success / shadow mismatch / cache conflict |
| --- | ---: | ---: | ---: | ---: |
| pytest | 10 historical merged patches | **8.165714×** | **78.415%** | **0 / 0 / 0** |
| SymPy | 20 historical merged patches | **5.454509×** | **78.309%** | **0 / 0 / 0** |

Qualified runtime implementation:

```text
0b3f1e7f3a3feb1b7e41f32704a3b558a3455e58
```

The detailed sanitized methodology, including the final SymPy provenance disclosure, is in [../EVIDENCE.md](../EVIDENCE.md).

## Supported boundary

v0.4.0 remains deliberately narrow:

- Linux/amd64;
- immutable OCI runtime image pinned by digest;
- explicit operator-reviewed source closure;
- deterministic result-only test targets;
- read-only checkout;
- no network during task execution;
- declared environment and exact command/policy included in identity;
- changed, unknown, unsupported, or conflicting evidence fails closed.

ZeroRun does not automatically prove source-closure completeness.

## Private pilot distribution

Approved design partners receive a compiled Linux/amd64 evaluation package rather than source-repository access. The validated package includes:

```text
zerorun-linux-amd64
install.sh
zerorun.example.json
QUICKSTART.md
AGENTS.md
LICENSE.txt
THIRD_PARTY_NOTICES.txt
PYTHON-LICENSE.txt
BUILD_INFO.txt
SHA256SUMS.txt
```

The package is checksum-protected and smoke-tested for installation, CLI version/help, absence of Python source/bytecode, and privacy-preserving pilot metrics export.

See [PILOT.md](PILOT.md) for public onboarding guidance.

## Claim boundary

The release supports the statement that ZeroRun v0.4 passed its **internal historical technical qualification** on the accepted pytest and SymPy workloads.

It does not establish:

- universal 5× speedup;
- a guaranteed reduction in total customer CI spend;
- external production reliability;
- automatic source-closure proof;
- retention or willingness to pay;
- paid commercial validation.

## Next milestone

The next evidence target is external usage:

- 2–5 real developers or teams;
- at least 100 genuine chronological external edit → test requests;
- normal failures, misses, bypasses and broad edits preserved;
- reuse, verification, p50/p95, compute savings and setup/support burden measured;
- customer economics evaluated separately from correctness.
