+++
title = "Go Genkit: Building AI-Powered Applications"
description = "A comprehensive guide to Google's Go Genkit framework for developing production-ready AI applications"
outputs = ["Reveal"]
[reveal_hugo]
custom_theme = "reveal-hugo/themes/genkit-modern.css"
margin = 0.1
highlight_theme = "github-dark"
transition = "slide"
transition_speed = "fast"
background_transition = "fade"
controls = true
progress = true
center = true
touch = true
fragments = true
auto_slide = 0
[reveal_hugo.templates.google_blue]
class = "google-blue"
background = "#4285f4"
[reveal_hugo.templates.google_green]
class = "google-green"
background = "#34a853"
+++

# 🚀 {.r-fit-text}

# Go Genkit {data-auto-animate="true"}

**Building AI-Powered Applications with Google's Framework**

{{% fragment class="fade-up" %}}
*Production-ready AI development made simple*
{{% /fragment %}}

{{% note %}}
Welcome everyone! Today we're diving into Go Genkit, Google's powerful framework for building AI applications. 
- Ask: Who has built AI applications before?
- Mention this is cutting-edge tech from the Firebase team
- Set expectation for hands-on examples
{{% /note %}}

---

## What is Go Genkit? {data-background-gradient="linear-gradient(45deg, #4285f4 0%, #34a853 100%)" data-transition="fade"}

<div class="r-vstack">

{{% fragment class="fade-in-then-semi-out" %}}
### 🏗️ Google's Open-Source Framework
Built by the Firebase team for creating AI-powered applications
{{% /fragment %}}

{{% fragment class="grow" %}}
### 🌍 Multi-Language Support
- **JavaScript/TypeScript** (Stable)
- **Go** (Beta) ← Today's focus  
- **Python** (Alpha)
{{% /fragment %}}

{{% fragment class="highlight-current-blue" %}}
### ⚡ Production-Ready Features
Monitoring, evaluation, deployment, and observability built-in
{{% /fragment %}}

</div>

{{% note %}}
- Emphasize Google's investment in AI tooling
- Point out Go is in beta but very capable
- Mention production-ready means enterprise features from day one
{{% /note %}}

---

## Why Choose Go Genkit? {data-auto-animate="true"}

<div class="r-hstack">
<div class="fragment highlight-current-red">🎯 **Type Safety**</div>
<div class="fragment highlight-current-green">⚡ **Performance**</div>
<div class="fragment highlight-current-blue">🔄 **Concurrency**</div>
<div class="fragment highlight-current-yellow">☁️ **Cloud Native**</div>
</div>

---

## Why Choose Go Genkit? {data-auto-animate="true"}

<div class="r-vstack">
<div class="fragment fade-right">
**🎯 Type Safety** → Compile-time error detection
</div>
<div class="fragment fade-right">
**⚡ Performance** → Efficient memory management  
</div>
<div class="fragment fade-right">
**🔄 Concurrency** → Built-in goroutines
</div>
<div class="fragment fade-right">
**☁️ Cloud Native** → Easy Kubernetes deployment
</div>
</div>

{{% note %}}
Walk through each benefit:
- Type safety catches errors before runtime
- Go's performance is crucial for AI workloads
- Concurrency handles multiple AI requests efficiently
- Cloud native deployment reduces ops overhead
{{% /note %}}

## Architecture Overview {data-background-color="#f8f9fa"}

<div class="genkit-highlight">

{{< mermaid >}}
graph TB
    subgraph "🏗️ Your Application"
        A[Go Application]
        B[Business Logic]
    end
    
    subgraph "⚙️ Genkit Core"
        C[Flow Engine]
        D[Model Registry]
        E[Tool System]
        F[Prompt Manager]
    end
    
    subgraph "🤖 AI Providers"
        G[Google AI]
        H[OpenAI]
        I[Anthropic]
        J[Ollama]
    end
    
    subgraph "💾 Storage"
        K[Vector Stores]
        L[Databases]
    end
    
    A --> C
    B --> C
    C --> D
    C --> E
    C --> F
    D --> G
    D --> H
    D --> I
    D --> J
    E --> K
    E --> L
    
    style A fill:#4285f4
    style C fill:#34a853
    style G fill:#fbbc04
{{< /mermaid >}}

