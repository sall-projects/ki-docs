# Kyara Intelligence docs

This repo holds the customer-facing documentation for Kyara Intelligence (Mintlify).

## Writing style

- Do not use em dashes.

## Related repositories

These docs describe a product whose source lives in two sibling repos. When you need to confirm how something actually behaves (endpoints, parameters, error codes, UI copy, defaults), read the code there rather than guessing.

- **Proxy / API**: `/home/sal/Documents/KyaraAI/Stacks/kyaraai-proxy`. The OpenAI-compatible gateway that serves `api.kyara-intelligence.com`. Source of truth for endpoints, request validation, supported and rejected parameters, and error responses.
- **Frontend / fullstack**: `/home/sal/Documents/KyaraAI/Stacks/kyaraai-frontend`. The dashboard, onboarding flow, and model catalog. Source of truth for the sign-in and key-creation experience, plan and balance behavior, and anything a user sees in the web app.
