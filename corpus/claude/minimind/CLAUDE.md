# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

MiniMind is an educational, from-scratch implementation of a small language model (25.8M–145M params) in PyTorch. All core algorithms (pretraining, SFT, LoRA, DPO, PPO, GRPO, SPO, distillation) are implemented natively without relying on third-party training abstractions. The project is primarily in Chinese with bilingual comments.

## Repository Structure

- `model/` — Model definitions and tokenizer files
  - `model_minimind.py` — `MiniMindConfig`, `MiniMindForCausalLM` (Dense + MoE), RoPE with YaRN scaling, GQA attention, RMSNorm. Inherits from `PreTrainedModel` + `GenerationMixin` for HF compatibility.
  - `model_lora.py` — From-scratch LoRA implementation (`apply_lora`, `save_lora`, `load_lora`). Only applies to square Linear layers.
  - `tokenizer.json`, `tokenizer_config.json` — BPE tokenizer (vocab_size=6400), uses `<|im_start|>`/`<|im_end|>` special tokens.
- `trainer/` — All training scripts, run from within this directory (`cd trainer`)
  - `trainer_utils.py` — Shared utilities: `MiniMindConfig` instantiation, checkpoint save/resume (`lm_checkpoint`), DDP init, LR schedule (cosine), `init_model`, `SkipBatchSampler`
  - `train_pretrain.py` — Pretraining on raw text (jsonl)
  - `train_full_sft.py` — Full supervised fine-tuning
  - `train_lora.py` — LoRA fine-tuning (freezes base, trains only LoRA params)
  - `train_dpo.py` — Direct Preference Optimization
  - `train_ppo.py` — PPO with CriticModel (RLAIF)
  - `train_grpo.py` — Group Relative Policy Optimization (RLAIF)
  - `train_spo.py` — Self-Play Optimization with adaptive value tracker (RLAIF)
  - `train_reason.py` — Reasoning model training with `<think>`/`<answer>` tags
  - `train_distillation.py` — White-box knowledge distillation (KL divergence)
  - `train_tokenizer.py` — Reference script for BPE tokenizer training (not normally needed)
- `dataset/` — Dataset loading (`lm_dataset.py` defines `PretrainDataset`, `SFTDataset`, `DPODataset`, `RLAIFDataset`)
- `scripts/` — Inference and serving
  - `serve_openai_api.py` — FastAPI OpenAI-compatible API server
  - `chat_openai_api.py` — Client for the API server
  - `web_demo.py` — Streamlit chat UI
  - `convert_model.py` — Convert torch checkpoints to HF Transformers or Llama format
- `eval_llm.py` — Interactive inference/eval script (auto-test or manual chat)

## Common Commands

All training scripts are executed from the `trainer/` directory.

```bash
# Install dependencies
pip install -r requirements.txt

# Pretraining (single GPU)
cd trainer && python train_pretrain.py --epochs 1 --batch_size 32 --hidden_size 512

# SFT (single GPU, loads pretrain weights by default)
cd trainer && python train_full_sft.py --epochs 2 --batch_size 16 --from_weight pretrain

# DDP multi-GPU training (any training script)
cd trainer && torchrun --nproc_per_node 2 train_pretrain.py

# LoRA fine-tuning
cd trainer && python train_lora.py --from_weight full_sft --data_path ../dataset/sft_mini_512.jsonl

# DPO training
cd trainer && python train_dpo.py --from_weight full_sft

# RLAIF (PPO/GRPO/SPO)
cd trainer && python train_grpo.py --from_weight full_sft

# Reasoning model training
cd trainer && python train_reason.py --from_weight full_sft

# Distillation
cd trainer && python train_distillation.py --from_weight full_sft

# Interactive inference
python eval_llm.py --weight full_sft --hidden_size 512

# OpenAI-compatible API server
cd scripts && python serve_openai_api.py

# Streamlit web demo
cd scripts && python web_demo.py

# Convert to HF Transformers format
cd scripts && python convert_model.py
```

## Model Variants

Controlled via `--hidden_size`, `--num_hidden_layers`, and `--use_moe` args:

| Variant | hidden_size | num_hidden_layers | use_moe | Params |
|---------|------------|-------------------|---------|--------|
| Small   | 512        | 8                 | 0       | ~26M   |
| Base    | 768        | 16                | 0       | ~104M  |
| MoE     | 640        | 8                 | 1       | ~145M  |

## Architecture Details

- **Attention**: Grouped-Query Attention (GQA) with 8 heads and 2 KV heads by default. Flash attention auto-enabled when available.
- **Position encoding**: RoPE with optional YaRN scaling for long-context extrapolation (`--inference_rope_scaling`).
- **MoE**: DeepSeek-style with shared experts + routed experts, softmax gating, auxiliary load-balancing loss.
- **Weight tying**: `embed_tokens.weight` is tied to `lm_head.weight`.
- **Chat template**: Uses `<|im_start|>`/`<|im_end|>` format (ChatML-style), applied via `tokenizer.apply_chat_template()`.

## Key Conventions

- **Weight file naming**: `{stage}_{hidden_size}[_moe].pth` (e.g., `pretrain_512.pth`, `full_sft_512_moe.pth`). Stored in `out/` directory.
- **Resume checkpoints**: Stored in `checkpoints/` with `_resume.pth` suffix, containing model, optimizer, scaler, epoch, step, and wandb_id.
- **Training pipeline order**: pretrain → full_sft → (optional: lora / dpo / ppo / grpo / spo / reason / distillation)
- **`--from_weight`**: Controls which checkpoint stage to load from. Use `none` to train from scratch.
- **`--from_resume 1`**: Enables automatic checkpoint resume (supports cross-GPU-count recovery).
- **Logging**: `swanlab` (imported as `wandb`) for training visualization, enabled with `--use_wandb`.
- **All trainer scripts** use `sys.path.append` to add the project root, and set `__package__ = "trainer"` for relative imports. Scripts must be run from the `trainer/` directory.
- **Labels convention**: `-100` for ignored tokens (padding and prompt tokens in SFT). SFT only trains on assistant responses between `bos_token + "assistant\n"` and `eos_token + "\n"` boundaries.
- **Dataset format**: All datasets use `.jsonl` format. Pretrain uses `{"text": "..."}`, SFT uses `{"conversations": [...]}` with role/content pairs.