</div>

{{% note %}}
This shows how Genkit sits between your app and AI providers:
- Your app talks to Genkit, not directly to AI APIs
- Genkit handles all the complexity 
- Easy to switch providers or use multiple ones
{{% /note %}}

---

## Getting Started {data-auto-animate="true"}

### Installation

```bash
# Initialize Go module
go mod init my-genkit-app
```

---

## Getting Started {data-auto-animate="true"}

### Installation

```bash
# Initialize Go module
go mod init my-genkit-app

# Install Genkit core
go get github.com/firebase/genkit/go/genkit
```

---

## Getting Started {data-auto-animate="true"}

### Installation

```bash
# Initialize Go module
go mod init my-genkit-app

# Install Genkit core
go get github.com/firebase/genkit/go/genkit

# Install AI provider
go get github.com/firebase/genkit/go/plugins/googleai
```

{{% note %}}
Show how simple it is to get started - just a few go get commands.
Mention other providers available: OpenAI, Anthropic, Ollama
{{% /note %}}

---

### Basic Example

```go
package main

import (
    "context"
    "fmt"
    "log"
    
    "github.com/firebase/genkit/go/ai"
    "github.com/firebase/genkit/go/genkit"
    "github.com/firebase/genkit/go/plugins/googleai"
)

func main() {
    ctx := context.Background()
    
    // Initialize Genkit
    genkit.Init(ctx, nil)
    googleai.Init(ctx, &googleai.Config{
        APIKey: os.Getenv("GOOGLE_AI_API_KEY"),
    })
    
    // Generate text
    result, err := ai.Generate(ctx, &ai.GenerateRequest{
        Model:  googleai.Model("gemini-1.5-flash"),
        Prompt: ai.NewTextPrompt("Explain Go concurrency"),
    })
    
    if err != nil {
        log.Fatal(err)
    }
    
    fmt.Println(result.Text)
}
```

---

## Core Components {data-transition="convex"}

<div class="r-vstack">

{{% fragment class="zoom-in" %}}
### 🤖 Models
**Unified Interface** for multiple AI providers
{{% /fragment %}}

{{% fragment class="zoom-in" %}}  
### 🔄 Flows
**Workflows** that orchestrate AI operations
{{% /fragment %}}

{{% fragment class="zoom-in" %}}
### 📝 Prompts
**Template System** for managing prompts
{{% /fragment %}}

{{% fragment class="zoom-in" %}}
### 🛠️ Tools
**Function Calling** to extend AI capabilities
{{% /fragment %}}

</div>

---

### 1. Models

{{% fragment class="highlight-current-blue" %}}
**Unified Interface** for multiple AI providers
{{% /fragment %}}

```go
// Google AI
googleai.Model("gemini-1.5-flash")

// OpenAI (via plugin)
openai.Model("gpt-4")

// Anthropic (via plugin)  
anthropic.Model("claude-3-sonnet")

// Local models
ollama.Model("llama3")
```

---

### 2. Flows

{{% fragment %}}
**Workflows** that orchestrate AI operations
{{% /fragment %}}

```go
var chatFlow = genkit.DefineFlow(
    "chatFlow",
    func(ctx context.Context, input string) (string, error) {
        // Multi-step AI workflow
        resp, err := ai.Generate(ctx, &ai.GenerateRequest{
            Model: googleai.Model("gemini-1.5-flash"),
            Prompt: ai.NewTextPrompt(input),
        })
        return resp.Text, err
    },
)
```

---

### Flow Architecture

