# Packs (macro-F1 ≥ 0.70 for in-app testing)

| Pack | Encoder | Task | Test macro-F1 | Ship? | Notes |
|------|---------|------|--------------:|:-----:|-------|
| `cbramod-a-vig-full` | CBraMod | A-vig drowsy/hypnagogic | **0.747** | **yes** | Full-corpus subject-holdout |
| `cbramod-head-c-wake-light` | CBraMod | wake/light | **0.760** | probe | Full corpus; not 4-way product |
| `reve-a-vig-subsample` | REVE-base | A-vig | **0.783** | no | **Experimental**; subsample metrics |
| `reve-head-c-wake-light-subsample` | REVE-base | wake/light | **0.791** | no | **Experimental**; subsample metrics |
| `cbramod-spur-a` | CBraMod | A-vig (older pack) | — | legacy | Earlier SC400-era pack; prefer `cbramod-a-vig-full` |

## REVE license

Heads-only publish is OK. **Do not** commit REVE-base weights. App must download gated REVE from Hugging Face with the user’s account.

## Version tags

Optional git tags like `cbramod-a-vig-full/v1.0.0` pin what the app loads. “v0.2” was only an example tag name, not a separate model family.
