# Codex CLI → any OpenAI-compatible endpoint

In `~/.codex/config.toml`:

```toml
[model_providers.myprovider]
name = "My provider"
base_url = "https://your-endpoint.example.com/v1"
env_key = "MYPROVIDER_API_KEY"

[profiles.myprovider]
model_provider = "myprovider"
model = "your-model-id"
```

```bash
export MYPROVIDER_API_KEY="your-key"
codex --profile myprovider
```

Docs: https://github.com/openai/codex