{{< mermaid >}}
flowchart TD
    A[User Input] --> B[Flow Start]
    B --> C{Validation}
    C -->|Valid| D[Process Input]
    C -->|Invalid| E[Return Error]
    D --> F[Call AI Model]
    F --> G[Process Response]
    G --> H{Quality Check}
    H -->|Good| I[Return Result]
    H -->|Poor| J[Retry/Improve]
    J --> F
    E --> K[End]
    I --> K
{{< /mermaid >}}

---

### 3. Prompts & Dotprompt

{{% fragment %}}
**Template System** for managing prompts
{{% /fragment %}}

```yaml
# prompts/summarize.prompt
---
model: googleai/gemini-1.5-flash
input:
  schema:
    text: string
    max_length: number
---

Please summarize the following text in {{max_length}} words or less:

{{text}}

Key points to focus on:
- Main ideas
- Important details
- Conclusions
```

---

### Using Dotprompt

```go
// Load and execute prompt
prompt, err := dotprompt.Open("summarize")
if err != nil {
    log.Fatal(err)
}

result, err := prompt.Generate(ctx, map[string]any{
    "text": "Long article text here...",
    "max_length": 100,
})
```

---

### 4. Tools & Function Calling

{{% fragment %}}
**Extend AI capabilities** with custom functions
{{% /fragment %}}

```go
var weatherTool = genkit.DefineTool(
    "get_weather",
    "Get current weather for a location",
    func(ctx context.Context, input struct {
        Location string `json:"location"`
    }) (string, error) {
        // Call weather API
        weather := getWeatherFromAPI(input.Location)
        return fmt.Sprintf("Weather in %s: %s", 
            input.Location, weather), nil
    },
)
```

---

### Tool Integration

```go
resp, err := ai.Generate(ctx, &ai.GenerateRequest{
    Model: googleai.Model("gemini-1.5-flash"),
    Prompt: ai.NewTextPrompt(
        "What's the weather like in San Francisco?"),
    Tools: []*ai.Tool{weatherTool},
})
```

---

<!-- Interactive poll example -->
## Quick Poll 📊 {data-background-gradient="linear-gradient(135deg, #667eea 0%, #764ba2 100%)"}

### Which AI provider do you currently use?

<div class="r-stack">
<div class="fragment fade-in-then-out">🗳️ **Vote now!**</div>
<div class="fragment">

{{% fragment class="fade-left" %}}**A)** Google AI (Gemini){{% /fragment %}}
{{% fragment class="fade-left" %}}**B)** OpenAI (GPT){{% /fragment %}}
{{% fragment class="fade-left" %}}**C)** Anthropic (Claude){{% /fragment %}}
{{% fragment class="fade-left" %}}**D)** Local models (Ollama){{% /fragment %}}
{{% fragment class="fade-left" %}}**E)** Haven't started with AI yet{{% /fragment %}}

</div>
</div>

{{% note %}}
- Great way to gauge audience experience
- Use results to adjust technical depth
- Mention Genkit supports all these providers!
{{% /note %}}

---

## RAG (Retrieval-Augmented Generation)

### Vector Store Integration

{{< mermaid >}}
graph LR
    A[User Query] --> B[Embed Query]
    B --> C[Vector Search]
    C --> D[Retrieve Documents]
    D --> E[Augment Prompt]
    E --> F[Generate Response]
    F --> G[Return Answer]
    
    subgraph "Vector Store"
        H[Document Embeddings]
        I[Similarity Search]
    end
    
    C --> H
    H --> I
    I --> D
{{< /mermaid >}}

---

### RAG Implementation

```go
// Define retriever
var docRetriever = genkit.DefineRetriever(
    "docs",
    func(ctx context.Context, req *ai.RetrieverRequest) (*ai.RetrieverResponse, error) {
        // Vector similarity search
        docs := vectorStore.Search(req.Content, 5)
        
        var parts []*ai.DocumentData
        for _, doc := range docs {
            parts = append(parts, &ai.DocumentData{
                Content: []*ai.Part{ai.NewTextPart(doc.Content)},
            })
        }
        
        return &ai.RetrieverResponse{Documents: parts}, nil
    },
)
```

---

### RAG Flow

