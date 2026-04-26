# rust-nightly

Reusable GitHub Action workflow for nightly Rust builds.

## What it does

- Runs full test suite with `--all-features --workspace`
- Builds in release mode
- Optional: run benchmarks
- Optional: upload coverage to Codecov
- Optional: create release (draft or prerelease)

## Usage

```yaml
name: Nightly

on:
  schedule:
    - cron: '0 0 * * *'
  workflow_dispatch:

jobs:
  nightly:
    uses: libnudget/rust-nightly/.github/workflows/nightly.yml@main
    with:
      rust-version: stable
      create-release: true
      release-tag: nightly
      release-draft: false
      release-prerelease: true
```

## Inputs

| Name | Type | Default | Description |
|------|------|---------|-------------|
| `rust-version` | string | `stable` | Rust toolchain version |
| `toolchain-components` | string | `rustfmt,clippy` | Rust components |
| `test-flags` | string | `--all-features --workspace` | cargo test flags |
| `build-flags` | string | `--release --all-features --workspace` | cargo build flags |
| `run-benchmarks` | boolean | `false` | Run benchmarks |
| `create-release` | boolean | `false` | Create release |
| `release-tag` | string | `nightly` | Release tag prefix |
| `release-draft` | boolean | `true` | Create as draft release |
| `release-prerelease` | boolean | `false` | Mark as prerelease |
| `codecov-token` | string | - | Codecov token |

## License

MIT
