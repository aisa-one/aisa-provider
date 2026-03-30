---
name: aisa-models
description: |
  Use PROACTIVELY when the user asks about Chinese AI models, wants to call Qwen/Kimi/DeepSeek/GLM/MiniMax/Seed APIs,
  needs a unified gateway for multiple LLM providers, or asks about AIsa API usage, pricing, or model selection.
  Also use when comparing Chinese AI models or setting up multi-model inference pipelines.
version: 1.0.0
---

# AIsa Model Provider

AIsa provides a single OpenAI-compatible API endpoint for China's top AI models.

**Base URL:** `https://api.aisa.one/v1`
**Auth:** `Authorization: Bearer $AISA_API_KEY`

## Available Models

| Model ID              | Name          | Input        | Reasoning | Context |
|-----------------------|---------------|--------------|-----------|---------|
| `minimax-m2.1`        | MiniMax M2.1  | text         | No        | 200k    |
| `kimi-k2.5`           | Kimi K2.5     | text         | Yes       | 256k    |
| `qwen3-max`           | Qwen3 Max     | text, image  | Yes       | 256k    |
| `glm-5`               | GLM-5         | text, image  | Yes       | 200k    |
| `deepseek-v3.2`       | DeepSeek V3.2 | text         | Yes       | 128k    |
| `seed-1-8-251228`     | Seed 1.8      | text         | Yes       | 128k    |

## Quick Start

```bash
export AISA_API_KEY="your-key"

# Chat completion (OpenAI-compatible)
curl https://api.aisa.one/v1/chat/completions \
  -H "Authorization: Bearer $AISA_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{
    "model": "kimi-k2.5",
    "messages": [{"role": "user", "content": "Hello"}]
  }'
```

## Model Selection Guide

- **Best reasoning:** Kimi K2.5 (256k context, strong reasoning)
- **Best multimodal:** Qwen3 Max or GLM-5 (text + image)
- **Best cost-efficiency:** DeepSeek V3.2 ($0.28/$0.42 per M tokens)
- **Fastest:** MiniMax M2.1 (no reasoning overhead)
- **Largest context for code:** Kimi K2.5 (256k)

## Integration with Code

```python
from openai import OpenAI

client = OpenAI(
    api_key="your-aisa-api-key",
    base_url="https://api.aisa.one/v1"
)

response = client.chat.completions.create(
    model="kimi-k2.5",
    messages=[{"role": "user", "content": "Explain this code"}]
)
```

## Pricing (per million tokens)

| Model            | Input   | Output  |
|------------------|---------|---------|
| MiniMax M2.1     | $0.21   | $0.84   |
| Kimi K2.5        | $0.40   | $2.11   |
| Qwen3 Max        | $0.72   | $3.60   |
| GLM-5            | $1.00   | $3.20   |
| DeepSeek V3.2    | $0.28   | $0.42   |
| Seed 1.8         | $0.23   | $1.80   |

Every response includes `usage.cost` and `usage.credits_remaining`.

## Get Started

1. Sign up at [aisa.one](https://aisa.one)
2. Get your API key from the dashboard
3. Add credits (pay-as-you-go)
4. Set `export AISA_API_KEY="your-key"`

Full API reference: [docs.aisa.one](https://aisa.mintlify.app/api-reference/introduction)
