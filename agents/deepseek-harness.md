# DeepSeek Harness → any OpenAI-compatible endpoint

DeepSeek's agent harness (`dsh`, developer preview).

1. In the web UI: **Settings → Models → Add model provider**, switch the card to **Custom model API**.
2. **Provider ID:** lowercase, e.g. `myprovider` (permanent; to rename, add a new provider).
3. **Base URL:** `https://your-endpoint.example.com/v1`
4. **API protocol:** OpenAI Chat Completions (also OpenAI Responses, Anthropic Messages; one per provider).
5. **API key:** your key.
6. **Models:** **Fetch available models**, or type `your-model-id`.

The page saves to `$DSH_HOME/profiles/<profile>/cordis.patch.yml` (`web` for `dsh web`), which you can also edit by hand:

```yaml
- id: llm-pi-ai
  config:
    providers:
      myprovider:
        apiKeyEnv: MYPROVIDER_API_KEY
        api: openai-completions
        baseURL: https://your-endpoint.example.com/v1
        models:
          - id: your-model-id
```

If a gateway rejects every request with a working key, set `compat.supportsDeveloperRole: false` and `compat.maxTokensField: max_tokens` on the provider (see [ENDPOINT-QUIRKS.md](../ENDPOINT-QUIRKS.md)).

Docs: https://github.com/deepseek-ai/deepseek-harness/blob/master/docs/user/guide/providers.md
