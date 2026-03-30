# AIsa Provider Plugin

Unified API gateway for China's top AI models in Claude Code.

## What it does

Access 6+ leading Chinese AI models through a single API key and OpenAI-compatible endpoint:

- **Kimi K2.5** — 256k context, strong reasoning
- **Qwen3 Max** — Multimodal (text + image), reasoning
- **DeepSeek V3.2** — Cost-effective reasoning ($0.28/M input tokens)
- **GLM-5** — Multimodal, reasoning
- **MiniMax M2.1** — Fast inference, 200k context
- **Seed 1.8** — Reasoning, 128k context

## Installation

```bash
# In Claude Code
/plugin install aisa-provider
```

## Setup

```bash
export AISA_API_KEY="your-key"
```

Get your API key at [aisa.one](https://aisa.one).

## Components

```
aisa-provider/
├── .claude-plugin/
│   └── plugin.json
├── skills/
│   └── aisa-models/
│       └── SKILL.md
└── README.md
```

## Usage

Once installed, Claude Code automatically activates the `aisa-models` skill when you:

- Ask about Chinese AI models or providers
- Need to call Qwen, Kimi, DeepSeek, GLM, MiniMax, or Seed APIs
- Want to compare model capabilities or pricing
- Need help setting up multi-model inference

## License

MIT
