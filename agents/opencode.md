# opencode → any OpenAI-compatible endpoint

Add a provider block to `opencode.json` (project) or `~/.config/opencode/opencode.json` (global):

```json
{
  "provider": {
    "myprovider": {
      "npm": "@ai-sdk/openai-compatible",
      "name": "My provider",
      "options": {
        "baseURL": "https://your-endpoint.example.com/v1",
        "apiKey": "your-key"
      },
      "models": {
        "your-model-id": { "name": "Your model" }
      }
    }
  }
}
```

Then `/models` inside opencode and pick it. Local example: `"baseURL": "http://localhost:11434/v1"` for Ollama.

Docs: https://opencode.ai/docs/providers
