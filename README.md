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
      "model": "google/gemini-3-flash"
    }
  }
}
```

Recommended vision models available through OpenCode Zen:

| Model | MMMU Pro | Context | Notes |
|---|---|---|---|
| `google/gemini-3-flash` | 79% | 1M | Best balance of cost, speed and vision accuracy |
| `google/gemini-2.5-flash` | — | 1M | Reliable fallback, already in the skill |
| `openai/gpt-5.2-codex` | 75% | 400K | Strong coding + vision in one model |
| `kimi/k2.6` | 79.4% | 256K | Good open-source option for document analysis |
| `minimax/m3` | — | 1M | New multimodal model, strong on structured data |

Higher-end models (`claude-opus-4.7`, `gemini-3-pro`) also work
but cost more than needed for PDF analysis.
