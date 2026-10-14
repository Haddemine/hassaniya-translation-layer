# Hassaniya Translation Layer

Code and data for the paper **"Unlocking Hassaniya in LLMs: Bridging the Gap through a Translation Layer"** (I2COMSAPP'26).

> 🚧 The code and data are being prepared and will be added to this repository soon.

## Overview

Hassaniya, the Arabic dialect spoken mainly in Mauritania, is poorly served by large language models (LLMs). Instead of training a Hassaniya LLM, we connect Hassaniya speakers to existing LLMs through a **translation layer**:

```
User (Hassaniya)
      │  translation layer: Hassaniya → English
      ▼
English LLM (unmodified)
      │  translation layer: English → Hassaniya
      ▼
User (Hassaniya)
```

The LLM itself is never modified, so it keeps all its general capabilities and can be replaced by a newer model without retraining.

## Compared configurations

| | Configuration | Description |
|---|---|---|
| (A) | Direct GPT-4.1-mini | No translation layer (baseline) |
| (B) | Fine-tuned GPT-4.1-mini | Translation layer fine-tuned on our corpus |
| (C) | Fine-tuned Qwen2.5-3B | Open-weight translation layer, fine-tuned with LoRA |
| (D) | Few-shot GPT-4.1-mini | Unmodified GPT-4.1-mini prompted with examples retrieved from our corpus |

## Results

Human evaluation on a held-out test set of 120 examples across ten domains, scored by three independent native Hassaniya speakers (total score out of 360):

| Configuration | HA → EN | EN → HA | Conversation | chrF (EN → HA) |
|---|---|---|---|---|
| (A) Direct GPT-4.1-mini | 110 | 110 | 90 | 34.6 |
| (B) Fine-tuned GPT-4.1-mini | **324** | **287** | **277** | **83.2** |
| (C) Fine-tuned Qwen2.5-3B | 80 | 65 | 45 | 19.0 |
| (D) Few-shot GPT-4.1-mini | 305 | 265 | 270 | 80.1 |

See the paper for the full evaluation protocol.

## Repository contents (coming soon)

```
├── data/          # Hassaniya–English pairs we constructed
├── notebooks/     # Fine-tuning (LLaMA-Factory) and evaluation notebooks
├── src/           # Translation layer, few-shot retrieval, chat pipeline
└── README.md
```

## Data and licensing

- The Hassaniya–English pairs we constructed will be released in this repository.
- Pairs derived from third-party resources (DAH, the HASSANIYA dataset, Casablanca) are **not redistributed**; please obtain them from their original sources under their own licenses.
- The fine-tuned GPT-4.1-mini model cannot be shared, as it is hosted within the OpenAI platform.


## Contact

For questions or data access requests, please open an issue in this repository.
