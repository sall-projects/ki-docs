# Source: https://kyara-intelligence.com/docs/quickstart

1. 1

 Create an API key

 Open the [dashboard](https://kyara-intelligence.com/dashboard) and create a key. It's shown once, so copy it somewhere safe. Store it as an environment variable rather than hard-coding it: `KYARA_INTELLIGENCE_API_KEY`.

2. 2

 Choose a model

 Browse the [model catalog](https://kyara-intelligence.com/models) and copy a model id. This guide uses `deepseek/deepseek-v4-flash` as a fast, low-cost default.

3. 3

 Send a request

 Point your OpenAI client at the Kyara base URL and call chat completions:

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

Install the SDK

Install the official OpenAI SDK first: `npm install openai` for JavaScript, or `pip install openai` for Python. Any OpenAI-compatible SDK works with the same base URL.

## What's next

See [Chat completions](https://kyara-intelligence.com/docs/api/chat-completions) for the full request and streaming options, or connect an app such as [SillyTavern](https://kyara-intelligence.com/docs/sillytavern).