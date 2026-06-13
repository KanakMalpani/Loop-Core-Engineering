# Launch checklist — v0.1 public stack



Complete these once per machine/account. Automations in CI depend on GitHub secrets or PyPI trusted publishing.



## 1. Discipline repo



- [x] Push [Loop-Engineering](https://github.com/KanakMalpani/Loop-Engineering) narrative mirror



## 2. PyPI (LoopGym → LoopBench)



1. Register projects at https://pypi.org/ : `loopgym`, `loopbench`

2. On each PyPI project (`loopgym`, `loopbench`), add a **trusted publisher** (Owner `KanakMalpani`, workflow `publish.yml`, environment blank) **or** add **`PYPI_API_TOKEN`** to [LoopGym](https://github.com/KanakMalpani/LoopGym/settings/secrets/actions) and [LoopBench](https://github.com/KanakMalpani/LoopBench/settings/secrets/actions) secrets.

3. Re-run publish (releases **v0.1.0** already exist):

   ```bash

   gh workflow run publish.yml -R KanakMalpani/LoopGym

   # after LoopGym succeeds:

   gh workflow run publish.yml -R KanakMalpani/LoopBench

   ```

4. Verify: `pip install loopgym loopbench`



## 3. Hugging Face (LoopNet)



- [x] Add **`HF_TOKEN`** to [loopnet secrets](https://github.com/KanakMalpani/loopnet/settings/secrets/actions)

- [x] Upload dataset: [KanakMalpani/loopnet-seed-v0.1](https://huggingface.co/datasets/KanakMalpani/loopnet-seed-v0.1)

- [x] Verify:

   ```python

   from datasets import load_dataset

   ds = load_dataset("KanakMalpani/loopnet-seed-v0.1", split="train")

   ```



## 4. GitHub discoverability



- [x] Repository topics on all stack repos

- [ ] **Pin repos on your profile** (manual — no public API): GitHub profile → Customize pins → add Loop Core Engineering, loopnet, LoopGym, LoopBench



## 5. Demo assets



- [x] `assets/demo.gif` on LoopBench README


