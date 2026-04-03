# Ask Sage API — Community Resources

<p align="center">
  <img src="images/AskSage_Logo.png" alt="Ask Sage Logo" height="200" width="200">
</p>

<p align="center">
  <em>Community-driven examples and documentation for the Ask Sage API</em>
</p>

<p align="center">
  <a href="https://docs.asksage.ai/">Official Docs</a> •
  <a href="https://pypi.org/project/asksageclient/">Python Client v1.42</a> •
  <a href="https://discord.gg/upxuAdNvjY">Discord</a> •
  <a href="https://www.asksage.ai/">Ask Sage</a>
</p>

---

> **Note:** This is a community-driven repository. The official API documentation is at [docs.asksage.ai](https://docs.asksage.ai/).

## What is Ask Sage?

[Ask Sage](https://www.asksage.ai/) is an agnostic generative AI platform that provides access to a wide range of AI models through a single API. It's designed for easy integration into existing workflows and can be customized to meet the needs of users and organizations.

## Quick Start

### 1. Install the Python client

```bash
pip install asksageclient
```

### 2. Set up your credentials

```bash
export ASKSAGE_EMAIL="your_email@domain.com"
export ASKSAGE_API_KEY="your_api_key_here"
```

### 3. Send your first query

```python
import os
from asksageclient import AskSageClient

client = AskSageClient(
    email=os.environ["ASKSAGE_EMAIL"],
    api_key=os.environ["ASKSAGE_API_KEY"]
)

response = client.query(
    message="What is machine learning?",
    model="gpt-4o"
)

print(response["message"])
```

> **Note:** API access requires a paid Ask Sage subscription. Get your API key from the Ask Sage platform under **Account & Tokens → API Keys**.

## Available Models

Ask Sage provides access to models from multiple providers through a single API:

| Provider | Models |
|---|---|
| **OpenAI (Azure)** | GPT-4o, GPT-4o-mini, GPT-4.1, GPT-4.1-mini, GPT-5.1, o1, o1-mini, o3-mini, o4-mini |
| **OpenAI (Azure Gov)** | GPT-4o-gov, GPT-4.1-gov, GPT-5.1-gov, o1-gov, o3-mini-gov, o4-mini-gov |
| **Anthropic** | Claude 3.5 Sonnet, Claude 3.5 Haiku, Claude Sonnet 4, Claude Opus 4 |
| **Google** | Gemini 2.0 Flash, Gemini 2.5 Pro, Gemini 2.5 Flash |
| **Meta** | LLAMA 4 Scout, LLAMA 4 Maverick |
| **Mistral** | Mistral Large |
| **xAI** | Grok |
| **Cohere** | Command R+ |
| **Image Generation** | DALL-E 3, Imagen 4, GPT Image 1 |
| **Speech** | Whisper (STT), OpenAI TTS |
| **AWS Bedrock** | Various (Titan, Nova, etc.) |

Use the `get_models` endpoint or `client.get_models()` to see the full list of models available on your account.

```python
models = [
    'gpt-4o', 'gpt-4o-mini', 'gpt-4.1', 'gpt-4.1-mini', 'gpt-5.1',
    'o1', 'o1-mini', 'o3-mini', 'o4-mini',
    'gpt-4o-gov', 'gpt-4.1-gov', 'gpt-5.1-gov',
    'o1-gov', 'o3-mini-gov', 'o4-mini-gov',
    'claude-35-sonnet', 'claude-35-haiku', 'claude-sonnet-4', 'claude-opus-4',
    'gemini-20-flash', 'gemini-25-pro', 'gemini-25-flash',
    'llama-4-scout', 'llama-4-maverick',
    'mistral-large', 'xai-grok', 'cohere',
    'dall-e-3', 'imagen-4', 'gpt-image-1',
    'whisper', 'openai-tts',
    'aws-bedrock-titan', 'aws-bedrock-nova'
]
```

> **Note:** Available models may vary by account and tenant configuration. Admins can restrict access to certain models.

## API Compatibility Endpoints

Ask Sage provides native API compatibility with **OpenAI**, **Anthropic**, and **Google Gemini** — use the SDKs and tools you already know with zero code changes beyond swapping the base URL.

### OpenAI-Compatible Endpoint

```python
from openai import OpenAI

client = OpenAI(
    base_url="https://api.asksage.ai/openai/",
    api_key="your_asksage_api_key"
)

response = client.chat.completions.create(
    model="gpt-4o",
    messages=[{"role": "user", "content": "Hello!"}]
)

print(response.choices[0].message.content)
```

### Anthropic-Compatible Endpoint

```python
import anthropic

client = anthropic.Anthropic(
    base_url="https://api.asksage.ai/server/anthropic",
    api_key="your_asksage_api_key"
)

response = client.messages.create(
    model="claude-sonnet-4",
    max_tokens=1024,
    messages=[{"role": "user", "content": "Hello!"}]
)

print(response.content[0].text)
```

### Gemini-Compatible Endpoint

```python
import requests

model = "gemini-2.5-flash"
url = f"https://api.asksage.ai/server/google/v1/models/{model}:generateContent"

response = requests.post(url, headers={
    "Authorization": "Bearer your_asksage_api_key",
    "Content-Type": "application/json"
}, json={
    "contents": [{"parts": [{"text": "Hello!"}]}]
})

print(response.json())
```

For full endpoint documentation including streaming, function calling, and advanced parameters, see the [API Compatibility Guides](https://docs.asksage.ai/).

## Integrations

Ask Sage's API compatibility endpoints enable seamless integration with popular developer tools:

- **[Claude Code](https://docs.anthropic.com/en/docs/claude-code)** — Use Ask Sage models as your coding assistant
- **[Codex CLI](https://github.com/openai/codex)** — OpenAI's CLI tool works with Ask Sage via the compatible endpoint
- **[Continue.dev](https://continue.dev/)** — Open-source AI code assistant for VS Code and JetBrains
- **[Cursor](https://cursor.sh/)** — AI-powered code editor
- **[GitHub Copilot](https://github.com/features/copilot)** — Configure with Ask Sage's endpoint

See the [official documentation](https://docs.asksage.ai/) for detailed setup instructions for each integration.

## API Overview

### API Documentation (Swagger)

- **Server API v1.56**: [Swagger Docs](https://app.swaggerhub.com/apis-docs/asksageinc/ask-sage_server_api/1.56) — Base URL: `api.asksage.ai/server/`
- **User API v1.21**: [Swagger Docs](https://app.swaggerhub.com/apis-docs/asksageinc/ask-sage_user_api/1.21) — Base URL: `api.asksage.ai/user/`

### Key Endpoints

| Endpoint | Description |
|---|---|
| `/server/query` | Generate completions from any available model |
| `/server/query_with_file` | Query with a file as context |
| `/server/get-models` | List available models |
| `/server/get-datasets` | List available datasets |
| `/server/get-train` | Train a model on custom data |
| `/user/get-token-with-api-key` | Get a 24-hour access token |
| `/user/add-dataset` | Create a new dataset |

### Python Client

The [asksageclient](https://pypi.org/project/asksageclient/) Python package (v1.42) wraps all API endpoints:

```bash
pip install asksageclient
```

| Function | Description |
|---|---|
| `query()` | Send prompts to any model |
| `query_with_file()` | Query with file context |
| `get_models()` | List available models |
| `get_datasets()` | List datasets |
| `train()` / `train_with_file()` | Ingest data into a dataset |
| `get_personas()` | List available personas |
| `follow_up_questions()` | Generate follow-up questions |
| `tokenizer()` | Tokenize text |
| `file()` | Upload and convert files |

### Authentication

There are three ways to authenticate:

1. **Python Client** — Pass your email and API key directly to `AskSageClient`
2. **24-Hour Access Token** — Generate a short-lived token via `/get-token-with-api-key`
3. **Static API Key** — Use your API key directly in the `x-access-tokens` header

```python
import os
from asksageclient import AskSageClient

# Recommended: use environment variables
client = AskSageClient(
    email=os.environ["ASKSAGE_EMAIL"],
    api_key=os.environ["ASKSAGE_API_KEY"]
)
```

## Examples

### 0. AI Ethics

A discussion on the ethical implications of using AI and best practices for responsible use.

- [AI Ethics Overview](examples/ex_0_ai_ethics/AI-Ethics.md)

### 1. API Endpoints

Hands-on walkthrough of Ask Sage API endpoints and the Python client.

- [API Endpoints Overview](examples/ex_1_api_endpoints/AskSage_API_Endpoints.md)
- [Python Client Notebook](examples/ex_1_api_endpoints/asksage_python_client_overview.ipynb)

### 2. Prompt Engineering

Techniques for crafting effective prompts to get the best results from LLMs.

- [Prompt Engineering Overview](examples/ex_2_prompt_engineering/prompt_engineering_overview.md)
- [Code Generation](examples/ex_2_prompt_engineering/Prompt_Engineering_For_Code_Generation.ipynb)
- [Grant Writing](examples/ex_2_prompt_engineering/Prompt_Engineering_For_Grant_Writing.ipynb)
- [Writing A Speech](examples/ex_2_prompt_engineering/Prompt_Engineering_For_Writing_A_Speech.ipynb)
- [Recipe Generation](examples/ex_2_prompt_engineering/Prompt_Engineering_For_Recipe_Generation.ipynb)
- [Project Management](examples/ex_2_prompt_engineering/Prompt_Engineering_For_Project_Management.ipynb)
- [Detailed Explanation](examples/ex_2_prompt_engineering/Prompt_Engineering_Detailed_Explanation.ipynb)
- [Chatbot Creation](examples/ex_2_prompt_engineering/Prompt_Engineering_Chatbot_Creation.ipynb)

### 9. Additional Requested Examples

Community-requested examples and use cases.

- [LLM Image Interpretation](examples/ex_9_additional_requested_examples/ex_1_llm_interpretation_description.ipynb)

> Have an idea for an example? Join the [Discord](https://discord.gg/upxuAdNvjY) or open an issue!

## Best Practices

- **Secure your credentials** — Use environment variables, not hardcoded values
- **Respect rate limits** — Handle `429` responses with appropriate backoff
- **Handle errors gracefully** — Check response status codes and error messages
- **Use the right model** — Different models have different strengths and costs
- **Test thoroughly** — Validate outputs before using in production
- **Monitor usage** — Track token consumption to manage costs

## Additional Resources

- [AI/ML Vocabulary](study_materials/AI_ML_Vocabulary.md)
- [Ask Sage Documentation](https://docs.asksage.ai/)
- [Python Client on PyPI](https://pypi.org/project/asksageclient/)
- [Ask Sage Discord](https://discord.gg/upxuAdNvjY)

## Contributing

We welcome contributions! See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

## License

This repository is licensed under the MIT License. See [LICENSE](LICENSE.md) for details.
