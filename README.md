# Coding Agent Setups

Copy-paste configs for pointing popular coding agents at **any OpenAI-compatible (or Anthropic-compatible) endpoint** — local or cloud.

Every OpenAI-compatible client needs the same three settings; only *where they go* differs per tool:

| Setting | Example |
|---|---|
| **Base URL** | `http://localhost:11434/v1` (Ollama) · `https://openrouter.ai/api/v1` · `https://api.stdcmpt.com/v1` |
| **API key** | whatever your endpoint issues (local servers often accept any string) |
| **Model id** | the id your endpoint serves, e.g. `llama3.1:8b`, `deepseek/deepseek-v4`, `standardcompute` |

## Agents

Last checked against each agent's docs: **2026-10-15**.

| Agent | Config surface | Guide |
|---|---|---|
| Claude Code | `ANTHROPIC_BASE_URL` + `ANTHROPIC_AUTH_TOKEN` (or `ANTHROPIC_API_KEY`) env vars (Anthropic Messages API) | [agents/claude-code.md](agents/claude-code.md) |
| opencode | `opencode.json` provider block | [agents/opencode.md](agents/opencode.md) |
| Pi | `~/.pi/agent/models.json` | [agents/pi.md](agents/pi.md) |
| Aider | `OPENAI_API_BASE` env var or `~/.aider.conf.yml` | [agents/aider.md](agents/aider.md) |
| Codex CLI | `~/.codex/config.toml` `[model_providers]` (Responses API only) | [agents/codex-cli.md](agents/codex-cli.md) |
| Cline | Settings → API Provider → "OpenAI Compatible" | [agents/cline.md](agents/cline.md) |
| Roo Code (shut down 2026-05-15) | Settings → "OpenAI Compatible" provider | [agents/roo-code.md](agents/roo-code.md) |
| Hermes Agent | `~/.hermes/config.yaml` `model:` block | [agents/hermes.md](agents/hermes.md) |
| Continue | `config.yaml` — model with `provider: openai` + `apiBase` | [agents/continue.md](agents/continue.md) |
| Cursor | Settings → Models → Override OpenAI Base URL | [agents/cursor.md](agents/cursor.md) |
| Kilo Code | Settings → Providers → Custom provider | [agents/kilo-code.md](agents/kilo-code.md) |
| Zed | `settings.json` `language_models` block, `api_url` | [agents/zed.md](agents/zed.md) |
| Oh My Pi | `~/.omp/agent/models.yml` | [agents/oh-my-pi.md](agents/oh-my-pi.md) |
| Qwen Code | `~/.qwen/settings.json` `modelProviders` | [agents/qwen-code.md](agents/qwen-code.md) |
| Grok Build | `~/.grok/config.toml` `[model.<id>]` | [agents/grok-build.md](agents/grok-build.md) |
| Amp | Settings → Model Routing → Custom URL | [agents/amp.md](agents/amp.md) |
| Command Code | `/connect` or `~/.commandcode/providers.json` | [agents/command-code.md](agents/command-code.md) |
| jcode | `jcode provider add` | [agents/jcode.md](agents/jcode.md) |
| DeepSeek Harness | Settings → Models → Custom model API | [agents/deepseek-harness.md](agents/deepseek-harness.md) |
| Trae IDE | Model settings → custom OpenAI-compatible model | [docs](https://docs.trae.ai/ide/models) |
| Gemini CLI | not supported: it only speaks the Gemini API (`GOOGLE_GEMINI_BASE_URL` changes the host, not the format) | [details](https://github.com/henrikdukefoss/agent-provider-configs#gemini-cli) |

More agents and assistants (Crush, Goose, Factory Droid, OpenClaw, GitHub Copilot in VS Code and CLI, JetBrains AI Assistant and Junie, Docker Agent, NanoClaw, Octop, Rakazo, nanoMuse) and the Magpie provider manager are covered, with Responses/Anthropic variants and per-agent gotchas, in the sibling repo [agent-provider-configs](https://github.com/henrikdukefoss/agent-provider-configs).

## Endpoints these configs work with

Any server or service speaking the OpenAI chat-completions format:

- **Local:** [Ollama](https://ollama.com) (`http://localhost:11434/v1`), [vLLM](https://github.com/vllm-project/vllm), [LM Studio](https://lmstudio.ai), [llama.cpp server](https://github.com/ggml-org/llama.cpp)
- **Aggregators / pay-per-token:** [OpenRouter](https://openrouter.ai), [Together](https://together.ai), [DeepInfra](https://deepinfra.com), [Groq](https://groq.com)
- **Flat-rate subscription:** [Standard Compute](https://standardcompute.com) (`https://api.stdcmpt.com/v1`, also serves the Anthropic Messages API for Claude Code)
- **First-party:** OpenAI, Anthropic (Messages API), and their official SDKs

[![Add to Magpie](https://usemagpie.ai/img/add-to-magpie.svg)](https://usemagpie.ai/import#name=Standard+Compute&id=standardcompute&chat=https%3A%2F%2Fapi.stdcmpt.com%2Fv1&anthropic=https%3A%2F%2Fapi.stdcmpt.com&website=https%3A%2F%2Fstandardcompute.com&keys=https%3A%2F%2Fstandardcompute.com%2Fdashboard%2Fapi-keys&icon=https%3A%2F%2Fstandardcompute.com%2Fapple-icon.png)

Using Magpie? One click adds Standard Compute as a provider (you paste your key in Magpie). Guide: https://standardcompute.com/integrations/magpie

Model availability, tool-calling support, and reasoning-parameter support vary by endpoint — check your provider's model list.

## Endpoint quirks

See [ENDPOINT-QUIRKS.md](ENDPOINT-QUIRKS.md) for the differences between endpoints that most often break agent setups (`developer` role, `reasoning_effort`, `/v1` suffix conventions, Responses-only clients, streaming tool calls).

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
