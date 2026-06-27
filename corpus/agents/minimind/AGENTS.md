# Repository Notes

This repository is a local working copy of `jingyaogong/minimind`, an educational PyTorch implementation of small language-model training and inference.

## Working Rules

- Treat this as an upstream-derived project. Keep upstream sync changes, local training changes, and local experiment assets in separate commits.
- Do not commit generated model weights, checkpoints, or local tool state. `checkpoints/`, `minimind_weights/`, `ikun-2.5B/`, `.playwright-mcp/`, and `.superpowers/` are local artifacts.
- Treat custom JSONL datasets under `dataset/` as sensitive until their source, license, and privacy status are reviewed.
- Training scripts are normally run from `trainer/`; preserve that path assumption unless refactoring all affected commands.
- Prefer syntax and import checks over training runs during repository maintenance. Full training requires GPU/MPS/CPU capacity and explicit dataset/weight choices.

## Relevant Commands

```bash
pip install -r requirements.txt
python3 -m py_compile dataset/lm_dataset.py eval_llm.py trainer/train_full_sft.py trainer/train_lora.py trainer/trainer_utils.py
git diff --check
```

Use the original README and `CLAUDE.md` for detailed training, SFT, LoRA, DPO, PPO, GRPO, SPO, distillation, API serving, and Streamlit commands.

