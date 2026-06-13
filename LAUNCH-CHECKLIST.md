# Launch checklist — v0.1 public stack

Complete these once per machine/account. Automations in CI depend on GitHub secrets.

## 1. Discipline repo

- [x] Push [Loop-Engineering](https://github.com/KanakMalpani/Loop-Engineering) narrative mirror

## 2. PyPI (LoopGym → LoopBench)

1. Register projects at https://pypi.org/ : `loopgym`, `loopbench`
2. Create a PyPI API token (entire account or per-project).
3. Add secret **`PYPI_API_TOKEN`** to [LoopGym](https://github.com/KanakMalpani/LoopGym/settings/secrets/actions) and [LoopBench](https://github.com/KanakMalpani/LoopBench/settings/secrets/actions) secrets.
4. Re-run publish (releases **v0.1.0** already exist):
   ```bash
   gh workflow run publish.yml -R KanakMalpani/LoopGym
   # after LoopGym succeeds:
   gh workflow run publish.yml -R KanakMalpani/LoopBench
   ```
5. Verify: `pip install loopgym loopbench`

> **Note:** v0.1.0 releases were created; first publish failed without `PYPI_API_TOKEN`. Workflow now skips OIDC and requires the token explicitly.

## 3. Hugging Face (LoopNet)

1. Create token at https://huggingface.co/settings/tokens (write).
2. Add **`HF_TOKEN`** to [loopnet secrets](https://github.com/KanakMalpani/loopnet/settings/secrets/actions).
3. Run **Actions → Upload to Hugging Face** (default dataset: `KanakMalpani/loopnet-seed-v0.1`).
4. Verify:
   ```python
   from datasets import load_dataset
   ds = load_dataset("KanakMalpani/loopnet-seed-v0.1", split="train")
   ```

## 4. GitHub discoverability

- [x] Repository topics on all stack repos
- [ ] **Pin repos on your profile** (manual — no public API): GitHub profile → Customize pins → add Loop Core Engineering, loopnet, LoopGym, LoopBench

## 5. Demo assets

- [x] `assets/demo.gif` on LoopBench README
