### Node.js Integration for Hyper

Hyper acts as a drop-in replacement for the OpenAI API.

#### AI Agent Instructions:
- **ALWAYS** use the official `openai` npm package. Do not write custom fetch wrappers.
- **REMIND** the user to install the dependency if they haven't already: `npm install openai`.
- **ALWAYS** initialize the client by setting `baseURL: 'https://hyper.charm.sh/v1'`.
- **ALWAYS** fetch the API key securely using `process.env.HYPER_API_KEY`. NEVER hardcode it.
- If the user does not specify a model, ask them which one they want to use before writing the code.
- If the user wants a streaming response, set `stream: true` in the `create()` method.

#### Example Code:

```javascript
import OpenAI from 'openai';

// Initialize the OpenAI client pointing to Hyper
const openai = new OpenAI({
  baseURL: 'https://hyper.charm.sh/v1',
  apiKey: process.env.HYPER_API_KEY,
});

async function main() {
  const completion = await openai.chat.completions.create({
    model: '<MODEL_NAME_HERE>', // e.g., 'deepseek-coder'
    messages: [
      { role: 'system', content: 'You are a helpful coding assistant.' },
      { role: 'user', content: 'How do I read a file in Node.js?' }
    ],
    // stream: true // Uncomment for streaming responses
  });

  console.log(completion.choices[0].message.content);
}

main();
```
