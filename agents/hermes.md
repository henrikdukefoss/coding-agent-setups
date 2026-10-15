# Hermes Agent → any OpenAI-compatible endpoint

Hermes resolves its provider from `~/.hermes/config.yaml`. `OPENAI_BASE_URL` is only read for the built-in OpenAI provider, so setting env vars alone doesn't switch it to your endpoint:

```yaml
model:
  provider: custom
  base_url: https://your-endpoint.example.com/v1
  default: your-model-id
  key_env: MYPROVIDER_API_KEY   # env var holding the key (or api_key: your-key)
```

Or run `hermes model` → **Custom endpoint** and enter the base URL, key and model name. For several endpoints, or an Anthropic-compatible one (`transport: anthropic_messages`), use named entries under `providers:`.

Docs: https://hermes-agent.nousresearch.com/docs/integrations/providers
