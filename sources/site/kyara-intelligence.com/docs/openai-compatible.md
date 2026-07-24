# Source: https://kyara-intelligence.com/docs/openai-compatible

## The three values

Wherever an app asks for OpenAI settings, supply:

- **Base URL**: the Kyara endpoint, including `/v1`.
- **API key**: your key from the [dashboard](https://kyara-intelligence.com/dashboard).
- **Model**: a model id from the [catalog](https://kyara-intelligence.com/models).

Base URL `https://api.kyara-intelligence.com/v1`

Text generation only

Kyara implements the chat completions endpoint for text in, text out. Apps that depend on tool calling, structured outputs, vision, or audio will not have those features; see [unsupported features](https://kyara-intelligence.com/docs/unsupported-features).

Include /v1, not /chat/completions

Most clients append the route themselves. Use the base URL exactly as shown, ending in `/v1`. If an app explicitly asks for a full chat-completions URL, then add `/chat/completions`; otherwise leave it off.

## Generic example

Under the hood, every integration makes the same request:

curlJavaScriptPython

Copy

```
curl https://api.kyara-intelligence.com/v1/chat/completions \
  -H "Authorization: Bearer $KYARA_INTELLIGENCE_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{
    "model": "deepseek/deepseek-v4-flash",
    "messages": [
      { "role": "user", "content": "Hello!" }
    ]
  }'
```

## Popular apps

Short notes for a few common clients. The setup is the same idea everywhere.

[Cherry Studio Add a provider of type "OpenAI", set the API host to the base URL, paste your key, and add a model id.](https://www.cherry-ai.com/) [Open WebUI Settings → Connections → add an OpenAI API connection with the base URL and your key.](https://openwebui.com/) [Continue (VS Code / JetBrains) Add a model with provider "openai", set apiBase to the base URL, and apiKey to your key.](https://continue.dev/) [LibreChat Configure a custom endpoint with the base URL, your key, and the model ids you want to expose.](https://www.librechat.ai/)