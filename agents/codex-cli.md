# Codex CLI → any Responses-API endpoint

Codex CLI only speaks the OpenAI **Responses API**: the endpoint must serve `POST /v1/responses`. `wire_api = "chat"` was removed, so a Chat-Completions-only endpoint needs a translating gateway (LiteLLM, for one) in between.

In `~/.codex/config.toml`:

```toml
model = "your-model-id"
model_provider = "myprovider"

[model_providers.myprovider]
name = "My provider"
base_url = "https://your-endpoint.example.com/v1"
env_key = "MYPROVIDER_API_KEY"
wire_api = "responses"
```

```bash
export MYPROVIDER_API_KEY="your-key"
codex
```

Notes:
- Provider tables only work in the user config (`~/.codex/config.toml`), not in a project `.codex/config.toml`.
- Since Codex 0.134.0, `--profile work` reads `~/.codex/work.config.toml`; `[profiles.work]` tables inside `config.toml` are no longer read.
- `openai`, `ollama` and `lmstudio` are reserved provider IDs.

Docs: https://developers.openai.com/codex/config-advanced
