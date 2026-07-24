# Source: https://kyara-intelligence.com/docs/authentication

## Get your key

Create and manage keys in the [dashboard](https://kyara-intelligence.com/dashboard). A new key is shown only once; copy it immediately. You can regenerate a key at any time, which revokes the old one.

## Send the token

Pass the key in the `Authorization` header as a bearer token. The OpenAI SDKs do this for you when you set `apiKey`.

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

Keep your key secret

Treat the key like a password. Never embed it in client-side code or commit it to a repository. Read it from an environment variable such as `KYARA_INTELLIGENCE_API_KEY` on the server.

## Let users bring their own key

Building an app for other people? Instead of asking for keys manually, send users through the hosted [onboarding flow](https://kyara-intelligence.com/docs/api/onboarding) to create and return their own key.