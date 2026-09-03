# ZeroRun v0.4 private pilot

ZeroRun v0.4 is currently distributed to approved design partners as a compiled Linux/amd64 evaluation package. The runtime source is not required for participation.

**The binary is intentionally not published in this public repository.** Approved participants receive `zerorun-pilot-linux-amd64.tar.gz` and `zerorun-pilot-linux-amd64.tar.gz.sha256` through a private channel after the workload boundary is reviewed.

## Workload fit

A good first pilot target is:

- deterministic;
- repeatedly executed after code edits;
- expensive enough that avoiding unchanged work matters;
- runnable on Linux/amd64;
- runnable without network access during the test;
- compatible with a pinned OCI dependency image;
- narrow enough that its result-producing source closure can be reviewed.

Do not start with an arbitrary full CI pipeline.

## Package contents

Approved participants receive a checksum-protected archive containing:

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

The customer package does not contain the private Python source tree.

## Installation

The pilot package is delivered with an outer checksum. Verify it first:

```bash
sha256sum -c zerorun-pilot-linux-amd64.tar.gz.sha256
tar -xzf zerorun-pilot-linux-amd64.tar.gz
cd zerorun-pilot-linux-amd64
./install.sh
zerorun --version
```

Expected version:

```text
zerorun 0.4.0
```

The default installer target is `$HOME/.local/bin/zerorun` and does not require root access.

## Configuration

The supplied `.zerorun.json` template starts with reuse disabled until the source closure and pinned image are reviewed.

The relevant identity includes:

- exact command;
- reviewed project-relative source inputs;
- declared environment variables that affect the result;
- immutable `image@sha256:<digest>` runtime identity;
- Linux/amd64 platform and execution policy.

ZeroRun does not automatically prove that the declared source closure is complete. If the closure cannot be defended, the task should not be marked reviewed.

## Initial validation

After configuration:

```bash
zerorun doctor
zerorun run pilot-tests
zerorun run pilot-tests
zerorun run pilot-tests --verify
```

Healthy initial lifecycle:

```text
MISS_EXECUTED
HIT_REUSED
VERIFY_MATCH
```

Changed or uncertain evidence is expected to execute fresh. A conflict is something to investigate, not override.

## Coding-agent integration

The private package includes an `AGENTS.md` example. For a reviewed target, replace the direct test invocation in the agent loop with:

```bash
zerorun run pilot-tests
```

The agent must not weaken the source closure, runtime pinning, or safety policy to increase hit rate.

## Pilot metrics

Participants can create a sanitized aggregate report:

```bash
zerorun pilot-export --output zerorun-pilot-report.json
```

The export intentionally excludes source code, commands, raw environment values, repository paths, cache keys, task names, reasons, and raw events.

For the external validation program, ZeroRun also records an agreed direct baseline and counts genuine chronological edit → test requests separately.

## Apply

Private pilot: https://zero-run.onrender.com/contact

Do not post confidential source code, credentials, tokens, private keys, or sensitive repository details in public issues.
