# Loop Core Engineering

[![validate-lss](https://github.com/KanakMalpani/Loop-Core-Engineering/actions/workflows/validate.yml/badge.svg)](https://github.com/KanakMalpani/Loop-Core-Engineering/actions/workflows/validate.yml)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Python 3.12+](https://img.shields.io/badge/python-3.12+-blue.svg)](https://www.python.org/downloads/)
[![LSS 1.0.0](https://img.shields.io/badge/LSS-1.0.0-green.svg)](specs/lss-1.0.schema.json)

**Canonical home for Loop Engineering specifications** — LSS, LES, taxonomy IDs, and cross-repo contracts.

This repo is the **root of the dependency graph** for the Loop Engineering ecosystem. Downstream projects pin specs from here rather than copying schema silently.

---

## Ecosystem

| Repo | Purpose |
|------|---------|
| **[Loop Core Engineering](https://github.com/KanakMalpani/Loop-Core-Engineering)** (this repo) | LSS / LES specs, validators, ID registry |
| **[LoopNet](https://github.com/KanakMalpani/loopnet)** | Loop trajectory dataset (`ln/record-v1`) |
| **[LoopGym](https://github.com/KanakMalpani/LoopGym)** | Runtime — create, run, and replay loops |
| **[LoopBench](https://github.com/KanakMalpani/LoopBench)** | Benchmark suite, submissions, leaderboards |

---

## Quick start

```bash
git clone https://github.com/KanakMalpani/Loop-Core-Engineering.git
cd Loop-Core-Engineering
pip install -r requirements.txt
python tools/validate_lss.py examples/minimal-loop.yaml
python tools/validate_all_examples.py
python tools/les_calculator.py --spec examples/minimal-loop.yaml --display
```

**Full ecosystem map:** [ECOSYSTEM.md](ECOSYSTEM.md)

On Windows, use `py -3.12` if the default Python lacks pip (requires Python 3.12+).

---

## Specifications (v1.0.0)

| Artifact | Pin | Path |
|----------|-----|------|
| LSS JSON Schema | `lss@1.0.0` | [`specs/lss-1.0.schema.json`](specs/lss-1.0.schema.json) |
| LSS overview | — | [`specs/lss-1.0.md`](specs/lss-1.0.md) |
| LES formulas | `les@1.0.0` | [`specs/les-1.0.md`](specs/les-1.0.md) |
| ID registry | — | [`specs/loop-ids.md`](specs/loop-ids.md) |
| Failure taxonomy | — | [`specs/failure-taxonomy.md`](specs/failure-taxonomy.md) |
| Semver policy | — | [`CHANGELOG.md`](CHANGELOG.md) |
| Cross-repo sync | — | [`SYNC.md`](SYNC.md) |
| RFC template | — | [`templates/rfc-template.md`](templates/rfc-template.md) |

### LES scale

- **Canonical:** `[0, 1]` for APIs and storage
- **Display:** `0–100` optional for reports (`les_display = les_normalized × 100`)

---

## Examples

Validated in CI:

- [`examples/minimal-loop.yaml`](examples/minimal-loop.yaml)
- [`examples/research-loop.yaml`](examples/research-loop.yaml)
- [`examples/multi-agent-loop.yaml`](examples/multi-agent-loop.yaml)

---

## Tools

| Script | Purpose |
|--------|---------|
| `tools/validate_lss.py` | Validate one YAML file against LSS schema |
| `tools/validate_all_examples.py` | CI entrypoint for all examples |
| `tools/les_calculator.py` | Design-time LES estimate from LSS structure |

---

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md). Spec changes require an RFC per [`templates/rfc-template.md`](templates/rfc-template.md).

---

## Status

v0.1 shipped — see [`STATUS.md`](STATUS.md).
