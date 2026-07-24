# Source: https://kyara-intelligence.com/docs/unsupported-features

## Summary

Kyara is text in, text out. The [chat completions endpoint](https://kyara-intelligence.com/docs/api/chat-completions) accepts standard OpenAI requests, and any [OpenAI-compatible app](https://kyara-intelligence.com/docs/openai-compatible) can connect, but the following capabilities are not available:

- **Function / tool calling**: `tools` and `tool_choice` are ignored.
- **Structured outputs and JSON mode**: `response_format` is ignored.
- **Vision**: image inputs are rejected; message content must be plain text.
- **Audio**: no audio input, output, speech, or transcription.
- **Embeddings**: no `/v1/embeddings` endpoint.

## Endpoints

Only the endpoints below exist. Every other OpenAI API path, including the ones listed as not available, returns `404 Not Found`.

| Endpoint | Status |
| --- | --- |
| `POST /v1/chat/completions` | **Available** (text generation only) |
| `GET /v1/models` | **Available** |
| `GET /v1/balance` | **Available** (Kyara extension, not part of the OpenAI API) |
| `/v1/completions` (legacy) | Not available |
| `/v1/embeddings` | Not available |
| `/v1/images/*` | Not available |
| `/v1/audio/*` | Not available |
| `/v1/responses` | Not available |
| `/v1/files`, `/v1/batches` | Not available |
| `/v1/fine_tuning/*` | Not available |
| `/v1/moderations` | Not available |
| `/v1/assistants`, `/v1/threads`, `/v1/vector_stores` | Not available |
| `/v1/realtime` | Not available |

## Request parameters

Chat completions requests are validated against an allowlist. Every parameter falls into one of three groups: forwarded to the model, silently ignored, or rejected with a `400` error.

### Supported

These parameters are accepted and passed through to the model:

- `model`, `messages`
- `temperature`, `top_p`, `top_k`, `presence_penalty`, `frequency_penalty`, `seed`
- `max_tokens`, `max_completion_tokens`, `stop`, `n`
- `stream`, `stream_options` (`include_usage`, `include_obfuscation`)
- `logprobs`, `top_logprobs`, `user`
- `reasoning` (object with `effort` and/or `max_tokens`)

### Silently ignored

Ignored parameters do not error

For client compatibility, unrecognized top-level parameters are removed from the request instead of rejected. Sending `tools` or `response_format` returns a normal response, but the model never sees them, so tool calls or structured output will simply not happen.

Notable parameters that are dropped this way:

- `tools`, `tool_choice`, `functions`, `parallel_tool_calls`
- `response_format` (JSON mode and structured outputs)
- `reasoning_effort` (use the nested `reasoning.effort` instead)
- `logit_bias`, `prediction`
- `modalities`, `audio`, `web_search_options`
- `store`, `metadata`, `service_tier`

### Rejected with an error

These request shapes return a `400` validation error:

- Message `content` that is not a plain string, such as multimodal content arrays with `image_url` or audio parts.
- Message roles other than `system`, `developer`, `user`, or `assistant`; there is no `tool` role.
- Unknown fields inside `messages`, `stream_options`, or `reasoning` objects.

## Notes

- `top_k` is accepted as an extension beyond the OpenAI standard, since many models support it.
- To control reasoning, send `"reasoning": { "effort": "medium" }` rather than the top-level `reasoning_effort`.
- Support for sampling parameters still varies per model; see the [catalog](https://kyara-intelligence.com/models).

This list can shrink

Unsupported today does not mean unsupported forever. Check back here as the platform evolves; newly added capabilities will move off this page and into the [API reference](https://kyara-intelligence.com/docs/api/chat-completions).