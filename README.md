# Coding Agent Setups

Copy-paste configs for pointing popular coding agents at **any OpenAI-compatible (or Anthropic-compatible) endpoint** — local or cloud.

Every OpenAI-compatible client needs the same three settings; only *where they go* differs per tool:

| Setting | Example |
|---|---|
| **Base URL** | `http://localhost:11434/v1` (Ollama) · `https://openrouter.ai/api/v1` · `https://api.stdcmpt.com/v1` |
| **API key** | whatever your endpoint issues (local servers often accept any string) |
| **Model id** | the id your endpoint serves, e.g. `llama3.1:8b`, `deepseek/deepseek-v4`, `standardcompute` |

## Agents

| Agent | Config surface | Guide |
|---|---|---|
| Claude Code | `ANTHROPIC_BASE_URL` + `ANTHROPIC_API_KEY` env vars (Anthropic Messages API) | [agents/claude-code.md](agents/claude-code.md) |
| opencode | `opencode.json` provider block | [agents/opencode.md](agents/opencode.md) |
| Pi | `~/.pi/agent/models.json` | [agents/pi.md](agents/pi.md) |
| Aider | `OPENAI_API_BASE` env var or `~/.aider.conf.yml` | [agents/aider.md](agents/aider.md) |
| Codex CLI | `~/.codex/config.toml` `[model_providers]` | [agents/codex-cli.md](agents/codex-cli.md) |
| Cline | Settings → API Provider → "OpenAI Compatible" | [agents/cline.md](agents/cline.md) |
| Roo Code | Settings → "OpenAI Compatible" provider | [agents/roo-code.md](agents/roo-code.md) |
| Hermes Agent | `~/.hermes/config.yaml` `model:` block | [agents/hermes.md](agents/hermes.md) |
| Continue | `config.yaml` — model with `provider: openai` + `apiBase` | [agents/continue.md](agents/continue.md) |
| Cursor | Settings → Models → Override OpenAI Base URL | [agents/cursor.md](agents/cursor.md) |
| Kilo Code | Settings → "OpenAI Compatible" provider | [agents/kilo-code.md](agents/kilo-code.md) |
| Zed | `settings.json` `language_models` block, `api_url` | [agents/zed.md](agents/zed.md) |
| Oh My Pi | `~/.omp/agent/models.yml` | [agents/oh-my-pi.md](agents/oh-my-pi.md) |
| Trae IDE | Model settings → custom OpenAI-compatible model | [docs](https://docs.trae.ai) |

## Endpoints these configs work with

Any server or service speaking the OpenAI chat-completions format:

- **Local:** [Ollama](https://ollama.com) (`http://localhost:11434/v1`), [vLLM](https://github.com/vllm-project/vllm), [LM Studio](https://lmstudio.ai), [llama.cpp server](https://github.com/ggml-org/llama.cpp)
- **Aggregators / pay-per-token:** [OpenRouter](https://openrouter.ai), [Together](https://together.ai), [DeepInfra](https://deepinfra.com), [Groq](https://groq.com)
- **Flat-rate subscription:** [Standard Compute](https://standardcompute.com) (`https://api.stdcmpt.com/v1`, also serves the Anthropic Messages API for Claude Code)
- **First-party:** OpenAI, Anthropic (Messages API), and their official SDKs

Model availability, tool-calling support, and reasoning-parameter support vary by endpoint — check your provider's model list.

## Endpoint quirks

See [ENDPOINT-QUIRKS.md](ENDPOINT-QUIRKS.md) for the differences between endpoints that most often break agent setups (`developer` role, `reasoning_effort`, `/v1` suffix conventions, streaming tool calls).

## See what your agents cost

[tokenreceipt](https://github.com/henrikdukefoss/tokenreceipt) reads the local logs these agents write (Claude Code, Codex CLI, OpenCode, Gemini CLI, Cline, Roo, Kilo, Pi, Hermes) and prints your usage at API list prices as a receipt. Runs locally: `npx github:henrikdukefoss/tokenreceipt`.

## Related guides

Written by Standard Compute, which maintains this repo:

- [Claude Code with other models](https://standardcompute.com/claude-code-other-models) and [Codex CLI with non-OpenAI models](https://standardcompute.com/codex-cli-other-models): config, providers and trade-offs for the two agents that need the most setup.
- [Fixing "model does not exist" (404)](https://standardcompute.com/fix/model-not-found): wrong model ID, extra `/v1` and other causes.
- [Fixing "maximum context length exceeded" (400)](https://standardcompute.com/fix/context-length-exceeded): what it means when an agent sends more than the endpoint's model accepts.
- [Tool calling, MCP, streaming and caching through an LLM gateway](https://standardcompute.com/llm-gateway-compatibility): which features survive a proxy and which don't.
- [OpenCode on a fixed monthly price](https://standardcompute.com/opencode-flat-rate). Also in: [Español](https://standardcompute.com/opencode-precio-fijo) · [Português](https://standardcompute.com/opencode-preco-fixo) · [Deutsch](https://standardcompute.com/opencode-flatrate) · [Français](https://standardcompute.com/opencode-forfait)

## Contributing

PRs welcome: new agents, corrections, or additional endpoint quirks (e.g. `developer`-role compatibility flags). Keep entries factual and provider-neutral.

## License

MIT
