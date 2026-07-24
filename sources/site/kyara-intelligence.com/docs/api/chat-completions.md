# Source: https://kyara-intelligence.com/docs/api/chat-completions

## Request

Send a standard OpenAI chat completions request with your Kyara key and a model id. Sampling parameters such as `temperature`, `top_p`, and `max_tokens` are passed through to the model (support varies per model; see the [catalog](https://kyara-intelligence.com/models)). Kyara is text-only: features like `tools` and `response_format` are not supported; see [unsupported features](https://kyara-intelligence.com/docs/unsupported-features) for the full list.

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

## Response

The response matches the OpenAI schema:

Copy

```
{
  "id": "chatcmpl-abc123",
  "object": "chat.completion",
  "model": "deepseek/deepseek-v4-flash",
  "choices": [
    {
      "index": 0,
      "message": { "role": "assistant", "content": "Hello! How can I help you today?" },
      "finish_reason": "stop"
    }
  ],
  "usage": { "prompt_tokens": 9, "completion_tokens": 9, "total_tokens": 18 }
}
```

## Streaming

Add `"stream": true` to receive the response as Server-Sent Events, token by token.

Copy

```
curl https://api.kyara-intelligence.com/v1/chat/completions \
  -H "Authorization: Bearer $KYARA_INTELLIGENCE_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{
    "model": "deepseek/deepseek-v4-flash",
    "stream": true,
    "messages": [
      { "role": "user", "content": "Hello!" }
    ]
  }'
```

Model availability

Model ids and pricing can change during early access. Treat the [models page](https://kyara-intelligence.com/models) as the current source of truth.