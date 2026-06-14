# PDF Understanding Skill for OpenCode

Converts PDF to structured markdown with text extraction, diagram
descriptions, and mermaid code generation via a vision model.

## Installation

1. Copy `.opencode/` into the root of your PDF project folder
2. Add `opencode.json` (or merge with existing)
3. Install poppler-utils:
   - Windows: `winget install --id=oschwartz10612.Poppler -e`
   - macOS: `brew install poppler`
   - Linux: `apt install poppler-utils`

## Usage

In opencode:
```
Use pdf-understanding skill on lecture.pdf
```

Result: `output/<filename>.md`

## Dependencies

- poppler-utils (pdftoppm)
- OpenCode Zen API key (free for MiMo V2.5 Free)

## Configuration

### Vision model

The skill uses `opencode/mimo-v2.5-free` by default. To use a
paid model (better accuracy, fewer rate limits), change the model
in `opencode.json` under `agent.pdf-vision-agent.model`:

```json
{
  "agent": {
    "pdf-vision-agent": {
      "model": "openai/gpt-5-nano"
    }
  }
}
```

Recommended vision models available through OpenRouter:

| Model | Context | Price (per 1M tok) | Notes |
|---|---|---|---|
| `xiaomi/mimo-v2.5` | 1M | $0.14/$0.28 | Best cost/perception, native omnimodal, Apr 2026 |
| `qwen/qwen3.5-flash-02-23` | 1M | $0.065/$0.26 | Fast vision-language MoE, Feb 2026 |
| `google/gemini-2.5-flash-lite` | 1M | $0.10/$0.40 | Lightweight reasoning, optional thinking, Jul 2025 |
| `openai/gpt-4o-mini` | 128K | $0.15/$0.60 | MMLU 82%, small & reliable, Jul 2024 |
| `openai/gpt-5-nano` | 400K | $0.05/$0.40 | Ultra-low latency, smallest GPT-5, Aug 2025 |

Higher-end models (`claude-opus-4.7`, `gemini-3-pro`) also work
but cost more than needed for PDF analysis.
