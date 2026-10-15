# Qwen Code → any OpenAI-compatible endpoint

In `~/.qwen/settings.json`:

```json
{
  "modelProviders": {
    "openai": [
      {
        "id": "your-model-id",
        "name": "your-model-id (my provider)",
        "baseUrl": "https://your-endpoint.example.com/v1",
        "envKey": "MYPROVIDER_API_KEY"
      }
    ]
  },
  "security": { "auth": { "selectedType": "openai" } },
  "model": { "name": "your-model-id" }
}
```

```bash
export MYPROVIDER_API_KEY="your-key"
qwen
```

Notes:
- The free Qwen OAuth tier ended on 2026-04-15. Use an API key instead: this file, or `/auth` → **Custom Provider** inside the app.
- `model.name` must match an `id` under `modelProviders`. Switch models with `/model`.
- `baseUrl` is the `/v1` root, not the full `/chat/completions` URL.
- Anthropic-compatible endpoint: put the entry under `"anthropic": [...]` and set `"selectedType": "anthropic"`.

Docs: https://github.com/QwenLM/qwen-code/blob/main/docs/users/configuration/auth.md
