# octomil-contract-bundles

Public distribution of **Octomil contract bundles**.

Each GitHub release `vX.Y.Z` carries one asset, `contract-bundle-X.Y.Z.tar.gz`: the
deterministic, generated **contract surface** (JSON schemas, OpenAPI spec, enums,
telemetry conventions, error codes, conformance tests, generated sources) for that
contract version.

- **Source of truth** is the private `octomil/octomil-contracts` repo. This repo holds
  only the published bundle artifacts — no source, no history.
- Bundles are published automatically by `octomil-contracts`' release workflow.
- SDK CI conformance gates download the matching bundle here **without authentication**.

Integrity: each bundle contains `contract-bundle.json` with per-file sha256 + sizes.
That manifest ships inside the archive, so it catches corruption or per-file edits but
does not authenticate the archive itself. Consumers that need tamper resistance should
pin the expected sha256 of the `.tar.gz` out-of-band and verify it before extracting.
