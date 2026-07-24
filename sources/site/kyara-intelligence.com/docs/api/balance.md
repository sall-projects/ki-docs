# Source: https://kyara-intelligence.com/docs/api/balance

## Request

Call the balance endpoint with your API key to read exact credit balances and percentages:

Copy

```
curl https://api.kyara-intelligence.com/v1/balance \
  -H "Authorization: Bearer $KYARA_INTELLIGENCE_API_KEY"
```

## Response

Copy

```
{
  "object": "balance",
  "available": true,
  "plan": "lite",
  "balances": {
    "base": { "credits": 500000, "percent": 50 },
    "overage": { "credits": 25000000, "percent": 25 },
    "total": { "credits": 25500000, "percent": 25.25 }
  },
  "caps": {
    "base": { "credits": 1000000 },
    "overage": { "credits": 100000000 },
    "total": { "credits": 101000000 }
  },
  "baseWindow": {
    "startedAt": "2030-01-01T00:00:00.000Z",
    "refreshesAt": "2030-01-01T04:00:00.000Z"
  }
}
```

The endpoint verifies the API key, refreshes the base balance when its window is due, then reads the usage bucket. Unlike chat, it never blocks on an empty balance; it reports `available: false` when the total balance is exhausted.

Errors

Errors use the OpenAI-style format: invalid or missing keys return `401 authentication_error`; valid keys with missing or invalid balance data return `500 server_error`.