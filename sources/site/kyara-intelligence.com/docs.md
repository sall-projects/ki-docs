# Source: https://kyara-intelligence.com/docs

Base URL `https://api.kyara-intelligence.com/v1`

Authentication `Bearer <API_KEY>`

Endpoint `POST /chat/completions`

## How it works

Kyara speaks the OpenAI Chat Completions API. To use it from any OpenAI SDK or compatible app, change just three things:

1. Set the base URL to `https://api.kyara-intelligence.com/v1`.
2. Use your Kyara API key as the bearer token.
3. Pick a model id from the catalog.

## Your first request

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

## Next steps

[Quickstart Make your first request in under a minute.](https://kyara-intelligence.com/docs/quickstart) [SillyTavern Connect the SillyTavern frontend to Kyara.](https://kyara-intelligence.com/docs/sillytavern) [OpenAI-compatible apps Point any OpenAI client at the gateway.](https://kyara-intelligence.com/docs/openai-compatible) [API reference Chat completions, streaming, and balance.](https://kyara-intelligence.com/docs/api/chat-completions)