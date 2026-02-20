# 🛞 nautilus-trader-wheels

Pre-built [`nautilus_trader`](https://github.com/nautechsystems/nautilus_trader) wheels for **Linux ARM64** and **x86_64** — skip the 1–2 hour source compile.

| | Detail |
|---|---|
| **Architectures** | `aarch64`, `x86_64` |
| **Python** | 3.12 |
| **Build system** | Cython + Rust (PyO3) via `uv build --wheel` |
| **Schedule** | Weekly (Sundays 04:00 UTC) + manual dispatch |
| **Pinned commit** | [`e8e685e4`](https://github.com/nautechsystems/nautilus_trader/commit/e8e685e48b2fd47c20669ae9842dab85fba71ce7) |

## Install

### From GitHub Releases (recommended)

```bash
gh release download -R 3ScreensCapital/nautilus-trader-wheels -p "*.whl"
pip install nautilus_trader-*.whl
```

### From Actions Artifacts

```bash
gh run list -R 3ScreensCapital/nautilus-trader-wheels -w build-wheel.yml
gh run download <RUN_ID> -R 3ScreensCapital/nautilus-trader-wheels -n nautilus_trader-arm64-wheel
```

## Trigger a Build

```bash
# Both architectures, pinned commit
gh workflow run build-wheel.yml -R 3ScreensCapital/nautilus-trader-wheels

# Specific commit
gh workflow run build-wheel.yml \
  -R 3ScreensCapital/nautilus-trader-wheels \
  -f commit_sha=<COMMIT_SHA>

# Single architecture (arm64 or x86_64)
gh workflow run build-wheel.yml \
  -R 3ScreensCapital/nautilus-trader-wheels \
  -f architectures=arm64
```

## Releases

Wheels are published as GitHub Releases tagged `build-YYYYMMDD-<sha8>`. Artifacts are retained for 90 days.
