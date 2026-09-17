# neurofeed_heads

Companion to [`windwerfer/neurofeed`](https://github.com/windwerfer/neurofeed): **versioned frozen model packs** (task heads + manifests) for Muse and Crown.

This repo is **not** the training lab (`muse-eeg-heads`). It ships what the app loads.

## What lives where

| Asset | Where | Why |
|-------|--------|-----|
| Head `.pt` + `pack_manifest.json` + labels/channels | **This repo** (`packs/`) | Small (KB–MB); pin by release tag |
| CBraMod encoder `pretrained_weights.pth` (~20 MB) | **Hugging Face** (`weighting666/CBraMod`) or private Kaggle cache; SHA256-pinned in manifest | Redistributable Apache-2.0; don’t duplicate in every commit |
| Window corpora / emb caches (GBs) | **Kaggle** private datasets (`muse-eeg-heads-windows`, `muse-eeg-heads-cache`) | Too large for GitHub; training only |
| Training code / experiments | `muse-eeg-heads` (or future training tree) | R&D, not app runtime |

## Current ≥0.70 packs (for app testing)

See `packs/README.md`. Highlights: **CBraMod A-vig full 0.747** (ship), **CBraMod Head C 0.760** (probe), **REVE subsample A-vig/Head C ~0.78–0.79** (experimental heads-only; user brings gated base).

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
- **Crown (crown8):** later packs; do not mix montages in one pack.

## License / ship policy

- Prefer open licenses for ship (Apache-2.0 encoder, heads with dataset attribution).
- Do **not** ship gated REVE base weights or LUNA in this repo.
- REVE remains optional/experimental in the app, user-local download.

## Contributing

All changes via **PR** (no direct pushes to the default branch).
