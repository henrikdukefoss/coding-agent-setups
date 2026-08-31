# Aider → any OpenAI-compatible endpoint

```bash
export OPENAI_API_BASE="https://your-endpoint.example.com/v1"
export OPENAI_API_KEY="your-key"
aider --model openai/your-model-id
```

Or persist in `~/.aider.conf.yml`:

```yaml
openai-api-base: https://your-endpoint.example.com/v1
openai-api-key: your-key
model: openai/your-model-id
```

The `openai/` prefix tells aider to use the OpenAI-compatible client for an unknown model id.

Docs: https://aider.chat/docs/llms/openai-compat.html
