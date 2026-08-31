# Oh My Pi → any OpenAI-compatible endpoint

In `~/.omp/agent/models.yml` (create if missing):

```yaml
providers:
  myprovider:
    baseUrl: https://your-endpoint.example.com/v1
    api: openai-completions
    apiKey: your-key
    models:
      - id: your-model-id
```

Select with `/model` inside omp.

Docs: https://github.com/can1357/oh-my-pi
