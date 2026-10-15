# Kilo Code → any OpenAI-compatible endpoint

1. Open Kilo Code **Settings** → **Providers** tab, scroll down and click **Custom provider**.
2. **Base URL:** `https://your-endpoint.example.com/v1` (Kilo fetches the model list from `/v1/models` when the endpoint has one).
3. **API Key:** your key.
4. **Model:** the id your endpoint serves.

The same provider can live in `~/.config/kilo/kilo.json` (OpenCode-style `provider` block with `"npm": "@ai-sdk/openai-compatible"`), shared with the Kilo CLI.

Docs: https://kilo.ai/docs/ai-providers/openai-compatible
