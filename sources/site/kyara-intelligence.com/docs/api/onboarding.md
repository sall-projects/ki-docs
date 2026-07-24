# Source: https://kyara-intelligence.com/docs/api/onboarding

Use the onboarding URL when your app needs each user to bring their own Kyara key. Add a `redirect` query parameter pointing back to your app:

URL `https://api.kyara-intelligence.com/onboard?redirect=https://your-app.com/callback`

## What the user sees

1. 1

 Sign in or create an account

 The user authenticates with Kyara, or signs up if they're new.

2. 2

 Review and generate a key

 Kyara explains what an API key is for, then the user generates one.

3. 3

 Return to your app

 The user is sent back to your `redirect` URL to finish connecting.

Redirect requirements

The `redirect` value must be a valid HTTP or HTTPS URL. Kyara shows the destination domain to the user before sending them back.