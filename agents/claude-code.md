# Claude Code → any Anthropic-compatible endpoint

Claude Code speaks the **Anthropic Messages API**, so the endpoint must serve `/v1/messages` (an OpenAI-only endpoint will not work).

```bash
export ANTHROPIC_BASE_URL="https://your-endpoint.example.com"   # no /v1 suffix
export ANTHROPIC_AUTH_TOKEN="your-key"                           # sent as Authorization: Bearer
claude
```

Notes:
- `ANTHROPIC_AUTH_TOKEN` sends the key as `Authorization: Bearer`; `ANTHROPIC_API_KEY` sends it as `x-api-key`. Use the one your endpoint documents; if unsure, start with `ANTHROPIC_AUTH_TOKEN` and switch on a 401. In interactive mode, `ANTHROPIC_API_KEY` needs a one-time approval before it replaces a saved claude.ai login.
- For an endpoint that serves non-Claude model IDs, also set `ANTHROPIC_MODEL` and `ANTHROPIC_DEFAULT_OPUS_MODEL` / `ANTHROPIC_DEFAULT_SONNET_MODEL` / `ANTHROPIC_DEFAULT_HAIKU_MODEL` (the Haiku one runs background tasks), or those calls ask for Claude model names.
- `/status` shows which base URL and credential are active.
- Known endpoints serving the Messages API besides Anthropic: self-hosted proxies (e.g. LiteLLM), and flat-rate services such as [Standard Compute](https://standardcompute.com/integrations/claude-code) (`ANTHROPIC_BASE_URL=https://api.stdcmpt.com`).

Docs: https://code.claude.com/docs/en/llm-gateway-connect
