# jcode → any OpenAI-compatible endpoint

Add a named provider profile (writes `[providers.myprovider]` to `~/.jcode/config.toml`):

```bash
printf '%s' "your-key" | jcode provider add myprovider \
  --base-url https://your-endpoint.example.com/v1 \
  --model your-model-id \
  --api-key-stdin \
  --set-default

jcode --provider-profile myprovider auth-test --no-tool-smoke
```

Notes:
- `--api-key-stdin` keeps the key out of your shell history; `--api-key-env NAME` reads it from an env var; `--no-api-key` is for localhost servers.
- `--set-default` makes the profile the startup provider and model.
- Custom profiles are OpenAI-compatible (Chat Completions) only.

Docs: https://github.com/1jehuang/jcode/blob/master/OAUTH.md