```go
var ragFlow = genkit.DefineFlow(
    "ragFlow",
    func(ctx context.Context, query string) (string, error) {
        // Retrieve relevant documents
        docs, err := ai.Retrieve(ctx, &ai.RetrieverRequest{
            Retriever: docRetriever,
            Content:   ai.NewTextPart(query),
        })
        if err != nil {
            return "", err
        }
        
        // Generate response with context
        resp, err := ai.Generate(ctx, &ai.GenerateRequest{
            Model: googleai.Model("gemini-1.5-flash"),
            Prompt: buildRAGPrompt(query, docs.Documents),
        })
        
        return resp.Text, err
    },
)
```

---

## Advanced Features

### Streaming Responses

```go
stream, err := ai.GenerateStream(ctx, &ai.GenerateRequest{
    Model:  googleai.Model("gemini-1.5-flash"),
    Prompt: ai.NewTextPrompt("Write a long story..."),
})

for chunk := range stream {
    if chunk.Error != nil {
        log.Printf("Error: %v", chunk.Error)
        break
    }
    fmt.Print(chunk.Content[0].Text)
}
```

---

### Structured Output

```go
type Recipe struct {
    Name        string   `json:"name"`
    Ingredients []string `json:"ingredients"`
    Steps       []string `json:"steps"`
    PrepTime    int      `json:"prep_time"`
}

var recipe Recipe
err := ai.GenerateInto(ctx, &ai.GenerateRequest{
    Model: googleai.Model("gemini-1.5-flash"),
    Prompt: ai.NewTextPrompt("Create a recipe for chocolate chip cookies"),
    Output: ai.Output{
        Format: ai.OutputFormatJSON,
        Schema: ai.DefineSchema("Recipe", "", recipe),
    },
}, &recipe)
```

---

### Multi-modal Input

```go
imageData, _ := os.ReadFile("image.jpg")

resp, err := ai.Generate(ctx, &ai.GenerateRequest{
    Model: googleai.Model("gemini-1.5-flash"),
    Prompt: ai.NewMultiModalPrompt(
        ai.NewTextPart("What's in this image?"),
        ai.NewMediaPart("image/jpeg", imageData),
    ),
})
```

---

## Evaluation & Testing

### Built-in Evaluation

```go
var evaluator = genkit.DefineEvaluator(
    "helpfulness",
    func(ctx context.Context, input struct {
        Input  string `json:"input"`
        Output string `json:"output"`
    }) (*ai.EvaluationResult, error) {
        // Evaluate response quality
        score := evaluateHelpfulness(input.Input, input.Output)
        
        return &ai.EvaluationResult{
            Score: score,
            Details: map[string]any{
                "reasoning": "Response addresses user query directly",
            },
        }, nil
    },
)
```

---

### Testing Framework

```go
func TestChatFlow(t *testing.T) {
    ctx := context.Background()
    
    testCases := []struct {
        input    string
        expected string
    }{
        {"Hello", "greeting response"},
        {"Help me", "helpful response"},
    }
    
    for _, tc := range testCases {
        result, err := chatFlow.Run(ctx, tc.input)
        assert.NoError(t, err)
        assert.Contains(t, result, tc.expected)
    }
}
```

---

## Deployment Options

### Cloud Run Deployment

```dockerfile
FROM golang:1.21-alpine AS builder
WORKDIR /app
COPY . .
RUN go build -o main .

FROM alpine:latest
RUN apk --no-cache add ca-certificates
WORKDIR /root/
COPY --from=builder /app/main .
CMD ["./main"]
```

---

### Kubernetes Deployment

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: genkit-app
spec:
  replicas: 3
  selector:
    matchLabels:
      app: genkit-app
  template:
    metadata:
      labels:
        app: genkit-app
    spec:
      containers:
      - name: genkit-app
        image: gcr.io/project/genkit-app:latest
        ports:
        - containerPort: 8080
        env:
        - name: GOOGLE_AI_API_KEY
          valueFrom:
            secretKeyRef:
              name: ai-secrets
              key: google-ai-key
