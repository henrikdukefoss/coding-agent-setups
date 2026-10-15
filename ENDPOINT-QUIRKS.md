# Endpoint quirks worth knowing

Things that differ between OpenAI-compatible endpoints and commonly break agent setups:

- **`developer` role:** reasoning-capable OpenAI models use a `developer` message role; many compatible servers (Ollama, vLLM, SGLang) only accept `system`. Tools with a compat flag (e.g. Pi's `supportsDeveloperRole: false`) need it set for those endpoints.
- **`reasoning_effort`:** passes through on some endpoints, rejected on others. If your agent lets you disable it (Pi: `supportsReasoningEffort: false`), do so for endpoints that 400 on it.
- **`/v1` suffix:** most OpenAI-compatible tools want the base URL **with** `/v1`; Anthropic-format tools (Claude Code) want it **without** (they append `/v1/messages` themselves).
  Not every Anthropic-format client follows that: OpenCode/Kilo Code (`@ai-sdk/anthropic`), Continue and Grok Build's `messages` backend want the Anthropic base URL **with** `/v1`.
- **Responses-only clients:** Codex CLI only calls `/v1/responses` (`wire_api = "chat"` was removed). An endpoint that only serves `/v1/chat/completions` needs a translating gateway in between.
- **Model id prefixes:** aider needs `openai/<id>` to route unknown ids through the OpenAI client; most other tools take the bare id.
- **Streaming tool calls:** a few proxies buffer tool-call deltas; if tool use hangs mid-stream, test with streaming off before blaming the agent.
- **Auth header shape:** OpenAI-format clients send `Authorization: Bearer <key>`. Anthropic-format endpoints usually read `x-api-key`; some read `Authorization: Bearer`. Claude Code sends Bearer with `ANTHROPIC_AUTH_TOKEN` and `x-api-key` with `ANTHROPIC_API_KEY`.

PRs with more (verified) quirks welcome.
