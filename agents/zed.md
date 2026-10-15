# Zed → any OpenAI-compatible endpoint

In `settings.json`:

```json
{
  "language_models": {
    "openai_compatible": {
      "myprovider": {
        "api_url": "https://your-endpoint.example.com/v1",
        "available_models": [
          { "name": "your-model-id", "max_tokens": 128000 }
        ]
      }
    }
  }
}
```

Enter the key under **Settings → AI → LLM Providers** (stored in the system keychain), or set an env var named after the provider ID in upper snake case plus `_API_KEY` (`myprovider` → `MYPROVIDER_API_KEY`).

Docs: https://zed.dev/docs/ai/use-api-access
