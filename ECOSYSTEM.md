# Loop Engineering Ecosystem

Published v0.1 stack — install, pin, and cross-link from here.

| Repo | GitHub | Role | Install |
|------|--------|------|---------|
| **Loop Core Engineering** | [Loop-Core-Engineering](https://github.com/KanakMalpani/Loop-Core-Engineering) | LSS / LES specs, validators | `pip install git+https://github.com/KanakMalpani/Loop-Core-Engineering.git` |
| **LoopNet** | [loopnet](https://github.com/KanakMalpani/loopnet) | Dataset `ln/record-v1` | Clone + JSONL, or HF (see below) |
| **LoopGym** | [LoopGym](https://github.com/KanakMalpani/LoopGym) | Runtime (Sim / Live / Replay) | `pip install git+https://github.com/KanakMalpani/LoopGym.git` |
| **LoopBench** | [LoopBench](https://github.com/KanakMalpani/LoopBench) | Benchmarks + leaderboard | `pip install git+https://github.com/KanakMalpani/LoopBench.git` + LoopGym |

## Version pins (v0.1)

- `lss@1.0.0` — [specs/lss-1.0.schema.json](specs/lss-1.0.schema.json)
- `les@1.0.0` — [specs/les-1.0.md](specs/les-1.0.md)
- `loopgym@0.1.0` · `loopbench@0.1.0` · `loopnet@0.1.0`

## Quick full stack (local dev)

```bash
git clone https://github.com/KanakMalpani/Loop-Core-Engineering.git
git clone https://github.com/KanakMalpani/loopnet.git
git clone https://github.com/KanakMalpani/LoopGym.git
git clone https://github.com/KanakMalpani/LoopBench.git

pip install -e LoopGym -e LoopBench
loopbench run --task LB-CR-1 --spec LoopBench/submissions/examples/spec-fast-loop.yaml --seeds 0,1 -o results.json
```

## LoopNet without clone

```python
from datasets import load_dataset

ds = load_dataset(
    "json",
    data_files="https://raw.githubusercontent.com/KanakMalpani/loopnet/main/data/seed/records.jsonl",
    split="train",
)
```

After Hugging Face upload: `load_dataset("KanakMalpani/loopnet-seed-v0.1", split="train")`.

## CI dependency order

```
Loop Core Engineering → LoopNet (optional) → LoopGym → LoopBench
```

## Narrative docs

Manifesto, fundamentals, patterns, and case studies live in the **[Loop Engineering](https://github.com/KanakMalpani/Loop-Engineering)** discipline repo. **Schema authority stays in Loop Core Engineering.**
