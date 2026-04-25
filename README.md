# rust-nightly

Reusable GitHub Action workflow for nightly Rust builds.

## What it does

- Runs full test suite with `--all-features --workspace`
- Builds in release mode
- Optional: run benchmarks
- Optional: upload coverage to Codecov

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
      run-benchmarks: true
    secrets:
      codecov-token: ${{ secrets.CODECOV_TOKEN }}
```

## Inputs

| Name | Type | Default | Description |
|------|------|--------|-------------|
| `rust-version` | string | `stable` | Rust toolchain version |
| `toolchain-components` | string | `rustfmt,clippy` | Rust components |
| `test-flags` | string | `--all-features --workspace` | cargo test flags |
| `build-flags` | string | `--release --all-features --workspace` | cargo build flags |
| `run-benchmarks` | boolean | `false` | Run benchmarks |

## Secrets

| Name | Required | Description |
|------|----------|-------------|
| `codecov-token` | false | Codecov upload token |

## License

MIT
