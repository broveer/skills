### cURL Integration for Hyper

Using cURL is the most direct way to interact with the Hyper API.

#### AI Agent Instructions:
- **ALWAYS** set the `Authorization` header using the `HYPER_API_KEY` environment variable. NEVER hardcode the API key in the command.
- **ALWAYS** set the `Content-Type` to `application/json`.
- If the user does not specify a model, prompt them to choose one (e.g., Llama 3, DeepSeek, etc.) before providing the command. Do not guess the model.
- Streaming is supported out of the box. If the user wants a streaming response, add `"stream": true` to the JSON payload.

#### Example Command:

```bash
curl https://hyper.charm.sh/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer $HYPER_API_KEY" \
  -d '{
    "model": "<MODEL_NAME_HERE>",
    "messages": [
      {
        "role": "system",
        "content": "You are a helpful coding assistant."
      },
      {
        "role": "user",
        "content": "Write a hello world function in bash."
      }
    ]
  }'
```
