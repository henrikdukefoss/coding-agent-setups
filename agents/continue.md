# Continue → any OpenAI-compatible endpoint

In `~/.continue/config.yaml` (or workspace `config.yaml`):

```yaml
models:
  - name: My model
    provider: openai
    model: your-model-id
    apiBase: https://your-endpoint.example.com/v1
    apiKey: your-key
    capabilities: [tool_use]   # Continue guesses capabilities from the model name; set this for agent mode
```

Docs: https://docs.continue.dev/customize/model-providers/top-level/openai
