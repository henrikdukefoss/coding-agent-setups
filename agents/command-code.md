# Command Code → any OpenAI-compatible endpoint

Run `/connect` → **(BYOK) Add your own provider**, or edit `~/.commandcode/providers.json`:

```json
{
  "provider": {
    "myprovider": {
      "name": "My provider",
      "baseURL": "https://your-endpoint.example.com/v1",
      "apiKey": "$MYPROVIDER_API_KEY",
      "models": {
        "your-model-id": { "contextWindow": 128000 }
      }
    }
  }
}
```

Then pick the model with `/model`.

Notes:
- `apiKey` takes a reference, never the raw key (a pasted secret is refused): `"$NAME"`, `"{env:NAME}"`, `"!command"`, or `false` for keyless local servers.
- `api` defaults to `openai-completions`; also `openai-responses` and `anthropic-messages`.
- A URL pasted with `/chat/completions` on the end is trimmed to the `/v1` root.

Docs: https://commandcode.ai/docs/byok
