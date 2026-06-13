# Loop Engineering Ecosystem

**One discipline. Four repos. Zero schema drift.**

This is the official install map for the published v0.1 stack. Start here if you are building, benchmarking, or researching self-improving AI systems.

---

## The four layers

| # | Repository | Analogy | One line |
|---|------------|---------|----------|
| 1 | [**Loop Core Engineering**](https://github.com/KanakMalpani/Loop-Core-Engineering) | The HTTP spec | LSS, LES, validators, IDs |
| 2 | [**LoopNet**](https://github.com/KanakMalpani/loopnet) | ImageNet | 500 loop trajectories + failures |
| 3 | [**LoopGym**](https://github.com/KanakMalpani/LoopGym) | OpenAI Gym | Run loops (sim / live / replay) |
| 4 | [**LoopBench**](https://github.com/KanakMalpani/LoopBench) | MLPerf | Score loops on public tasks |

**Narrative home** (manifesto, patterns, case studies): [Loop Engineering](https://github.com/KanakMalpani/Loop-Engineering)

---

## Version pins (v0.1)

| Pin | Location |
|-----|----------|
| `lss@1.0.0` | [`specs/lss-1.0.schema.json`](specs/lss-1.0.schema.json) |
| `les@1.0.0` | [`specs/les-1.0.md`](specs/les-1.0.md) |
| `loopnet@0.1.0` | [loopnet](https://github.com/KanakMalpani/loopnet) |
| `loopgym@0.1.0` | [LoopGym](https://github.com/KanakMalpani/LoopGym) |
| `loopbench@0.1.0` | [LoopBench](https://github.com/KanakMalpani/LoopBench) |

---

## 5-minute full stack

```bash
# Specs & validators
git clone https://github.com/KanakMalpani/Loop-Core-Engineering.git

# Runtime + benchmarks (pip install from GitHub)
pip install git+https://github.com/KanakMalpani/LoopGym.git
pip install git+https://github.com/KanakMalpani/LoopBench.git

# First benchmark run
loopbench run \
  --task LB-CR-1 \
  --spec LoopBench/submissions/examples/spec-fast-loop.yaml \
  --seeds 0,1 \
  -o results.json

loopbench validate results.json
```

Clone [loopnet](https://github.com/KanakMalpani/loopnet) when you need ReplayEnv or dataset R&D.

---

## Data without cloning LoopNet

```python
from datasets import load_dataset

ds = load_dataset(
    "json",
    data_files="https://raw.githubusercontent.com/KanakMalpani/loopnet/main/data/seed/records.jsonl",
    split="train",
)
```

Hugging Face (after upload): `KanakMalpani/loopnet-seed-v0.1`

---

## Dependency graph

```
Loop Core Engineering
        │
        ├──► LoopNet (dataset)
        │
        └──► LoopGym (runtime) ──► LoopBench (measurement)
```

CI in downstream repos checks out **Loop Core Engineering** from GitHub — never a forked schema.

---

## Where to go next

| I want to… | Go to |
|------------|-------|
| Write a valid loop spec | [LSS 1.0 overview](specs/lss-1.0.md) |
| Understand scoring | [LES 1.0](specs/les-1.0.md) |
| Run a loop locally | [LoopGym README](https://github.com/KanakMalpani/LoopGym) |
| Get a public score | [LoopBench README](https://github.com/KanakMalpani/LoopBench) |
| Train on loop trajectories | [LoopNet DATACARD](https://github.com/KanakMalpani/loopnet/blob/main/DATACARD.md) |
| Read the philosophy | [Loop Engineering manifesto](https://github.com/KanakMalpani/Loop-Engineering) |