```

---

## Monitoring & Observability

### Built-in Telemetry

{{< mermaid >}}
graph TB
    A[Genkit Application] --> B[Telemetry Collection]
    B --> C[Traces]
    B --> D[Metrics]
    B --> E[Logs]
    
    C --> F[OpenTelemetry]
    D --> G[Prometheus]
    E --> H[Structured Logging]
    
    F --> I[Distributed Tracing]
    G --> J[Performance Metrics]
    H --> K[Debug Information]
{{< /mermaid >}}

---

### Custom Telemetry

```go
import (
    "github.com/firebase/genkit/go/core/tracing"
)

func myFlow(ctx context.Context, input string) (string, error) {
    // Start trace span
    ctx, span := tracing.Start(ctx, "custom-operation")
    defer span.End()
    
    // Add attributes
    span.SetAttributes(
        attribute.String("input.length", fmt.Sprintf("%d", len(input))),
        attribute.String("operation.type", "text-processing"),
    )
    
    // Your logic here
    result, err := processText(input)
    
    if err != nil {
        span.RecordError(err)
        span.SetStatus(codes.Error, err.Error())
    }
    
    return result, err
}
```

---

## Real-World Examples

### 1. Customer Support Bot

```go
var supportBot = genkit.DefineFlow(
    "supportBot",
    func(ctx context.Context, req CustomerQuery) (SupportResponse, error) {
        // Check knowledge base
        docs, _ := ai.Retrieve(ctx, &ai.RetrieverRequest{
            Retriever: kbRetriever,
            Content:   ai.NewTextPart(req.Question),
        })
        
        // Generate response
        resp, err := ai.Generate(ctx, &ai.GenerateRequest{
            Model: googleai.Model("gemini-1.5-flash"),
            Prompt: buildSupportPrompt(req, docs.Documents),
        })
        
        return SupportResponse{
            Answer:     resp.Text,
            Confidence: calculateConfidence(resp),
            Sources:    extractSources(docs.Documents),
        }, err
    },
)
```

---

### 2. Document Analysis Pipeline

```go
var analyzeDocument = genkit.DefineFlow(
    "analyzeDocument",
    func(ctx context.Context, docData []byte) (AnalysisResult, error) {
        // Extract text from document
        text, err := extractText(docData)
        if err != nil {
            return AnalysisResult{}, err
        }
        
        // Analyze content
        analysis, err := ai.Generate(ctx, &ai.GenerateRequest{
            Model: googleai.Model("gemini-1.5-flash"),
            Prompt: ai.NewTextPrompt(fmt.Sprintf(`
                Analyze this document and extract:
                1. Key topics
                2. Sentiment
                3. Important entities
                4. Summary
                
                Document: %s
            `, text)),
            Output: ai.Output{
                Format: ai.OutputFormatJSON,
                Schema: ai.DefineSchema("Analysis", "", AnalysisResult{}),
            },
        })
        
        var result AnalysisResult
        err = json.Unmarshal([]byte(analysis.Text), &result)
        return result, err
    },
)
```

---

### 3. Code Generation Assistant

```go
var codeGenerator = genkit.DefineFlow(
    "generateCode",
    func(ctx context.Context, req CodeRequest) (CodeResponse, error) {
        // Generate initial code
        codeResp, err := ai.Generate(ctx, &ai.GenerateRequest{
            Model: googleai.Model("gemini-1.5-flash"),
            Prompt: ai.NewTextPrompt(fmt.Sprintf(`
                Generate %s code for: %s
                
                Requirements:
                - Include error handling
                - Add comments
                - Follow best practices
                - Include tests
                
                Language: %s
                Description: %s
            `, req.Language, req.Task, req.Language, req.Description)),
        })
        
        // Validate and improve code
        improvedCode, err := improveCode(ctx, codeResp.Text, req.Language)
        
        return CodeResponse{
            Code:        improvedCode,
            Language:    req.Language,
            Explanation: generateExplanation(ctx, improvedCode),
            Tests:       generateTests(ctx, improvedCode, req.Language),
        }, err
    },
)
```

---

<!-- Multi-column comparison -->
## Traditional vs Genkit {data-background-color="#1a1a1a"}

<div class="r-hstack">
<div>

{{% fragment class="fade-in-then-semi-out" %}}
### 😰 Traditional Approach
{{% /fragment %}}

{{% fragment class="fade-up" %}}
- Manual API integration
- Custom error handling  
- No built-in monitoring
- Complex deployment
- Vendor lock-in
{{% /fragment %}}

</div>
<div>

{{% fragment class="fade-in-then-semi-out" %}}
### 🚀 With Go Genkit
{{% /fragment %}}

{{% fragment class="fade-up" %}}
- Unified interface
- Built-in resilience
- Automatic telemetry
- Simple deployment
- Provider flexibility
{{% /fragment %}}

</div>
</div>

---

## Best Practices

### 1. Error Handling

```go
func robustFlow(ctx context.Context, input string) (string, error) {
    // Implement retry logic
    for attempt := 0; attempt < 3; attempt++ {
        result, err := ai.Generate(ctx, &ai.GenerateRequest{
            Model:  googleai.Model("gemini-1.5-flash"),
            Prompt: ai.NewTextPrompt(input),
        })
        
        if err == nil {
            return result.Text, nil
        }
        
        // Log and retry
        log.Printf("Attempt %d failed: %v", attempt+1, err)
        time.Sleep(time.Duration(attempt+1) * time.Second)
    }
    
    return "", fmt.Errorf("all attempts failed")
}
```

---

### 2. Configuration Management

```go
type Config struct {
    GoogleAIKey    string `env:"GOOGLE_AI_API_KEY"`
    OpenAIKey      string `env:"OPENAI_API_KEY"`
    ModelName      string `env:"MODEL_NAME" envDefault:"gemini-1.5-flash"`
    MaxRetries     int    `env:"MAX_RETRIES" envDefault:"3"`
    Timeout        time.Duration `env:"TIMEOUT" envDefault:"30s"`
    VectorDBURL    string `env:"VECTOR_DB_URL"`
}

