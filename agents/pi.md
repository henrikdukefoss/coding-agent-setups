# Pi → any OpenAI-compatible endpoint

Add the provider to `~/.pi/agent/models.json` (create if missing):

```json
{
  "providers": {
    "myprovider": {
      "baseUrl": "https://your-endpoint.example.com/v1",
      "api": "openai-completions",
      "apiKey": "your-key",
      "models": [
        { "id": "your-model-id" }
      ]
    }
  }
}
```

Select it with `/model` inside pi. For servers that reject the `developer` role or `reasoning_effort`, add:

```json
"compat": { "supportsDeveloperRole": false, "supportsReasoningEffort": false }
```

Docs: https://github.com/earendil-works/pi/blob/main/packages/coding-agent/docs/models.md
