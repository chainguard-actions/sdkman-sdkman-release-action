<!-- markdownlint-disable -->

# Hardening Report: sdkman--sdkman-release-action/v0.2.0

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **sdkman--sdkman-release-action/v0.2.0** was hardened automatically. 1 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

The workflow file .github/workflows/check-dist.yml references three GitHub Actions using mutable version tags (@v4) instead of immutable 40-character SHA commit digests. This exposes the workflow to supply-chain attacks where a compromised or malicious tag update could execute arbitrary code in the runner. Failing references:
- `uses: actions/checkout@v4` (line 22)
- `uses: actions/setup-node@v4` (line 24)
- `uses: actions/upload-artifact@v4` (line 55)
Each should be pinned to a full SHA, e.g. `actions/checkout@11bd71901bbe5b1630ceea73d27597364c9af683 # v4`.

Locations:

- `.github/workflows/check-dist.yml:22`
- `.github/workflows/check-dist.yml:24`
- `.github/workflows/check-dist.yml:55`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses

**Notes:**

Pinned all three mutable @v4 action references in .github/workflows/check-dist.yml to immutable full SHA digests:
- actions/checkout@v4 → actions/checkout@34e114876b0b11c390a56381ad16ebd13914f8d5 # v4
- actions/setup-node@v4 → actions/setup-node@49933ea5288caeca8642d1e84afbd3f7d6820020 # v4
- actions/upload-artifact@v4 → actions/upload-artifact@ea165f8d65b6e75b540449e92b4886f43607fa02 # v4
The workflow already had a `permissions: contents: read` block, so no permissions changes were needed.

