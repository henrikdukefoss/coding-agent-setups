# Amp → any OpenAI-compatible endpoint

Amp routes chosen models to your endpoint through a **Custom URL** connection (available on every Amp tier).

1. **Settings → Model Routing → Add → Custom URL** (workspace admins: workspace Model Routing).
2. **Format:** `chat-completions` (also `responses`, `anthropic-messages`).
3. **Base URL:** `https://your-endpoint.example.com/v1` (Amp appends `/chat/completions`).
4. **API key:** your key (sent as `Authorization: Bearer`).
5. **Model mapping:** which of Amp's `provider/model` IDs go to this connection, one pattern per line:

```text
<amp-model-id> -> your-model-id     # send Amp's model to your endpoint under your endpoint's ID
-openai/*                           # exclude a group
```

6. In **Settings → Mode Dial → Tune Modes**, pick the mapped models for the modes that should use them.

Notes:
- Models that match no mapping line keep running on Amp.
- Pick the left-hand IDs from Amp's model picker; put your endpoint's exact model ID after `->`.
- The CLI has the same operations under `amp config model-providers`.

Docs: https://ampcode.com/docs/customize/model-routing