func LoadConfig() (*Config, error) {
    cfg := &Config{}
    if err := env.Parse(cfg); err != nil {
        return nil, err
    }
    return cfg, nil
}
```

---

### 3. Testing Strategies

```go
// Mock provider for testing
type MockProvider struct {
    responses map[string]string
}

func (m *MockProvider) Generate(ctx context.Context, req *ai.GenerateRequest) (*ai.GenerateResponse, error) {
    prompt := req.Prompt.String()
    if response, exists := m.responses[prompt]; exists {
        return &ai.GenerateResponse{
            Text: response,
        }, nil
    }
    return nil, errors.New("no mock response")
}

func TestWithMock(t *testing.T) {
    mock := &MockProvider{
        responses: map[string]string{
            "Hello": "Hi there!",
        },
    }
    
    // Use mock in tests
    // ...
}
```

---

### 4. Performance Optimization

{{% fragment %}}
**Caching** - Cache frequent requests
{{% /fragment %}}

{{% fragment %}}
**Batching** - Process multiple requests together
{{% /fragment %}}

{{% fragment %}}
**Connection Pooling** - Reuse HTTP connections
{{% /fragment %}}

{{% fragment %}}
**Async Processing** - Use goroutines for parallel operations
{{% /fragment %}}

---

## Performance Tips

### Concurrent Processing

```go
func processMultipleInputs(ctx context.Context, inputs []string) ([]string, error) {
    results := make([]string, len(inputs))
    errors := make([]error, len(inputs))
    
    var wg sync.WaitGroup
    for i, input := range inputs {
        wg.Add(1)
        go func(idx int, inp string) {
            defer wg.Done()
            
            result, err := ai.Generate(ctx, &ai.GenerateRequest{
                Model:  googleai.Model("gemini-1.5-flash"),
                Prompt: ai.NewTextPrompt(inp),
            })
            
            if err != nil {
                errors[idx] = err
            } else {
                results[idx] = result.Text
            }
        }(i, input)
    }
    
    wg.Wait()
    
    // Handle any errors
    for _, err := range errors {
        if err != nil {
            return nil, err
        }
    }
    
    return results, nil
}
```

---

## Integration Examples

### REST API Server

```go
func main() {
    ctx := context.Background()
    
    // Initialize Genkit
    genkit.Init(ctx, nil)
    googleai.Init(ctx, &googleai.Config{
        APIKey: os.Getenv("GOOGLE_AI_API_KEY"),
    })
    
    // Create HTTP server
    mux := http.NewServeMux()
    
    mux.HandleFunc("/chat", func(w http.ResponseWriter, r *http.Request) {
        var req ChatRequest
        json.NewDecoder(r.Body).Decode(&req)
        
        response, err := chatFlow.Run(r.Context(), req.Message)
        if err != nil {
            http.Error(w, err.Error(), http.StatusInternalServerError)
            return
        }
        
        json.NewEncoder(w).Encode(ChatResponse{
            Response: response,
        })
    })
    
    log.Println("Server starting on :8080")
    http.ListenAndServe(":8080", mux)
}
```

---

### gRPC Service

```protobuf
syntax = "proto3";

