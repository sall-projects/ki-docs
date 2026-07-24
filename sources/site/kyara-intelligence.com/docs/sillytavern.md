# Source: https://kyara-intelligence.com/docs/sillytavern

SillyTavern talks to Kyara as a custom OpenAI-compatible source. You'll need your API key from the [dashboard](https://kyara-intelligence.com/dashboard) and a model id from the [catalog](https://kyara-intelligence.com/models).

Base URL `https://api.kyara-intelligence.com/v1`

Model `deepseek/deepseek-v4-flash`

![SillyTavern API Connections panel configured with Kyara base URL, API key, and model id.](https://kyara-intelligence.com/docs/sillytavern-configuration.png)

Example SillyTavern connection settings for Kyara.

## Step by step

1. 1

 Open the API Connections panel

 In SillyTavern, click the plug icon in the top bar to open **API Connections**.

2. 2

 Set API to Chat Completion

 Under **API**, choose `Chat Completion`.

3. 3

 Set the source to Custom

 Under **Chat Completion Source**, choose `Custom (OpenAI-compatible)`.

4. 4

 Enter the base URL

 In **Custom Endpoint (Base URL)**, paste:

 `https://api.kyara-intelligence.com/v1`

5. 5

 Paste your API key

 In **Custom API Key**, paste the key from your [dashboard](https://kyara-intelligence.com/dashboard), then click the save / connect button so it sticks.

6. 6

 Enter a model id

 In the **Model** field, enter a model id from the [catalog](https://kyara-intelligence.com/models), for example:

 `deepseek/deepseek-v4-flash`

7. 7

 Connect and test

 Click **Connect**, then **Test Message**. A **✨ Valid ✨** confirmation means you're live.

Mind the /v1

Your base URL must end in `/v1`. SillyTavern automatically appends `/chat/completions`, so don't add it yourself. A base URL of `https://api.kyara-intelligence.com/v1/chat/completions` will fail.

Not connecting?

Check three things: the base URL ends with `/v1` (and nothing more); the API key was actually saved (re-paste and hit save); and the model id has no typos. Copy it straight from the [catalog](https://kyara-intelligence.com/models) rather than typing it.

## Which model for roleplay?

Newcomers don't need to overthink it. Start with `deepseek/deepseek-v4-flash` for fast, inexpensive responses, then browse the [catalog](https://kyara-intelligence.com/models) for larger-context, character-tuned options as you settle into a favorite.

## Prefer the terminal?

Sanity-check your key before touching SillyTavern by sending one request directly:

Copy

```
curl https://api.kyara-intelligence.com/v1/chat/completions \
  -H "Authorization: Bearer $KYARA_INTELLIGENCE_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{
    "model": "deepseek/deepseek-v4-flash",
    "messages": [
      { "role": "user", "content": "ping" }
    ]
  }'
```