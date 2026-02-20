# 🛞 nautilus-trader-wheels

Pre-built [`nautilus_trader`](https://github.com/nautechsystems/nautilus_trader) wheels for **Linux** — skip the 1–2 hour source compile.

| | Detail |
| --- | --- |
| **Architectures** | `aarch64`, `x86_64` |
| **Python** | 3.12 |
| **Schedule** | Weekly (Sundays 04:00 UTC) + manual dispatch |
| **Pinned commit** | [`e8e685e4`](https://github.com/nautechsystems/nautilus_trader/commit/e8e685e48b2fd47c20669ae9842dab85fba71ce7) |

## Install

### From GitHub Releases (recommended)

```bash
gh release download -R 3ScreensCapital/nautilus-trader-wheels -p "*.whl"
pip install nautilus_trader-*.whl
```

### Direct URL

```bash
pip install "https://github.com/3ScreensCapital/nautilus-trader-wheels/releases/download/<TAG>/nautilus_trader-<version>-cp312-cp312-linux_aarch64.whl"
```

## Trigger a Build

```bash
# Pinned commit, both architectures
gh workflow run build-wheel.yml -R 3ScreensCapital/nautilus-trader-wheels

# Specific commit
gh workflow run build-wheel.yml -R 3ScreensCapital/nautilus-trader-wheels -f commit_sha=<SHA>

# Single architecture (arm64 or x86_64)
gh workflow run build-wheel.yml -R 3ScreensCapital/nautilus-trader-wheels -f architectures=arm64
```

## Releases

Wheels are published as GitHub Releases tagged `build-YYYYMMDD-<sha8>`. Artifacts are retained for 90 days.
