# Cursor → any OpenAI-compatible endpoint

1. **Settings → Models**.
2. Enable **Override OpenAI Base URL** and set `https://your-endpoint.example.com/v1`.
3. Paste your key as the OpenAI API key.
4. Add your model id as a custom model name and enable it.

Notes:
- Overriding the base URL disables Cursor's built-in model list for that provider — you talk to your endpoint's models only.
- Custom keys only work with chat models; Tab completion keeps using Cursor's own models.
- Requests go through Cursor's servers, so the endpoint must be reachable over public HTTPS (`localhost` needs a tunnel).

Docs: https://cursor.com/help/models-and-usage/api-keys
