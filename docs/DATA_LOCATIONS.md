# Data locations (training vs ship)

## Ship (this repo + HF)

- Head packs under `packs/`
- Encoder weights: Hugging Face `weighting666/CBraMod` — pin SHA256 from `encoder/EXPECTED.json` / `pack_manifest.json`

## Public windows (shareable)

| Asset | Where |
|-------|--------|
| Derived window NPZs (`muse4_*`, `crown8_*`) | Hugging Face [`windwerfer/neurofeed-eeg-windows`](https://huggingface.co/datasets/windwerfer/neurofeed-eeg-windows) (license other) |
| Schemas, fixed splits, dataset cards, upload scripts | [`neurofeed_eeg_datasets`](https://github.com/windwerfer/neurofeed_eeg_datasets) |

Use HF + `neurofeed_eeg_datasets` for retrain/eval and any public redistribution of derived windows.

## Train / eval scratch (not for public redistribution)

| Dataset | Role | Host |
|---------|------|------|
| `muse-eeg-heads-windows` | Private window mirrors for GPU jobs | Kaggle **private** — training scratch only |
| `muse-eeg-heads-cache` (encoders, embeds) | Private emb/model cache (~30 GB local) | Kaggle **private** — **never publish** |
| Kaggle src / aeng | Private training scratch | Kaggle **private** — not a public share path |
| Training lab `muse-eeg-heads` | Experiments / encode/train | Local/unpublished (a future public train-lab repo is under discussion) |

Kaggle T4 kernels remain a convenient heavy encode/train path. They are **not** the canonical source of derived windows. Publish **heads-only** into this repo after metrics land; publish shareable windows to Hugging Face via `neurofeed_eeg_datasets`.
