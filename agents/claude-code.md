# Claude Code → any Anthropic-compatible endpoint

Claude Code speaks the **Anthropic Messages API**, so the endpoint must serve `/v1/messages` (an OpenAI-only endpoint will not work).

```bash
export ANTHROPIC_BASE_URL="https://your-endpoint.example.com"   # no /v1 suffix
export ANTHROPIC_API_KEY="your-key"
claude
```

Notes:
- Some proxies also accept `ANTHROPIC_AUTH_TOKEN`; prefer `ANTHROPIC_API_KEY` unless your endpoint says otherwise.
- Model selection follows the endpoint's catalog; `/model` inside Claude Code shows what resolved.
- Known endpoints serving the Messages API besides Anthropic: self-hosted proxies (e.g. LiteLLM), and flat-rate services such as [Standard Compute](https://standardcompute.com/integrations/claude-code) (`ANTHROPIC_BASE_URL=https://api.stdcmpt.com`).

Docs: https://docs.claude.com/en/docs/claude-code
