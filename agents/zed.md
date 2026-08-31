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

Zed prompts for the API key on first use (stored in the system keychain).

Docs: https://zed.dev/docs/ai/configuration
