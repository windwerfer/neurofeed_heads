# Packs (macro-F1 ≥ 0.70 for in-app testing)

Windows for retrain/eval live on Hugging Face [`windwerfer/neurofeed-eeg-windows`](https://huggingface.co/datasets/windwerfer/neurofeed-eeg-windows).

| Pack | Encoder | Task | Test macro-F1 | Ship? | Notes |
|------|---------|------|--------------:|:-----:|-------|
| `cbramod-a-vig-full` | CBraMod | A-vig drowsy/hypnagogic | **0.747** | **yes** | Full-corpus subject-holdout |
| `cbramod-head-c-wake-light` | CBraMod | wake/light | **0.760** | probe | Full corpus; not 4-way product |
| `reve-a-vig-subsample` | REVE-base | A-vig | **0.783** | no | **Experimental**; subsample metrics |
| `reve-head-c-wake-light-subsample` | REVE-base | wake/light | **0.791** | no | **Experimental**; subsample metrics |
| `cbramod-spur-a` | CBraMod | A-vig (older pack) | — | legacy | Earlier SC400-era pack; prefer `cbramod-a-vig-full` |

| `cbramod-a-vig-crown2-hmc` | CBraMod | A-vig Crown2 HMC | **0.670** | **yes** | HMC-only C3/C4; HF `crown2_vigilance_hmc` |
| `cbramod-a-vig-crown4-hmc` | CBraMod | A-vig Crown4 HMC | **0.680** | **yes** | HMC-only C3/C4/F6/PO4 (F6≈F4, PO4≈O2); HF `crown4_vigilance_hmc` |
| `reve-a-vig-crown2-hmc` | REVE-base | A-vig Crown2 HMC | **0.649** | yes* | **Experimental** heads-only; user brings gated base |
| `reve-a-vig-crown4-hmc` | REVE-base | A-vig Crown4 HMC | **0.681** | yes* | **Experimental** heads-only; user brings gated base |

## REVE license

\* Crown HMC vig packs meet the **≥0.60** HMC Crown vig proxy ship bar. REVE packs remain heads-only / experimental (user brings gated base). Crown **attention** is still not shippable. Never mix with muse4 vig.

Heads-only publish is OK. **Do not** commit REVE-base weights. App must download gated REVE from Hugging Face with the user’s account.

## Version tags

Optional git tags like `cbramod-a-vig-full/v1.0.0` pin what the app loads. “v0.2” was only an example tag name, not a separate model family.
