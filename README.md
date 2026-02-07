# nautilus-trader-wheels

Pre-built `nautilus_trader` wheels for **Linux ARM64** (aarch64).

## Why?

Building `nautilus_trader` from source takes 1-2 hours on ARM64 due to Cython + Rust compilation. This repo automates wheel builds via GitHub Actions on native ARM64 runners, so our GCP nodes can install pre-built wheels instead.

## Current Pinned Commit

```
1aa26492072d30a4eb5f08470bf439ee50911485
```

(from `nautechsystems/nautilus_trader`)

## How to Trigger a Build

### Manual (with optional commit override)

```bash
gh workflow run build-wheel.yml \
  -R 3ScreensCapital/nautilus-trader-wheels \
  -f commit_sha=<COMMIT_SHA>
```

### Automatic

Runs weekly on Sundays at 04:00 UTC.

## How to Consume the Wheel

### Option 1: Download from GitHub Releases

```bash
# List available releases
gh release list -R 3ScreensCapital/nautilus-trader-wheels

# Download latest wheel
gh release download -R 3ScreensCapital/nautilus-trader-wheels -p "*.whl"

# Install
pip install nautilus_trader-*.whl
```

### Option 2: Download from Actions Artifacts

```bash
# Find the latest run
gh run list -R 3ScreensCapital/nautilus-trader-wheels -w build-wheel.yml

# Download artifact
gh run download <RUN_ID> -R 3ScreensCapital/nautilus-trader-wheels -n nautilus_trader-arm64-wheel
```

### Option 3: Direct URL in pip/uv

Once a release exists, you can point pip at the wheel URL:

```bash
pip install "https://github.com/3ScreensCapital/nautilus-trader-wheels/releases/download/<TAG>/nautilus_trader-<version>-cp312-cp312-linux_aarch64.whl"
```

## Build Details

- **Platform:** Linux ARM64 (ubuntu-22.04-arm runner)
- **Python:** 3.12
- **Build system:** Cython + Rust (PyO3) via `uv build --wheel`
- **Build mode:** release
