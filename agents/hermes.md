# Hermes Agent → any OpenAI-compatible endpoint

Hermes resolves its provider from `~/.hermes/config.yaml` (not from `OPENAI_BASE_URL` alone — with only env vars set it falls back to its default provider):

```yaml
model:
  provider: custom
  base_url: https://your-endpoint.example.com/v1
  default: your-model-id
```

Add your API key where your Hermes version expects it (config or env) — see its docs for the exact field.

Docs: https://hermes-agent.nousresearch.com
