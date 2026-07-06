### Python Integration for Hyper

Hyper acts as a drop-in replacement for the OpenAI API. 

#### AI Agent Instructions:
- **ALWAYS** use the official `openai` Python package. Do not write custom HTTP wrappers using `requests` unless explicitly asked.
- **REMIND** the user to install the dependency if they haven't already: `pip install openai`.
- **ALWAYS** initialize the client by setting `base_url="https://hyper.charm.sh/v1"`.
- **ALWAYS** fetch the API key securely using `os.environ.get("HYPER_API_KEY")`. NEVER hardcode it.
- If the user does not specify a model, ask them which one they want to use before writing the code.
- If the user wants a streaming response, set `stream=True` in the `create()` method.

#### Example Code:

```python
import os
from openai import OpenAI

# Initialize the client with Hyper's base URL and your API key
client = OpenAI(
    base_url="https://hyper.charm.sh/v1",
    api_key=os.environ.get("HYPER_API_KEY")
)

response = client.chat.completions.create(
    model="<MODEL_NAME_HERE>", # e.g., "deepseek-coder"
    messages=[
        {"role": "system", "content": "You are a helpful coding assistant."},
        {"role": "user", "content": "Write a python function to reverse a string."}
    ],
    # stream=True # Uncomment for streaming responses
)

print(response.choices[0].message.content)
```
