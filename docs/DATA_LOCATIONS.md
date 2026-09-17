# Data locations (training vs ship)

## Ship (this repo + HF)

- Head packs under `packs/`
- Encoder weights: Hugging Face `weighting666/CBraMod` — pin SHA256 from `encoder/EXPECTED.json` / `pack_manifest.json`

## Train / eval (not in git)

| Dataset | Approx size (local) | Suggested host |
|---------|---------------------|----------------|
| `muse-eeg-heads-cache` (encoders, embeds) | ~30 GB | Kaggle private dataset |
| `muse-eeg-heads-windows` | large | Kaggle private dataset |
| `datasets/vigilance_sleep_edf` windows | ~8 MB meta/windows slice | Optional GH LFS; prefer keep with training tree |

Kaggle kernels (T4) remain the heavy encode/train path. Publish **heads-only** into this repo after metrics land.