package chatservice;

service ChatService {
  rpc Chat(ChatRequest) returns (ChatResponse);
  rpc ChatStream(ChatRequest) returns (stream ChatResponse);
}

message ChatRequest {
  string message = 1;
  string user_id = 2;
}

message ChatResponse {
  string response = 1;
  double confidence = 2;
}
```

---

### GraphQL Integration

```go
type Resolver struct {
    chatFlow *genkit.Flow[string, string]
}

func (r *Resolver) Chat(ctx context.Context, args struct {
    Message string
}) (string, error) {
    return r.chatFlow.Run(ctx, args.Message)
}

var schema = `
    type Query {
        chat(message: String!): String!
    }
`
```

---

## Security Considerations

### 1. API Key Management

```go
// Never hardcode API keys
// ❌ Bad
apiKey := "your-secret-key-here"

// ✅ Good
apiKey := os.Getenv("GOOGLE_AI_API_KEY")
if apiKey == "" {
    log.Fatal("API key not set")
}
```

---

### 2. Input Validation

```go
func validateInput(input string) error {
    if len(input) == 0 {
        return errors.New("input cannot be empty")
    }
    
    if len(input) > 10000 {
        return errors.New("input too long")
    }
    
    // Check for malicious content
    if containsSQLInjection(input) {
        return errors.New("potential SQL injection detected")
    }
    
    return nil
}
```

---

### 3. Rate Limiting

```go
import "golang.org/x/time/rate"

var limiter = rate.NewLimiter(rate.Limit(10), 100) // 10 requests per second

func rateLimitedFlow(ctx context.Context, input string) (string, error) {
    if !limiter.Allow() {
        return "", errors.New("rate limit exceeded")
    }
    
    return chatFlow.Run(ctx, input)
}
```

---

## Debugging & Troubleshooting

### Common Issues

{{% fragment %}}
**API Key Problems** - Ensure environment variables are set correctly
{{% /fragment %}}

{{% fragment %}}
**Model Initialization** - Check provider configurations
{{% /fragment %}}

{{% fragment %}}
**Memory Issues** - Monitor goroutine usage and memory leaks
{{% /fragment %}}

{{% fragment %}}
**Network Timeouts** - Implement proper timeout handling
{{% /fragment %}}

---

### Debug Logging

```go
import "github.com/firebase/genkit/go/core/logger"

