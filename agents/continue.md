# Continue → any OpenAI-compatible endpoint

In `~/.continue/config.yaml` (or workspace `config.yaml`):

```yaml
models:
  - name: My model
    provider: openai
    model: your-model-id
    apiBase: https://your-endpoint.example.com/v1
    apiKey: your-key
```

Docs: https://docs.continue.dev/customize/model-providers/openai
