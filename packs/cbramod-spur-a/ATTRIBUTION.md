# Attribution — CBraMod Head A pack

## Encoder
- CBraMod pretrained weights — Apache-2.0 — weighting666/CBraMod (HF)
- Code — Apache-2.0 — wjq-learning/CBraMod
- Paper — Wang et al., CBraMod, ICLR 2025 / arXiv:2412.07236

## Training data (derived heads only)
- Sleep-EDF Expanded (PhysioNet) — attribute; W→drowsy, N1→hypnagogic
- Nights used in current heads: SC4001, SC4002, SC4011 (± SC4031 holdout)
- Open-license policy: no LUNA / L-FAME / SEED-VIG / BY-NC in shipping mix

## Channels
- Muse order: AF7, AF8, TP9, TP10
- Sleep-EDF proxy montage documented in channels.json

## Heads
- Head-only Linear classifiers (in_dim=200); MIT/BSD-preferred release posture
- Recommended binary default: head_a_binary_precision_tuned.pt (thresh 0.53)
- 4-way scaffold is not production-ready (attention classes untrained)

Pack built: 2026-09-07T01:39:28.857546+00:00
