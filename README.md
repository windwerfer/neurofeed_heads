# neurofeed_heads

Companion to [`windwerfer/neurofeed`](https://github.com/windwerfer/neurofeed): **versioned frozen model packs** (task heads + manifests) for Muse and Crown.

This repo is **not** the training lab ([`neurofeed_train`](https://github.com/windwerfer/neurofeed_train)). It ships what the app loads. Related: in-progress [`feedback_gym`](https://github.com/windwerfer/neurofeed/tree/main/feedback_gym).

## What lives where

| Asset | Where | Why |
|-------|--------|-----|
| Head `.pt` + `pack_manifest.json` + labels/channels | **This repo** (`packs/`) | Small (KB–MB); pin by release tag |
| CBraMod encoder `pretrained_weights.pth` (~20 MB) | **Hugging Face** (`weighting666/CBraMod`); SHA256-pinned in manifest | Redistributable Apache-2.0; don’t duplicate in every commit |
| Derived window corpora (NPZ) | **Hugging Face** [`windwerfer/neurofeed-eeg-windows`](https://huggingface.co/datasets/windwerfer/neurofeed-eeg-windows) (`muse4_*`, `crown8_*`; license other); schemas/splits in [`neurofeed_eeg_datasets`](https://github.com/windwerfer/neurofeed_eeg_datasets) | Canonical public share path for retrain/eval |
| Private GPU scratch (windows mirrors, emb caches) | Kaggle `muse-eeg-heads-windows` / `muse-eeg-heads-cache` / src / aeng — **private training only** | Not for public redistribution; **never publish cache** |
| Training code / experiments | [`neurofeed_train`](https://github.com/windwerfer/neurofeed_train) | R&D train/eval lab, not app runtime |

## Current ≥0.70 packs (for app testing)

See `packs/README.md`. Highlights: **CBraMod A-vig full 0.747** (ship), **CBraMod Crown HMC vig 0.670/0.680** (ship proxy), **CBraMod Head C 0.760** (probe), **REVE subsample A-vig/Head C ~0.78–0.79** + **REVE Crown HMC vig 0.649/0.681** (experimental heads-only; user brings gated base).

## Pack layout

```
packs/
  cbramod-spur-a/          # Muse A-vig ship path (frozen CBraMod + Head A)
    pack_manifest.json
    app_integration.json
    channels.json
    labels.json
    ATTRIBUTION.md
    encoder/EXPECTED.json  # SHA256 pin only (no giant .pth in git)
    heads/*.pt
```

App loads a **release tag** (e.g. `packs/cbramod-spur-a@v0.1.0`), verifies head SHA256s + encoder pin, then fetches encoder weights if missing.

## Devices

- **Muse (muse4):** AF7/AF8/TP9/TP10 — Spur A / CBraMod A-vig first.
- **Crown vig (HMC proxy):** shippable packs `cbramod-a-vig-crown2-hmc` (test **0.670**) and `cbramod-a-vig-crown4-hmc` (test **0.680**); experimental REVE siblings heads-only. Windows: HF `crown2_vigilance_hmc` / `crown4_vigilance_hmc` (HMC-only; F6≈F4, PO4≈O2). Do **not** mix with muse4 vig.
- **Crown attention (crown8):** HF has `crown8_*` attention windows; **still not shippable** (attention LOSO ~chance). Do not mix montages in one pack.

## License / ship policy

- **Original code/docs in this repo** (scripts, docs, pack manifest scaffolding authored here): **[Apache-2.0](LICENSE)** — see [`LICENSE`](LICENSE).
- **Published head artifacts** (`.pt` heads + pack manifests authored here): also **Apache-2.0**, and still subject to **dataset + encoder attribution** (see each pack’s `ATTRIBUTION.md`).
- This Apache grant does **not** re-license third-party encoders, gated REVE bases, or training corpora.
- Prefer open licenses for ship (Apache-2.0 encoder, heads with dataset attribution).
- Do **not** ship gated REVE base weights or LUNA in this repo.
- REVE remains optional/experimental in the app, user-local download.

## Contributing

All changes via **PR** (no direct pushes to the default branch).
