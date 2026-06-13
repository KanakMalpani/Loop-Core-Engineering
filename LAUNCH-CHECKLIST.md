# Launch checklist — v0.1 public stack

Complete these once per machine/account. Automations in CI depend on GitHub secrets.

## 1. Discipline repo

- [x] Push [Loop-Engineering](https://github.com/KanakMalpani/Loop-Engineering) narrative mirror

## 2. PyPI (LoopGym → LoopBench)

1. Register projects at https://pypi.org/ :
   - `loopgym`
   - `loopbench`
2. Create an API token (scope: each project or entire account).
3. Add repository secret **`PYPI_API_TOKEN`** to:
   - [LoopGym → Settings → Secrets](https://github.com/KanakMalpani/LoopGym/settings/secrets/actions)
   - [LoopBench → Settings → Secrets](https://github.com/KanakMalpani/LoopBench/settings/secrets/actions)
4. Publish order:
   ```bash
   gh release create v0.1.0 -R KanakMalpani/LoopGym --title "v0.1.0" --notes "Initial public release"
   # wait for Publish to PyPI workflow ✅
   gh release create v0.1.0 -R KanakMalpani/LoopBench --title "v0.1.0" --notes "Initial public release"
   ```
5. Verify: `pip install loopgym loopbench`

Workflow: [`.github/workflows/publish.yml`](.github/workflows/publish.yml) · Guide: [`PUBLISHING.md`](PUBLISHING.md)

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
- [x] Profile pinned repositories (Loop Core, LoopNet, LoopGym, LoopBench)

## 5. Demo assets

- [x] `assets/demo.gif` on LoopBench README
