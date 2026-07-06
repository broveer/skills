### Go Integration for Hyper

Hyper acts as a drop-in replacement for the OpenAI API. 

#### AI Agent Instructions:
- **ALWAYS** use the `github.com/sashabaranov/go-openai` library for Go integration.
- **REMIND** the user to install the dependency: `go get github.com/sashabaranov/go-openai`.
- **ALWAYS** override the base URL by setting `config.BaseURL = "https://hyper.charm.sh/v1"`.
- **ALWAYS** fetch the API key securely using `os.Getenv("HYPER_API_KEY")`. NEVER hardcode it.
- If the user does not specify a model, ask them which one they want to use before writing the code.
- If the user wants a streaming response, use the `CreateChatCompletionStream` method instead of `CreateChatCompletion`.

#### Example Code:

```go
package main

import (
	"context"
	"fmt"
	"os"

	"github.com/sashabaranov/go-openai"
)

func main() {
	// Fetch the API key
	apiKey := os.Getenv("HYPER_API_KEY")
	
	// Create a custom config that points to Hyper
	config := openai.DefaultConfig(apiKey)
	config.BaseURL = "https://hyper.charm.sh/v1"
	
	client := openai.NewClientWithConfig(config)

	resp, err := client.CreateChatCompletion(
		context.Background(),
		openai.ChatCompletionRequest{
			Model: "<MODEL_NAME_HERE>", // e.g., "deepseek-coder"
			Messages: []openai.ChatCompletionMessage{
				{
					Role:    openai.ChatMessageRoleSystem,
					Content: "You are a helpful coding assistant.",
				},
				{
					Role:    openai.ChatMessageRoleUser,
					Content: "Write a hello world in Go.",
				},
			},
			// Stream: true, // Set to true for streaming responses
		},
	)

	if err != nil {
		fmt.Printf("ChatCompletion error: %v\n", err)
		return
	}

	fmt.Println(resp.Choices[0].Message.Content)
}
```