func debugFlow(ctx context.Context, input string) (string, error) {
    logger := logger.FromContext(ctx)
    
    logger.Info("Flow started", 
        "input_length", len(input),
        "timestamp", time.Now(),
    )
    
    result, err := ai.Generate(ctx, &ai.GenerateRequest{
        Model:  googleai.Model("gemini-1.5-flash"),
        Prompt: ai.NewTextPrompt(input),
    })
    
    if err != nil {
        logger.Error("Generation failed", "error", err)
        return "", err
    }
    
    logger.Info("Flow completed", 
        "output_length", len(result.Text),
        "success", true,
    )
    
    return result.Text, nil
}
```

---

## Future Roadmap

### What's Coming

{{% fragment %}}
**Enhanced Model Support** - More providers and local models
{{% /fragment %}}

{{% fragment %}}
**Advanced RAG** - Better retrieval and chunking strategies
{{% /fragment %}}

{{% fragment %}}
**Multi-Agent Systems** - Coordinated AI agents
{{% /fragment %}}

{{% fragment %}}
**Fine-tuning Integration** - Direct model customization
{{% /fragment %}}

{{% fragment %}}
**Improved Observability** - Better monitoring and debugging tools
{{% /fragment %}}

---

## Community & Resources

### Getting Help

{{% fragment %}}
**📚 Documentation** - [genkit.dev](https://genkit.dev)
{{% /fragment %}}

{{% fragment %}}
**💬 Discord** - Active community support
{{% /fragment %}}

{{% fragment %}}
**🐛 GitHub Issues** - Bug reports and feature requests
{{% /fragment %}}

{{% fragment %}}
**📖 Examples** - Sample applications and tutorials
{{% /fragment %}}

---

### Contributing

```bash
# Clone the repository
git clone https://github.com/firebase/genkit.git

# Navigate to Go directory
cd genkit/go

# Make your changes
# Add tests
go test ./...

# Submit pull request
```

---

## Key Takeaways {.r-fit-text}

<div class="r-vstack">

{{% fragment class="highlight-current-blue" %}}
### 🚀 **Production Ready**
Built by Google with enterprise features
{{% /fragment %}}

{{% fragment class="highlight-current-green" %}}
### 🔧 **Developer Friendly**  
Great tooling and debugging experience
{{% /fragment %}}

{{% fragment class="highlight-current-red" %}}
### ⚡ **High Performance**
Go's efficiency with AI capabilities
{{% /fragment %}}

{{% fragment class="highlight-current-yellow" %}}
### 🌐 **Flexible**
Multiple providers and deployment options
{{% /fragment %}}

</div>

---

## Getting Started Today

### Next Steps

1. **Install** Go Genkit and try the examples
2. **Explore** the Developer UI and tooling
3. **Build** a simple flow for your use case
4. **Deploy** to your preferred platform
5. **Monitor** and optimize performance

---

<!-- Demo slide with special transition -->
## Live Demo Time! 🎯 {data-transition="zoom" data-background-color="#1a1a1a"}

<div class="fragment">

### Let's Build Something Together

**Building a real AI application with Go Genkit**

</div>

{{% fragment class="fade-up" %}}
```bash
# Follow along at:
git clone https://github.com/demo/genkit-live-demo
cd genkit-live-demo
go run main.go
```
{{% /fragment %}}

{{% note %}}
- This is where you'd do your live coding
- Have a backup plan in case of technical issues
- Keep it simple but impressive
- Maybe a chatbot or document summarizer
{{% /note %}}

---

# Thank You! {data-background-gradient="linear-gradient(45deg, #4285f4 0%, #34a853 100%)"}

## Questions & Discussion 💬

<div class="r-hstack">
<div>

### 📚 Resources
- [genkit.dev](https://genkit.dev)
- [GitHub](https://github.com/firebase/genkit)
- [Discord Community](https://discord.gg/qXt5zzQKpc)

</div>
<div>

### 📧 Contact
- **Email**: genkit-team@google.com
- **Twitter**: @genkitdev
- **LinkedIn**: /company/google

</div>
</div>

{{% fragment class="fade-up" %}}
### 🚀 Start building with Go Genkit today!
{{% /fragment %}}

{{% note %}}
- Thank the audience
- Encourage questions - be ready for technical depth
- Offer to connect on social media
- Maybe offer office hours or follow-up resources
{{% /note %}}