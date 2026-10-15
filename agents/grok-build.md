# Grok Build → any OpenAI-compatible endpoint

xAI's terminal coding agent (`grok`). In `~/.grok/config.toml`:

```toml
[model.myprovider]
model = "your-model-id"                          # sent to the endpoint
base_url = "https://your-endpoint.example.com/v1"
name = "your-model-id (my provider)"             # shown in the model picker
env_key = "MYPROVIDER_API_KEY"                   # env var name, sent as Authorization: Bearer
api_backend = "chat_completions"                 # or "responses", or "messages" (Anthropic)
context_window = 128000

[models]
default = "myprovider"
```

```bash
export MYPROVIDER_API_KEY="your-key"
grok
```

Notes:
- Switch with `/model myprovider` or `grok -m myprovider`; `grok models` lists custom models too.
- Without `context_window`, a new model is treated as 200,000 tokens, which decides when auto-compaction runs.
- For an Anthropic-compatible endpoint, set `api_backend = "messages"` and keep `/v1` on the base URL.

Docs: https://github.com/xai-org/grok-build/blob/main/crates/codegen/xai-grok-pager/docs/user-guide/11-custom-models.md
